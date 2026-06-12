---
title: "vmware tools frustration"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by N3r0H on 2007-09-18
Hey guys i was wondering if anyone could help me out. I installed ubuntu ultimate but am having problems finding vmware tools for fusion and installing it. I swear I have tried everything to get this working but my abilities are limited. Any help would be much appreciated. Ubuntu inside of macbook pro.

---

### Post by N3r0H on 2007-09-18
When I try to "install VMware tools" from the menu it appears it can't find them. This is getting very frustrating. Is there even these tools available for Ultimate or am I jst chasing my tail here.

---

### Post by HermanAB on 2007-09-18
Yup, the intructions are not exactly helpful are they?  You got to ignore the instructions, they don't work!

VMware Tools is part of VMware Workstation.  You can download an evaluation copy of VMware Workstation for free (got to give them your whole identity for that).  Get the tarball, not the rpm.  Untar the ball and look for the ISO images hidden in there somewhere.  Burn the Linux and Windows tools ISOs to a couple of discs (this is not necessary, but it is much easier this way).

Now start up your VM (Linux or Windoze) and wait for it to come up properly and log in.  Plug the appropriate CD in the drive.  I always have to put the CD in, then pop it out and put it in immediately a second time to get the thing to see it.

In the case of Windows, it will autoinstall and will tell you how to adjust the display - can't be easier really, once you know what you really have to do.  

In the case of Linux, you got to install it twice - gawd knows why.  Go to the tools CD and install the rpm, then copy the tar ball to the VM, untar it and run the setup utility hidden in there.  Once installed again, restart the VM and log in and life should be a helluvalot better.

Cheers,

Herman

---

### Post by N3r0H on 2007-09-18
Thanks Herman for giving me a hand. One question though will these tools works for other linux distros like Backtrack/Suse/Fedora as well?

---

### Post by HermanAB on 2007-09-18
The tools work on anything because it compiles itself from source.  So you have to install the kernel source first!

---

### Post by N3r0H on 2007-09-19
Well I can't even seem to get past the dowload part, I get a error half way through the dl. Is there any other place to get this?

---

### Post by N3r0H on 2007-09-19
Nevermind, thanks demonoid

---

### Post by N3r0H on 2007-09-19
Almost done but I'm not sure what "run the setup utility hidden in there" means.

---

### Post by N3r0H on 2007-09-19
What are the benefits of VMware tools anyway? Move files between boxes?

---

### Post by N3r0H on 2007-09-19
Oh yeah I couldn't mount the disk, some error so I copied from a usb stick and installed the RPM from inside already. So do I have to do it again or do I need to install from cd first. I patiently wait for you HermanAB.

---

