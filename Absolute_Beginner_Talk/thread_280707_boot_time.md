---
title: "boot time"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Avinator on 2006-10-19
Hello,

I am new here and I was wondering why it takes close to 4 minutes for Linux to boot ? I see boot times ranging from 40 secs to 1.5 minutes..Did I do a wrong install ? After booting, UBUNTU works GREAT ! Love it...much more than windows 8) 

Any help would be appreciated .... ( ps Ubuntu is the only os the hd ) oh...almost forgot...whats a good firewall to use ? I use Zone Alarm with xp..

Cheers !

---

### Post by 3rdalbum on 2006-10-19
Firewalls: Just use the inbuilt "iptables" firewall, which you can configure using Firestarter. You really don't need anything more powerful than that.

Are there any stages of your boot that seem to take a long time? Knowing this is probably the key to figuring out the problem (and then submitting a bug report)

---

### Post by podunk on 2006-10-19
About the firewall – it's built in. There is a GUI to configure and control it called “Firestarter”. I can't remember if it's part of the default install or not. If it is part of the default install look in 
Applications
Internet
Firestarter

If it's not there then install it with Synaptic Package Manager:
System
Administration
Synaptic Package Manager
Search – enter firestarter
When the search is done right click on firestarter and chose “Mark for installation”
Click the “Apply” button on the top
Once again though - the firewall is built in and on by default. You check it by going to
[www.grc.com](www.grc.com)
and clicking the "Sheilds Up!" link about halfway down the page.

As far as the boot up – I don't know? All the Linux's I tried booted up very fast, and Ubuntu is very fast on every machine I've tried.

One of the things you might check is your BIOS Options:
floppy seek at boot = should be off
Set your start up drive to be your hard drive instead of your cd-rom (and if you do keep your cd rom first – make sure there is no disk in it)
Enable fast POST
Disable additional memory checking

Does it sort of hang at the disk detection part? If so, visit your hard drive manufactures site, they will have a diagnostic utility – this is often a sign of impending hard drive failure.

If it's the Ubuntu part that is slow – do you have the right kernel? I don't know this for sure, but would bet that if you installed the AMD64 onto a Intel P4 machine it could cause trouble.

---

### Post by ReaderRat on 2006-10-19
Enter this in Terminal:
```
sudo aptitude update
```
Then run this:
```
sudo aptitude install firestarter
```

firestarter is a GUI for your firewall.

EDIT: Whoops....Late, Again !!

---

### Post by Avinator on 2006-10-20
Thank for the replies ! GRC! Oh....Do I rememer GRC! Great  website...as far as the boot time * new drive. It boots straight from the drive ...It seems it hangs when is accesing the "root directory"..Is the second item from the list- thats the most hang time. Otherwise, Ubuntu keeps growing on me :D 

The more I use it the more I enjoy it ! I am sure I will have other questions as I venture into the unknown...:cool: 

I did install firestarter and it works great !

Cheers !

---

### Post by jordanmthomas on 2006-10-20
You can see what takes the longest by installing a package called bootchart
```
sudo aptitude install bootchart
```

After a reboot, check /var/log/bootchart for a nice pretty graph of your boot.

---

### Post by Avinator on 2006-10-20
Thanks for the info. I am getting error messages:


Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suitefile:///home/avinator/Desktop/Screenshot.png

 system-config-cluster

I also get error messages when doing updates... see jpeg if posted properly.... Thanks for your help !

---

