---
title: "iMac G5 Rev C"
date: 2007-06-07
forum: Apple PPC Users
---

### Post by Reed206 on 2007-06-07
I am new to Ubuntu and can't install Feisty on my iMac G5 Rev C.

Does anyone know how to install on my machine?

---

### Post by Auria on 2007-06-07
Can you describe what you mean by "can't install" ?

Can't downlaod? Can't burn the CD? Holding C doesn't work? Crashes before anything happens? X fails to satrt? etc. etc.

---

### Post by Reed206 on 2007-06-07
Sorry, I've burned the CD and tried an install from it. I only got a black screen.

I then customized the install with updated yaboot from [https://wiki.ubuntu.com/iMacG5revC](https://wiki.ubuntu.com/iMacG5revC). The install still hung.

Don't know how to proceed from here.

---

### Post by stmiller on 2007-06-07
The live cd doesn't work for some iMac G5 users, as reported in the past. No video, sound, and other stuff.
There is an 'alternate' PowerPC cd which goes right to the Feisty installer (no pretty live desktop). So try to install with the alternate CD.

EDIT: Read this, esp at posts at the very end.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23445](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/23445)

---

### Post by Reed206 on 2007-06-10
Thanks, the alt install disk did the trick for getting the install to work. Now I have another problem:

I installed on to a Firewire external drive. When I hold the Option key while booting, I get to the startup disk chooser and I get a button for Linux. Clicking it takes me to a black screen with the following white text:

First Stage Ubuntu Bootstrap

Press l for Gnu/Linux,
x for MacOSX,
c for CDROM

I press l, but it just jumps back to the chooser screen.

I read that I need to edit the yaboot file, but since I'm a newbie I don't know how to edit a file on the Ubuntu drive from within OS X.

Can anyone help?

---

### Post by Jimbob17 on 2007-06-11
> **Reed206 said:**
> Thanks, the alt install disk did the trick for getting the install to work. Now I have another problem:

I installed on to a Firewire external drive. When I hold the Option key while booting, I get to the startup disk chooser and I get a button for Linux. Clicking it takes me to a black screen with the following white text:

First Stage Ubuntu Bootstrap

Press l for Gnu/Linux,
x for MacOSX,
c for CDROM

I press l, but it just jumps back to the chooser screen.

I read that I need to edit the yaboot file, but since I'm a newbie I don't know how to edit a file on the Ubuntu drive from within OS X.

Can anyone help?

There is some software to allow you to mount Linux partitions under OS X, click [here](http://sourceforge.net/projects/ext2fsx/) for the homepage. I haven't used it much, so I'm not sure if you have write permissions to the partitions.

HTH

---

### Post by powerpc64 on 2007-06-17
Suggestion, reverse the approach.

OS X can boot from Firewire, so put OS X there, and Ubuntu on the internal SATA drive.  You will need Carbon Copy Cloner or equivalent to move OS X over.  Use the control panel to "bless" the Firewire disk as the new startup device.

Reboot without the CD, and from this Firewire-based OS X session, wipe the internal SATA drive clean (so Ubuntu won't detect it when it configures yaboot).

Then boot the Ubuntu alt-install CD.  You have a 64-bit CPU, so use install-powerpc64 at the boot prompt.

If Ubuntu is still giving you trouble try [http://www.t2-project.org](http://www.t2-project.org) where you'll find PPC64 is actively supported.  There is going to be a new release soon, the Release Candidate is already out.

---

