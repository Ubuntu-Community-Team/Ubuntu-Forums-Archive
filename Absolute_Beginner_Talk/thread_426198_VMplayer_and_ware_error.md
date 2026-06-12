---
title: "VMplayer and ware error"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-04-28
I receive this error when I try to remove Vmplayer. 


[IMG]http://i11.tinypic.com/2sajtkk.png[/IMG]

[IMG]http://i18.tinypic.com/3zgwrqg.png[/IMG]

Then it shows I have an update and this is what I get.

[IMG]http://i13.tinypic.com/4i3kilj.png[/IMG]

joe203@joe203-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl0.9.7 vmware-player-kernel-modules
The following NEW packages will be installed:
  libssl0.9.7 vmware-player-kernel-modules
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2307kB of archives.
After unpacking 5362kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package vmware-player-kernel-modules.
(Reading database ... 113173 files and directories currently installed.)
Unpacking vmware-player-kernel-modules (from .../vmware-player-kernel-modules_2.6.20.15.14_i386.deb) ...
Selecting previously deselected package libssl0.9.7.
Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7k-3_i386.deb) ...
Setting up vmware-player-kernel-modules (2.6.20.15.14) ...
Setting up libssl0.9.7 (0.9.7k-3) ...

Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
cp: cannot create regular file `/etc/vmware/locations': No such file or directory
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe203@joe203-desktop:~$

I have tried to install VMworkstation ,  virtualbox and qemu, I tried to reinstall VMplayer but this error keeps getting in the way how can I fix this.

---

### Post by fwojciec on 2007-04-28
Could you post the output of "ls /etc/vmware"?

---

### Post by fwojciec on 2007-04-28
OK, here is a suggestion, it allowed me to uninstall vmware-player when my installation failed via apt-get failed.

Step 1.
Find the folder /etc/vmware and make sure it is empty (delete everything inside) - you have to do it as root (use sudo, or, if you need a gui run Alt-F2 "gksudo nautilus")
Step 2.
Create a folder named "locations" inside the /etc/vmware folder ("sudo mkdir /etc/vmware/locations")
Step 3.
sudo apt-get remove vmware-player
Step 4.
If it worked you can remove /etc/vmware folder (it needs to be removed in case you want to install vmware in the future)

It's a hack, but it worked for me - mind you, I was getting a different error (the reason my installation failed was different), but it might work for you as well.

---

### Post by Repent on 2007-04-28
> **fwojciec said:**
> Could you post the output of "ls /etc/vmware"?

joe203@joe203-desktop:~$ ls /etc/vmware
ls: /etc/vmware: No such file or directory
joe203@joe203-desktop:~$

---

### Post by Repent on 2007-04-28
> **fwojciec said:**
> OK, here is a suggestion, it allowed me to uninstall vmware-player when my installation failed via apt-get failed.

Step 1.
Find the folder /etc/vmware and make sure it is empty (delete everything inside) - you have to do it as root (use sudo, or, if you need a gui run Alt-F2 "gksudo nautilus")
Step 2.
Create a folder named "locations" inside the /etc/vmware folder ("sudo mkdir /etc/vmware/locations")
Step 3.
sudo apt-get remove vmware-player
Step 4.
If it worked you can remove /etc/vmware folder (it needs to be removed in case you want to install vmware in the future)

It's a hack, but it worked for me - mind you, I was getting a different error (the reason my installation failed was different), but it might work for you as well.

I don't have a /etc/vmware folder.

---

### Post by fwojciec on 2007-04-28
In that case try creating it:

> sudo mkdir /etc/vmware

and then create the location folder

> sudo mkdir /etc/vmware/locations

and follow the rest of the steps.

---

### Post by Repent on 2007-04-28
Wow that worked Thank you.

---

### Post by fwojciec on 2007-04-28
You're welcome :)

---

### Post by nikosuoa on 2007-05-01
fwojciec you are the best, joined the forum just to thank you!

---

### Post by erthian on 2007-05-13
> **fwojciec said:**
> OK, here is a suggestion, it allowed me to uninstall vmware-player when my installation failed via apt-get failed.

Step 1.
Find the folder /etc/vmware and make sure it is empty (delete everything inside) - you have to do it as root (use sudo, or, if you need a gui run Alt-F2 "gksudo nautilus")
Step 2.
Create a folder named "locations" inside the /etc/vmware folder ("sudo mkdir /etc/vmware/locations")
Step 3.
sudo apt-get remove vmware-player
Step 4.
If it worked you can remove /etc/vmware folder (it needs to be removed in case you want to install vmware in the future)

It's a hack, but it worked for me - mind you, I was getting a different error (the reason my installation failed was different), but it might work for you as well.

Wow, that did the trick.  How the hell did you figure that out???

---

### Post by takos on 2007-05-13
Thanks, I was struggling with the same issue. This resolved it... :)

---

### Post by Bengaul on 2007-06-28
Ah-ha!! :p TY!!

---

### Post by kevin41_uk on 2007-08-02
> **fwojciec said:**
> OK, here is a suggestion, it allowed me to uninstall vmware-player when my installation failed via apt-get failed.

Step 1.
Find the folder /etc/vmware and make sure it is empty (delete everything inside) - you have to do it as root (use sudo, or, if you need a gui run Alt-F2 "gksudo nautilus")
Step 2.
Create a folder named "locations" inside the /etc/vmware folder ("sudo mkdir /etc/vmware/locations")
Step 3.
sudo apt-get remove vmware-player
Step 4.
If it worked you can remove /etc/vmware folder (it needs to be removed in case you want to install vmware in the future)

It's a hack, but it worked for me - mind you, I was getting a different error (the reason my installation failed was different), but it might work for you as well.
Great trick, worked fine for me, have been stuck with this slowing down updates for a few days now.

many thanks

---

