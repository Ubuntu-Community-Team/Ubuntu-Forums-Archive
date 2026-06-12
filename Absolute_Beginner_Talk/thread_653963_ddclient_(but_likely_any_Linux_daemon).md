---
title: "ddclient (but likely any Linux daemon)"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by John Boy on 2007-12-30
I have a good ddclient.conf which is to say that when I run ddclient, it correctly updates my IP address as verified at DynDNS. The issue I have is that when I come back from hibernate or do a system restart, the daemon does not appear to get run in that the DynDNS IP address does not get updated. I have modified the ddclient.conf to set parameter run_daemon=true and the interval is 300 (and I did a restart of the process to get these seen) so I hope(d) that the task would run at least within 5 mins of the restart, indeed every 5 mins, it would run. The process is always there in that there is a PID but the only way I can get the IP address to update is to sudo ddclient.From reasing this forum I believe that, as I am running as a daemon, I don't need to set up a cron job.

Thanks for any help,

                                 Slainte,

                                           John

---

### Post by blueridgedog on 2007-12-30
Can you verify that it is indeed running as a process?

Try looking for it:

ps ax | grep ddclient

---

### Post by John Boy on 2007-12-31
Thanks - when I gave the command I got :

  5984 pts/1    S+     0:00 grep ddclient

Thanks,

             John

---

### Post by blueridgedog on 2007-12-31
That is your grep, so there is no process running by that name.

I suspect that is the nature of the problem.

---

### Post by g2g591 on 2007-12-31
did you install from the repository? I had no issues when i used the repo, "sudo apt-get install ddclient"

---

### Post by John Boy on 2007-12-31
Thanks to BlueRidge (NC perhaps?). I used Adept to load and install - even though I don't know what I am doing, I thought it would. I can confirm that if I reboot my router to force Telecom NZ to give me a new IP address, then no amount of waiting and/or restarts will get the new IP advertised. When I go into System Settings, advanced tab and Services there is ddclient and with administrator, I see that it is supposed to 'start during boot'. When I run ddclient, it updates right away. As the Title says, I don't think this behaviour/problem is specific to ddclient. Happy New Year, John

---

### Post by John Boy on 2008-01-01
I also realise that there is a second task ddclient~ which is not running. I am wondering if this task is the one which I started after changing the ddclient.conf to run as a daemon ? This might explain why I am seeing behaviour different than expected. If this is the case, how do I remove the old ddclient and force the tilda version ?

            Thanks,

                        John

---

### Post by blueridgedog on 2008-01-01
OK, I don't have ddclient, so I can't debug it from that perspective, but lets try something simple:

Open two terminal windows.

In one issue:

/usr/sbin/ddclient -daemon 100 -syslog

After that, in the other issue:

ps ax | grep ddclient

Lets see if we can make it run on it's own.

---

### Post by asmoore82 on 2008-01-01
I believe you need to tell the ACPI subsystem to stop/restart the ddclient daemon for you on power events...

edit "/etc/default/acpi-support"
```
$ sudo gedit "/etc/default/acpi-support"
```
and at or around line 60 make it look like this:
```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="ddclient"
```

---

### Post by John Boy on 2008-01-01
Following what BRD recommends, the output is:

 5352 pts/1    S      0:00 ddclient - sleeping for 16 seconds
 5359 pts/1    S      0:00 ddclient - sleeping for 46 seconds

so that seemed to kick it in to life, 

while I can see that I need to hook into ACPI re: power events, I would have thought that full reboot for a task with 'start at reboot' should have done the trick for the major events.

In the System Services of Advanced Tab of System Settings, I still have two ddclient - one without tilda, running with post-tilda attached stopped.Could this be indicating something suspicious ?

Thanks,

           John

---

### Post by blueridgedog on 2008-01-01
OK, so it runs when you tell it to and runs as a service when you ask.  How are you starting it now such that it fails, perhaps we need to add the --daemon line to the starting command rather than just in the config.

---

### Post by John Boy on 2008-01-02
Thanks blueridgedog for you response. In terms of starting it, I was hoping to start it once (as I have from the command line) and then, as it had 'run on reboot' I thought it would run each time I rebooted and I took asmoore's advice and added the 'stop-services' at line 62 and was hoping that this would handle some of the more exotic power events (such as hibernate). As I have said, I have a flaw in my understanding of how such things work in Linux. I can confirm that there is a s20 for ddclient in /etc/rc2.d so I would have hoped that the deamon would have been started by the system - obviously I have a rather large misunderstanding. Thanks for sticking with me through this.

                 Slainte,

                            John

---

### Post by blueridgedog on 2008-01-03
So, we have established if you run it with:

/usr/sbin/ddclient -daemon 100 -syslog

It runs as expected.

But, if you let it kick off from the entry in rc2, it doesn't.

Can you confirm that with:

ps ax | grep ddclient

In each configuration?  And please post the output (after booting and after running the command above).

Finally, as a punt you could simply put /usr/sbin/ddclient -daemon 100 -syslog in /etc/rc.local (before the exit line).

---

### Post by John Boy on 2008-01-03
After a reboot the command gives :

 ps ax | grep ddclient
 5372 pts/0    S+     0:00 grep ddclient

after I start with the command you gave the result is:

ps ax | grep ddclient
 5515 pts/0    S      0:00 ddclient - sleeping for 50 seconds
 5623 pts/0    S      0:00 ddclient - sleeping for 80 seconds
 5629 pts/0    S      0:00 ddclient - sleeping for 100 seconds
 5631 pts/0    S+     0:00 grep ddclient


Thanks,

            John

---

### Post by blueridgedog on 2008-01-03
Ok, then the rc entry is not starting it and I would edit the file (sudo) /etc/rc.local and put the following in:

/usr/sbin/ddclient -daemon 100 -syslog

(before the exit line).

---

### Post by John Boy on 2008-01-03
I think you are correct and I think we have the nub of the problem in that when I start it, I use sudo but it seems the OS does not have the privilege to do so when I look into the Daemon Log I see :


04/01/08 14:58:01	remus	ddclient[5623]	WARNING:  file /etc/ddclient.conf: Cannot open file '/etc/ddclient.conf'. (Permission denied)

04/01/08 14:58:01	remus	ddclient[5623]	WARNING:  file /var/cache/ddclient/ddclient.cache: Cannot open file '/var/cache/ddclient/ddclient.cache'. (Permission denied)

Thanks,

             John

---

### Post by John Boy on 2008-01-03
and here is what ls -l says on the .conf:

-rw-------  1 root root       603 2007-12-20 18:45 ddclient.conf

Thanks,

            John

---

### Post by blueridgedog on 2008-01-03
You could:

sudo chmod 777 /etc/ddclient.conf

---

### Post by John Boy on 2008-01-05
Thanks - ddclient now warns about the ownership of the conf file (in that it seems to want exclusivity) but seems to run OK. As ddclient comes from DynDNS (a classy company) I am wondering if Adept did not do something correct (as there are problems with permissions) and perhaps the best things is to purge remove everything and use apt-get or another proggy to install. If I have the same problem, thanks to this forum I know what to do and if things are magically correct, so much the better.

             Slainte,

                        John

---

