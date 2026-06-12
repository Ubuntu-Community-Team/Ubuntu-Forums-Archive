---
title: "How I install Ubuntu in a PcLinux computer"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Zodiac33 on 2008-01-12
I just load my laptop with PcLinux, but I didn't like it!  
So my next choice was Ubuntu, then I realize that I can install Ubuntu in my computer( was unable to read the Ubuntu CD), my second step and when the things start to go wrong come with the Fedora, I install Fedora but I think I made a mistake in some part of the instalation, and I couldn't use it.
My third step was trying to come back to the PcLinux but is not working to.

I'm still able to read the PcLinux Live CD, but is not possible to install it again the computer stop in a point 

GRUB Loading stage1.5.

GRUB loading, please wait...
_ (prompt blinking)

when I try to make the reboot.

I'm a beginner in Linux sys (You can see that) so if you can help me load the Ubuntu 7.10 I'll really appreciate that.

Thanks.:confused:

---

### Post by rowanparker on 2008-01-12
You could just load up a LiveCD (any, even DSL) and wipe the drive then try again.

---

### Post by Zodiac33 on 2008-01-12
Yes I already try to do that, insert again the Live CD (PcLinux) because is the only one that the computer can read.
But every time that the computer boot again I get stock in the same point.
The one that I mention before.

So what is the next steep?
What I can do?

---

### Post by rowanparker on 2008-01-12
Have you tried the Ubuntu Alternate disk?
Or is the cd drive not reading CD's well or is it the CD's not being able to boot?

---

### Post by bagguley on 2008-01-12
Can you enter the grub menu (hit esc or something right at the start of the boot)?

---

### Post by Zodiac33 on 2008-01-12
The computer read the PcLinux CD but not the Ubuntu.
I have another computer and the Unbutu CD runs well there.

---

### Post by Zodiac33 on 2008-01-12
No is not possible to type or do any actions at this point, the only that I can do is run the Pclinux CD

---

### Post by bagguley on 2008-01-12
Just to confirm you are trying to install ubuntu 7.10, youre not some how ended up with the 8.04 alpha testing disk?

The next step would be to try and install with the alternative disk as mentioned above. When you install make sure you wipe the entire drive so you can rule out duel boot probs.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and tick the box for the alternative disk.

---

### Post by ayenack on 2008-01-12
Zodiac33 take a look at [this site]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") and follow the instruction carefully. If don't have any other OS on the PC download the Super Grub Disk of your choice and use that to sort out your problems. The other way to do it is to use a MSDOS disk and format your drive with that. You need to either adjust or delete your MBR (Master Boot Record.)

---

### Post by Zodiac33 on 2008-01-12
I don't know anything about the alpha something, but thanks I'm going to look a new Ubuntu disk and start the process again.
I'll let you know what happens next.

Tanks.

---

### Post by ugm6hr on 2008-01-12
> **Zodiac33 said:**
> The computer read the PcLinux CD but not the Ubuntu.
I have another computer and the Unbutu CD runs well there.

At what stage does the Ubuntu LiveCD get stuck?

---

### Post by Zodiac33 on 2008-01-12
ayenac, I don't have 1G in my RAM

---

### Post by ayenack on 2008-01-12
No No Nooooo they are just my tag lines (signatures) ignore them they are nothing to do with this thread. If you go to the site I linked earlier to you should be able to download a Super Grub Disk and use that to sort out your problems.

Here's the site to look at.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Read through the help me and instructions before you do anything.

---

### Post by ayenack on 2008-01-12
> **ugm6hr said:**
> At what stage does the Ubuntu LiveCD get stuck?

I'm pretty sure Zodiac33 is having problems with MBR. GRUB is on there and she/he can't get it off also she/he can't get the Ubuntu LiveCD to load. Not sure why PCLinuxOS wont delete it but I've known a lot of people have the same problems when trying to install XP over a Linux install as well. Could just use an MSDOS Floppy to format the drive it'd do the same thing.

---

