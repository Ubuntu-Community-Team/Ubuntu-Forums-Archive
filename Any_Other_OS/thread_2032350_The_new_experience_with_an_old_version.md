---
title: "The new experience with an old version"
date: 2012-07-23
forum: Any Other OS
---

### Post by Nikolai D. on 2012-07-23
hi there,

ive installed easypeasy 1.5 on my asus eeepc 1000h.
Now i wanted to run virtualbox 3 on it. But vbox needs i guess to recompile the headers or whatever it is that it means. But i cant install the headers because i have kind of outdated repositories. Or thers a mismatch. Because it also looks that i have the headers installed.

So im asking myself is there any way i can upgrade easy peasy to 1.6? Or edit the souces so i could be hooked up to a more recent version of repos.
Or if theres some way i can get vbox running? That would be enough for me.

i didnt install 1.6 in the first place because the install didnt worked somehow.

thanks in advance,
Nikolai

p.s. As more explanation u have as more im happy to learn new things

---

### Post by papibe on 2012-07-23
Thread moved to **Other OS/Distro Talk**.

---

### Post by Nikolai D. on 2012-07-27
here is some additional info.

ndo@EesyPC15:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for ndo: 
 * Stopping VirtualBox kernel module                                                                                          *  done.
 * Recompiling VirtualBox kernel module                                                                                      
 * Look at /var/log/vbox-install.log to find out what went wrong
ndo@EesyPC15:~$ tail /var/log/vbox-install.log
Makefile:147: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
ndo@EesyPC15:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.30.5-ep0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ndo@EesyPC15:~$ uname -a
Linux EesyPC15 2.6.30.5-ep0 #10 SMP PREEMPT Thu Aug 27 19:45:06 CEST 2009 i686 GNU/Linux
ndo@EesyPC15:~$

---

### Post by Nikolai D. on 2012-07-27
ok solved it using this
sudo ln -s linux-headers-2.6.30.5-ep0 linux
from here
[https://forums.virtualbox.org/viewtopic.php?f=7&p=99019](https://forums.virtualbox.org/viewtopic.php?f=7&p=99019)

---

