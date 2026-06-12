---
title: "Xubuntu 7.10 on iBook G3 Clamshell"
date: 2008-03-10
forum: Apple PPC Users
---

### Post by Rubix Hacker on 2008-03-10
Hi I have a blueberry Clamshell G3 laptop and I currently have ubuntu 7.04 running on it, whenever I try to upgrade it, it bricks the distro and I have to reinstall. I have tried to install xubuntu using an alternative install cd to no avail. The computer will not install it. Has anyone else got this to work? I need 7.10 to sync my ipod touch. Thanks in advance for any advice.

---

### Post by stream303 on 2008-03-10
> **Rubix Hacker said:**
> whenever I try to upgrade it, it bricks the distro and I have to reinstall.

Where does it fail?  I wonder if your /etc/X11/xorg.conf file was overwritten with Gutsy's  "bulletproof-X" generic one, wiping out your custom horizontal, vertical and dpi settings?

In an earlier thread, a user reported that the install on clamshells was aided greatly by not allowing the installer to detect the keyboard - just manually tell it you are using a US macintosh keyboard....

Does the Gutsy install just drop you to a busybox shell?

---

### Post by Calash on 2008-03-11
I have 7.10 on my Blueberry, works great once you get past the busybox problem.  Where is it dying on yours?

---

### Post by bluebQQk on 2008-03-12
Happy to report Hardy on ibook g3 366 mhz ~576mb ram is running.

Started with hardy daily.. installed to command line.. used this:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
for a guide.

Installed xfce and thunar.

Got updates,upgrades ok.:)

Had some problems getting usb drive and cdrom mounted.

Edited hal.conf to get usb drive and cdrom recognized and mounted
/etc/dbus-1/system.d/hal.conf

not sure i have sound yet.. have not tried.. too tired for now.

I am sure our books are quite alike so you can too.

---

### Post by stream303 on 2008-03-12
First of all - Congratulations!  Hardy on a 320mb G3.  Nice.

But please, what exactly did you edit in your hal.conf file?

Hardy's  ability to recognize my cdrom after boot is the major problem on my G5 iMac.

---

### Post by bluebQQk on 2008-03-12
i added a group=plugdev policy at the bottom. I read about it on the net somewhere..
[http://www.jefferyfernandez.id.au/2007/07/26/a-security-policy-in-place-prevents-mounting-of-volumes/](http://www.jefferyfernandez.id.au/2007/07/26/a-security-policy-in-place-prevents-mounting-of-volumes/)

---

### Post by stream303 on 2008-03-12
Thanks so much.  I'll have to read these carefully and devise a strategy on how to enable this for my application.

Looks like the devs have been running as root for so long that they forgot about the fact that mortal users are going to be using the systems. :)

---

### Post by Rubix Hacker on 2008-03-31
I get stuck at the busybox issue
I have no idea how to fix it, I'm getting 512 mb of ram soon, sorry, computers been offline due to my grounding

---

### Post by Rubix Hacker on 2008-03-31
Yeah it drops me to busybox

---

### Post by stream303 on 2008-03-31
> **Rubix Hacker said:**
> Yeah it drops me to busybox

Have you tried adding modprobe ide-core at the busybox prompt  - maybe preceded with sudo modprobe ide-core ?  

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by Rubix Hacker on 2008-03-31
Thank you so much for helping me! I got it working smoothly now!

---

### Post by Rubix Hacker on 2008-03-31
Thank you so much! it running smoothly now!

---

