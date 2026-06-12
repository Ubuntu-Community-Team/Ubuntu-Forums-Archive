---
title: "2 HDDs, Windows + Ubuntu"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Arog on 2007-02-16
Hi,
I tried installing ubuntu earlier and I ended up screwing my Windows installation. The way my computer was set up was:
Hard drive 1 - 80gb
hard drive 2 - 320gb...I installed windows on here

I then proceeded to format the 80gb and install ubuntu/grub on there. Now I cannot access windows anymore (It says NTLDR is missing). So I tried swapping the harddrives so that hard drive 1 is 320gb and harddrive2 is 80gb...did a fixmbr from recovery console and no luck. NTLDR is missing.

So my plan is to start fresh by deleting both Windows and Ubuntu and installing everything again.

So now my set up is : SATA 1 - 320 gb, SATA 2 - 80gb. Windows on the 320, and Ubuntu on the 80. I know I should install Windows first then install Ubuntu, which will put Grub on the 320 (the primary) right?

Also, I didn't see any jumpers on the back of my harddrives, the new 320gb only has 1 jumper for either : SATA at 1.5 gb/s or SATA at 3 gb/s. Am I supposed to put something else in there? Thanks

Also, do you guys have any other ideas or is my original plan (windows on the 320 and ubuntu on the 80) sound good?

Thank you

---

### Post by kittyhawk63 on 2007-02-16
I have WindowsXp on a 40 gb. drive and Ubuntu on my 80GB drive. When I inserted the Live CD and clicked "install" it gave me a choice of what drive I wanted to install Ubuntu. I chose the drive without Windows. It installed without so much as a whimper. Sorry you are having trouble. Someone here should be able to help. I am too new to know how to resolve the problem, however. Good luck. Just hang in there.

---

### Post by nudnik on 2007-02-16
> **Arog said:**
> Hi,
I tried installing ubuntu earlier and I ended up screwing my Windows installation. The way my computer was set up was:
Hard drive 1 - 80gb
hard drive 2 - 320gb...I installed windows on here

I then proceeded to format the 80gb and install ubuntu/grub on there. Now I cannot access windows anymore (It says NTLDR is missing). So I tried swapping the harddrives so that hard drive 1 is 320gb and harddrive2 is 80gb...did a fixmbr from recovery console and no luck. NTLDR is missing.

So my plan is to start fresh by deleting both Windows and Ubuntu and installing everything again.

So now my set up is : SATA 1 - 320 gb, SATA 2 - 80gb. Windows on the 320, and Ubuntu on the 80. I know I should install Windows first then install Ubuntu, which will put Grub on the 320 (the primary) right?

Also, I didn't see any jumpers on the back of my harddrives, the new 320gb only has 1 jumper for either : SATA at 1.5 gb/s or SATA at 3 gb/s. Am I supposed to put something else in there? Thanks

Also, do you guys have any other ideas or is my original plan (windows on the 320 and ubuntu on the 80) sound good?

Thank you

The easiest way to do this is make the primary disk the Windows disk. Install Ubuntu to the secondary. At the end of the install Ubuntu will ask if you want GRUB installed to the master boot record, and that it has found another OS, Windows, on that disk. Answer "yes" and when you reboot you should see a nice DOS-like GRUB screen with options to boot either Windows or the Ubuntu kernel.

---

### Post by kittyhawk63 on 2007-02-16
Nudnik is correct. That is exactly as I saw it on my install.

---

### Post by old_geekster on 2007-02-16
Okay, SATA drives don't require jumpers to be set.  They are each connected by a separate cable.  They are both considered to be a "Master".

Here is the link to a great guide:

[http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html)

Follow this guide and you will have Ubuntu running in approximately 30 minutes.

Good luck!

---

### Post by CzarDominus on 2007-04-01
> **nudnik said:**
> The easiest way to do this is make the primary disk the Windows disk. Install Ubuntu to the secondary. At the end of the install Ubuntu will ask if you want GRUB installed to the master boot record, and that it has found another OS, Windows, on that disk. Answer "yes" and when you reboot you should see a nice DOS-like GRUB screen with options to boot either Windows or the Ubuntu kernel.

Quick question if you guys don't mind, at the end of the installation the option to where you want GRUB installed is given by a small button that states:

[CENTER]GRUB will be installed to (hd0)[/CENTER]

where you can click "(hd0)" in order to change it. Are you guys suggesting that I leave that as is (since Windows is primary and thus should be hd0)? Thanks for the help.

---

### Post by NicoleM on 2007-04-01
> **CzarDominus said:**
> Quick question if you guys don't mind, at the end of the installation the option to where you want GRUB installed is given by a small button that states:

[CENTER]GRUB will be installed to (hd0)[/CENTER]

where you can click "(hd0)" in order to change it. Are you guys suggesting that I leave that as is (since Windows is primary and thus should be hd0)? Thanks for the help.


I have a similar setup, and I kept grub on hd,0 (the mbr of teh windows hard drive) and have had everything run smoothly thus far.

from what I understand you CAN install grub on the secondary hard drive, but I'm not sure of the advantages or disadvantages of this or if it requires any additional tweaking.  Hopefully someone can calrify that, but I just wnated to add my experience that putting grub on hd,0 (first partition of the primary hard drive) has worked great for me with windows on the master and ubuntu on the slave drive.

---

