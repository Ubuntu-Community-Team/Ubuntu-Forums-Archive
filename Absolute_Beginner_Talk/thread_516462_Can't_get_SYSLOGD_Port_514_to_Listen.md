---
title: "Can't get SYSLOGD Port 514 to Listen"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by netglen on 2007-08-03
I followed several suggested websites on how to setup SYSLOGD to accept forwarded logs from other systems. However after following all the directions, I never see port 514 listening. For example I used the following directions from this site 

[https://help.ubuntu.com/community/AudiableLogs](https://help.ubuntu.com/community/AudiableLogs)

(Step 1)
#To make a backup: 
sudo cp /etc/services /etc/services.backup

#To edit
sudo gedit /etc/services

By default, Ubuntu 7.04 Desktop does not have port 514 open. Check to be sure it is not already on the list before you add the following:

syslog          514/udp                      # Syslogd Port 


(Step 2)
Regardless of how you control the audio portion of this tutorial, you are still going to want your logs going somewhere. By default Ubuntu 7.04 does not load syslogd in receive mode. This means that the computer that runs the syslogd in receive mode needs to automatically load the -r switch.

We need to backup and edit /etc/init.d/sysklogd.conf. NOTE sysklogd is not a typo.

#To make a backup: 
sudo cp /etc/init.d/sysklogd /etc/init.d/sysklogd.backup

#To edit:
sudo gedit /etc/init.d/sysklogd

Assuming you have not modified this file already, then you should see a block like this start near Line 21:

21:# Options for start/restart the daemons 
22:#   For remote UDP logging use SYSLOGD="-r"
23:#
24:SYSLOGD="-s syslog"

Simply change Line 24 to:

24:SYSLOGD="-r" 

then save and exit the file. We will restart sysklog in the next section, but doing it now wont hurt anything.

should not produce an error at all. 

(Step 3)
I decided it was best to put everything in one log for the sake of simplicity mainly, and because I had some issues with overlapping voices and events being spoken out of order. Plus, we can output this file in text only for use on a server or a computer without sound. NOTE if you dont have sound or server, you probably shouldnt bother doing this unless you want all of your logs in one file on one computer.

to put all the logs in one file is actually really simple, simply back up and edit /etc/syslog.conf like this:

#To make a backup: 
sudo cp /etc/syslog.conf /etc/syslog.conf.backup

#To edit:
sudo gedit /etc/syslog.conf

Now delete everything and replace with this:

# Sample syslogd configuration file to 
# messages to a remote host forward all.
*.*            /var/log/alllogs

NOTE: you can replace "/var/log/alllogs" with any name of your choice, just substitute "/var/log/alllogs" for your choice for the rest of the examples.

Now simply restart the sysklogd and networking daemons so it is listening for logs from remote computers and logging them to one file, type:

sudo /etc/init.d/networking restart 
sudo /etc/init.d/sysklogd restart

(END)

Now after all that, I execute a 'netstat -a' but I don't see port 514 listening. Now even with Ipchains running, I should still see the port active right? I tried using the following directions to add a machi9ne I wanted to monitor but still I don't see the port or anything being accepted.

[http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml](http://news.softpedia.com/news/Setting-Up-a-Central-Syslog-Server-44063.shtml)


Help!


--Glen

---

### Post by netglen on 2007-08-03
=== UPDATE ===

Well the only way I can get it to work so far is to stop the /etc/init.d/sysklogd service and manually execute a 'sudo /sbin/syslogd -r'. Once I do that I see port 514 open and I can send test messages and they're appears in the syslog logs. So what am I doing wrong? I tried the following in /etc/init.d/sysklogd and restarted both the networking and sysklogd services.

# Options for start/restart the daemons
#  For remote UDP logging use SYSLOGD="-r"
#
# SYSLOGD="-u syslog"
# SYSLOGD="-ur syslog"
# SYSLOGD="-r"
# SYSLOGD=" -r"
# SYSLOGD="-u syslog -r"
# SYSLOGD="-r syslog -u"
# SYSLOGD="-r -u syslog"


Of course I would remove the '#' for the one I was testing but none of the above settings would open port 514 for external collection. What the hell am I doing that is wrong?

---

### Post by netglen on 2007-08-03
=== UPDATE 2 ===

I think I found the problem. It looks like there is an alternate file is being used to pull the sysklogd passed parameters. All the webpages that I visited instructed that the "-r" parameter to be added in /etc/init.d/sysklogd file. But I found one webpage that mentioned another location at /etc/default/sysklogd. I visited that file and added the "-r" parameter there. After a restart of both the networking and sysklogd, I now see port 514 listening. 

So what is the story with the "/etc/default/sysklogd" and "/etc/init.d/sysklogd'? Was my install of Ubuntu different then everyone elses? Why did all the howtos point to a different file location? I can't even begin to look back at all the time I spent. :D

---

### Post by steve.horsley on 2007-08-03
The man page shipped with Ubunu is wrong.
Undo any changes you made to /etc/init.d/sysklogd and instead, edit /etc/default/syslogd.

EDIT:
Looks like you found the answer while I was looking at the problem too. No, your install is not different to everyone elses. I think the developers are not keeping the documentation up to date when they change the way things work. Developers hate doing documentation.

---

### Post by wazzup on 2007-11-08
Same thing here. Thanks. This thread saved me quite some time.

After editing /etc/default/sysklogd and restarting syslog I get

Nov  8 16:06:47 machine syslogd 1.4.1#20ubuntu4: restart (remote reception).

cool, but also:

Nov  8 16:06:47 machine kernel: [19492.401528] process `syslogd' is using obsolete setsockopt SO_BSDCOMPAT

This went away after restarting networking.

---

