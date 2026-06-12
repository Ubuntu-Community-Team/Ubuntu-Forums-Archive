---
title: "how to use inadyn with dyndns"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by kjacks on 2006-11-29
Last week I finished installing ubuntu-6.10-server-i386 I have a website that is hosted on my server and can access it via my external ip address.  Now I'm having problems setting up inadyn to use with my dyndns account.  

To start inadyn I use this command and get this response:

*xxxx*@ubuntu:~$ inadyn -u *xxxxxx* -p *xxxxxx* -a *xxxxx*.homelinux.com
INADYN: Started 'INADYN version 1.96' - dynamic DNS updater.
I:INADYN: IP address for alias '*xxxxxx*.homelinux.com' needs update to 'xx.xx.xx.xx'
I:INADYN: Alias '*xxxxx*.homelinux.com' to IP 'xx.xx.xx.xx' updated successful.


It works great but doesn't return me to the bash prompt so I can continue with other tasks.   I have to ctl-x to get back to the bash but that stops inadyn from running.  

How do i run this on my server in the background?

---

### Post by ingo on 2006-12-01
I never worked with inadyn, but how about just switching to another bash?

---

### Post by az on 2006-12-01
See here:
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by jdpipe on 2006-12-05
Try the following page
[http://freepage.ina-tech.net/modules/newbb/viewtopic.php?viewmode=flat&topic_id=413&forum=5](http://freepage.ina-tech.net/modules/newbb/viewtopic.php?viewmode=flat&topic_id=413&forum=5)

--------8<-------

HOWTO: set inadyn to start at boot with Ubuntu
The following will allow your Ubuntu Linux machine to be accessible anywhere that you are given an externally-accessible IP address. This includes most ISPs but excludes many office LANs.

First edit /etc/inadyn.conf:

sudo gedit /etc/inadyn.conf

It should contain something like to the following:

--username myusername
--password mypassword
--update_period 60000
--alias myhost.dyndns.org
--background

Now test that it works by typing

sudo /usr/sbin/inadyn

Next, add inadyn to your 'crontab':

sudo apt-get install inadyn
export EDITOR=gedit
sudo crontab -e

Edit the file to add the following additional line:

@reboot /usr/sbin/inadyn

Then save and edit the editor. Verify using

sudo crontab -l

When you reboot, you should see indyn listed when you type

ps -A | grep inadyn

Hope that helps someone out there. Feel free to add your comments.

Cheers
JP

---

### Post by vjairam on 2007-06-20
I was looking for how to update multiple dyndns.org hosts using the same inadyn.conf file and didnt get a straight answer on any blog. So when I did figure it out, I decided to add to jdpipe's already useful thread so that updating and verifying are easier for linux newbies like me.

Here's my inadyn.conf:

[root@mya etc]# cat inadyn.conf
username      myusername
password       mypassword
alias           mysite1.com
alias           mysite2.com
update_period   60000
background

where myusername is your dyndns.org username and mypassword is your dyndns.org password.

When you have a config file like above, in /etc/inadyn.conf, all you have to run is inadyn at the command line with no arguments. It figures out that since it didnt get any parameters, that it should get the data from a configuration file.

Now if everything went well, you should see the following messages in the file messages under /var/log - I am running fedora core (does the version even matter?)

Jun 20 16:50:52 mya INADYN[12590]: INADYN: Started 'INADYN version 1.96' - dynamic DNS updater. 
Jun 20 16:50:52 mya INADYN[12590]: I:INADYN: IP address for alias 'mysite1.com' needs update to '75.71.21.120' 
Jun 20 16:50:52 mya INADYN[12590]: I:INADYN: IP address for alias 'mysite2.com' needs update to '75.71.21.120' 
Jun 20 16:50:52 mya INADYN[12590]: I:INADYN: Alias 'mysite1.com' to IP '75.71.21.120' updated successful. 
Jun 20 16:50:53 mya INADYN[12590]: I:INADYN: Alias 'mysite2.com' to IP '75.71.21.120' updated successful. 

Now if you don't want to be running inadyn manually at the command line, and rather have it be an automated process, just add it to your crontab just like jdpipe suggests in this thread. 

hope that helps.

---

