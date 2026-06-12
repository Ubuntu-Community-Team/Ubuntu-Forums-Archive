---
title: "Virtual box problem"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-06-19
When trying to install VB I get the following :
dpkg -i '///home/benbow/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb' ;echo RESULT=$?
dpkg: status database area is locked by another process
RESULT=2

Any ideas?

---

### Post by thelinuxguy on 2007-06-19
Looks like you have synaptic running at the same time. Close it and try again.

---

### Post by defrex on 2007-06-19
Try restarting, it may free up whatever "database area is locked by another process".

---

### Post by Benbow on 2007-06-19
Yes, it was Synaptic but, the plot thickens, I now get :
benbow@benbow-desktop:~$ /etc/init.d/vboxdrv setup
open: Permission denied
 * Stopping VirtualBox kernel module vboxdrv                                    open: Permission denied
                                                                         [ OK ]
open: Permission denied
 * Recompiling VirtualBox kernel module vboxdrv                                 /etc/init.d/vboxdrv: line 162: /var/lib/vbox-install.log: Permission denied

open: Permission denied
 * Look at /var/lib/vbox-install.log to find out what went wrong

Oh dear!

---

### Post by thelinuxguy on 2007-06-19
I never had to do anything with vboxdrv setup when I installed VirtualBox under Edgy. I just installed from the .deb and it was ready to go. Maybe it  has changed for Feisty. Anyways, try with sudo.

---

### Post by bodhi.zazen on 2007-06-19
LOL

you need sudo :)

```
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

You usually need to run it twice, don't know why, it is a small bug

---

### Post by Benbow on 2007-06-19
Had to retrieve my posting as I am now in this position :
Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult 
/var/log/vbox-install.log to find out why the kernel module does not compile. 
Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup


as root.

 * Starting VirtualBox kernel module vboxdrv

 * No suitable module for running kernel found.

RESULT=0
 
I am unsure as to what to do

---

### Post by Golyadkin on 2007-06-19
I installed VirtualBox 1.4.0 deb for AMD64 Feisty from the virtualbox website. It works straight out of the box and didn't need any configuration.

Btw Benbow, I used to get that warning you have when I ran a beta version of Feisty with a kernel for which Virtualbox wasn't compiled yet.

---

### Post by bodhi.zazen on 2007-06-19
> **Benbow said:**
> Had to retrieve my posting as I am now in this position :
Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult 
/var/log/vbox-install.log to find out why the kernel module does not compile. 
Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup


as root.

 * Starting VirtualBox kernel module vboxdrv

 * No suitable module for running kernel found.

RESULT=0
 
I am unsure as to what to do

That is once, now run the same command a second time :)

```
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

> You usually need to run it twice, don't know why, it is a small bug

---

### Post by Benbow on 2007-06-19
Thanks for the tip but it doesn't seem to matter how many times I run it :
Password:
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/lib/vbox-install.log to find out what went wrong
benbow@benbow-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/lib/vbox-install.log to find out what went wrong
benbow@benbow-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/lib/vbox-install.log to find out what went wrong
benbow@benbow-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/lib/vbox-install.log to find out what went wrong
benbow@benbow-desktop:~$ 

Help.

---

### Post by wolfen69 on 2007-06-19
i had a similar problem and all it took was to uninstall and reinstall.(captain obvious at your service)

---

### Post by bodhi.zazen on 2007-06-19
> Look at /var/lib/vbox-install.log to find out what went wrong

What does the log file tell you then ?

---

### Post by ben2talk on 2008-03-11
Yippeeeeeeeee, so happy today. I don't know what the hell I'm doing - there are rather a confusing number of tools with the gnome interface, so I was lost for about a week.

Number one symptom was a delay between login and seeing the desktop. Then the virtualbox demanded that I recompile the driver EVERY time I start a session before I can use Virtualbox - I set up a launcher with gksudo etc/init.d/vboxdrv setup

Eventually the sesson failed to start up altogether, and I ended up cussing the 'sessions' applet.

Then I found gksu bum. An icon called 'BootUp-Manager' amongst the System/Admin menu items. (you can simply do Alt+F2 and type gksu bum).

The list here is not the same as in the session manager! Here I have some old entries from stuff I tried out last month... So now I unchecked acpi-support (for laptop power management) and 'cinestart' I assume from cinelerra, laptop-mode, and another one interesting...

Disable 'innotek VirtualBox'. WHen I restarted, my X session logged in as quickly as it did when I freshly installed it 4 months ago (but didn't lose any settings - menu still at the side etc.)

Then just click the Virtualbox icon, and it starts up with no trouble - boots XP in 15 seconds hahaha.

I'm so happy :P isn't life sweet?

---

