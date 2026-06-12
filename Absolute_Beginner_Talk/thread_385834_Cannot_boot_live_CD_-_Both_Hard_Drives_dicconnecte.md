---
title: "Cannot boot live CD - Both Hard Drives dicconnected!"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by pm63 on 2007-03-16
I want to install Ubuntu, but booting from a live CD does not work for me. 

I have two live CD's: 6.06 LTS and 6.10, and have tried the following with both. I am on WinXP.

I have left the CD in my CD drive, and rebooted, nothing happened. After finding out I had to change my BIOS to boot from CD first, I did so, but when I exited my BIOS:

"Hard drive 0 not found.
Hard drive 1 not found.

Hit F1 to retry, and F2 to enter setup."

I entered setup again, checked everytihing was OK, and exited it. Same error message. I tried changing the boot order back to how it was (HDD First). Same message. At this point I simply pulled the plug and restarted my computer. Thankfully, Windows booted up as normal with no damage done. I went back into BIOS, and changed it again to boot from CD. Same error message, but this time, when I restarted, the settings stuck.

The only problem now is that when I leave the CD in and restart, despite being set to boot from CD, it simply boots into Windows. Every time. 

Help anyone? I have no idea what could be the problem. My specs:

Dell PC (I am told by a friend I shouldn't have gone for them)
256MB RAM 
Intel P4 1.6 Ghz

Has anyone got any idea on what could be the problem? Thanks.

---

### Post by chewearn on 2007-03-16
Check your CD drive in WinXP using another disc, and then the liveCDs.  Is it working?
Also, post the arrangements of your drives in your PC, e.g. IDE0 master 160GB HD, IDE0 slave 80GB HD, IDE1 master CD drive, ...

---

### Post by chaplanger on 2007-03-16
Sounds like the CD you burned may not be bootable.  Check out this "How To" to make certain you do have a bootable UBUNTU ISO file on the CD you are trying to use. (I made this mistake the first time I burned UBUNTU files)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by pm63 on 2007-03-20
Thanks guys, but:

1. I have checked my CD drive, and it works. 
2. The CD's are bootable. One I got from a magazine, and the other was the exact same one my friend installed his Ubuntu off successfully.

AstalaVista, how do I find out my drive configurations?

I think its just my dodgy Dell BIOS...

---

### Post by nudnik on 2007-03-20
> **pm63 said:**
> Thanks guys, but:

1. I have checked my CD drive, and it works. 
2. The CD's are bootable. One I got from a magazine, and the other was the exact same one my friend installed his Ubuntu off successfully.

AstalaVista, how do I find out my drive configurations?

I think its just my dodgy Dell BIOS...

It sounds like your motherboard has an IDE channel device that gives Ubuntu indigestion. I recently discovered some ASUS boards present this problem as well. I believe "Jmicron" was the manufacturer of the offending component.

---

### Post by pm63 on 2007-03-23
So if I tried another distro would it make a difference? What else can I do?

---

### Post by golond on 2007-12-20
not an answer, but further information on the problem:
I recently got a Dell Dimension 8100/Limited and proceeded to install Ubuntu without problem using the DVD drive.  I've since pulled the DVD drive to use in another box, and have put two CD Rom drives into the Ubuntu machine. Both work normally under the OS

Here's the kicker.  I wanted to start over from scratch and tried to boot from the Ubuntu install disk.  Neither CD drive will boot on any IDE setting.  I've swapped the drives from IDE0 to IDE1, master, slave, single ... nothing makes them boot though they work fine when the hard drive is allowed to fully boot into the current Ubuntu install.

It leads me to wonder if the Dell bios has some issues with booting from some types of CD drives.  Try swapping the drive for a different one, if only temporarily. *shrug*  Good luck.

---

