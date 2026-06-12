---
title: "upgrade kernel"
date: 2012-04-28
forum: Apple Hardware Users
---

### Post by derxen on 2012-04-28
Can anyone help me with this problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/988957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/988957)?
The problem appears to be that there is no file /boot/initrd.img-3.2.0-24-powerpc-smp, while /boot/initrd.img is not a symlink, but the actual initrd.img. So: should I rename that file to  /boot/initrd.img-3.2.0-24-powerpc-smp and make a symlink to it named /boot/initrd.img? I'm just checking, before I mess things up irrepairably.

---

### Post by rsavage on 2012-04-28
When did you install? Did you use a live/desktop CD? 
 
Can you check the file described in this bug [https://bugs.launchpad.net/ubuntu/+source/live-build/+bug/958839](https://bugs.launchpad.net/ubuntu/+source/live-build/+bug/958839) please?
 
It looks also like you've got both the 32 bit and 64 bit kernels installed. Unless you've done this then there is a problem with the installer or kernel packages.

---

### Post by derxen on 2012-04-28
I installed from the livecd/usb a couple of weeks ago, and this problem appeared when upgrading to the release. I did check that bug, because it seems similar. I edited /etc/kernel-img.conf as suggested, tried upgrading again but got the same error. I don't know how I could have both the 32 and 64 kernels installed, it's certainly not something I did intentionally.

---

### Post by rsavage on 2012-04-28
You'll have to remove, possibly 'purge' the new new kernel package(s) and then re-install for the changes to take effect.

---

### Post by derxen on 2012-04-28
Very strange. I purged the new kernels (you were right, there were two), but apt-get update and upgrade doesn't get the new kernel back. vmlinux in /boot is now 3.2.0-23-powerpc64, but system settings gives the os as 32 bit. I also have both a 32 and a 64 version of system.map, abi and config in /boot

---

### Post by rsavage on 2012-04-28
To install new kernel packages (from the terminal) you'll need
 
sudo apt-get dist-upgrade
 
Did you select the live64 option when you installed?
 
The CD has the 32 bit and 64 bit kernels installed.  They get copied over and then the one that isn't used should be removed.  By the sounds of it you're still setup like the CD.
 
I would remove any kernel packages that don't have 64 in them.  So from memory things like linux-image-powerpc-smp or linux-powerpc-smp should be removed.  
 
> 
system settings gives the os as 32 bit

The packages are all 32 bit except the kernel.  So that maybe why you see this?

---

### Post by derxen on 2012-04-28
I purged the remaining 32bit image, so linux-image-3.2.0-23-powerpc64-smp is the one that remains. System.map, abi and config are now all 64 in /boot, but system settings still gives os as 32 bits. If I try dist-upgrade I still get 0 to upgrade however.

---

### Post by derxen on 2012-04-28
So I decided to install the powerpc64 metapackage (which apparently had been removed or had never been there) and then I got the exact same error again: it tries to set up the new image, but then cannot find /boot/initrd.img-3.2.0-24-powerpc64-smp
Yet my kernel-img.conf is correct now.

---

### Post by rsavage on 2012-04-28
Your problem stems from what happened on your install [http://ubuntuforums.org/showthread.php?t=1954070](http://ubuntuforums.org/showthread.php?t=1954070) .  Did you install to an external drive or something?

---

### Post by derxen on 2012-04-28
No, I installed to the first of the two internal hard drives, sda. What is the problem do you think?

---

### Post by rsavage on 2012-04-28
> **derxen said:**
> What is the problem do you think?
 
Dunno, you don't give a lot to go on.  I think you should still have the syslog from your install somewhere in the /var/log directory.  You need to look at that.
 
Do a search for "InstallStepError: YabootInstaller failed" in the syslog from the install.  If you have that then it is probably the same problem as [https://bugs.launchpad.net/ubuntu/+source/yaboot-installer/+bug/956481](https://bugs.launchpad.net/ubuntu/+source/yaboot-installer/+bug/956481) .
 
You'll be missing the last bit of the install which sorts out the kernels plus other stuff.  If it was me I'd re-install, but it's best to work out what the problem was first.

---

### Post by derxen on 2012-04-29
I cannot find an installer log. Looking through dpkg.log I do notice that most packages are marked 'half-installed'. I hesitate to reinstall, because basically every time I've installed the process aborted after installing the packages, more or less as the poster of that bug mentions (but earlier, I think). So my problem certainly seems similar. But unless I know what the cause is, there's no use reinstalling. One further data point, don't know whether it's relevant: during boot I get the error 'dev/adb' not found.

Is it crazy to try and reinstall just the half-installed packages?

---

### Post by rsavage on 2012-04-29
In /var/log you should have an installer diectory.  In that will be the syslog.  To look at it you'll have to open it with root privileges. 
 
Have you tried the alternate install or an up-to-date live cd?

---

### Post by derxen on 2012-05-02
There is no installer directory in /var/log, I guess that's one of the casualties of the incomplete installation process. If I have time trying the alternate install before we sell this machine (time's running out) I&#314;l let you know how that worked out. Thanks for all the help.

---

