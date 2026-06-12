---
title: "Grub 22"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by VortexSpin on 2008-01-15
I have a single physical hard drive with two partitions.  One has Windows, the other was just personal files until I wiped it and put Ubuntu on.  I decided Ubuntu wasn't for me (vital software is unsupported by WINE) and used GParted from the Live CD to format the Linux partition and its swap partition back to NTFS and combine the two.  So now I have two NTFS partitions again, Windows on one and nothing on the other.  Problem is that when I boot now I get a Grub error 22 and am dead in the water.

I've looked around and the solution is to use a Windows XP boot disk and fixmbr or fixboot.  Problem is that I have an Acer and the OEM disc doesn't have those functions on there.  I don't have access to a boot disc.  So I downloaded the Ultimate Boot Disc instead, but since the only OS I have access to this the Ubuntu Live CD, and I can't seem to eject the Live CD in order to burn the Ultimate Boot Disc, I'm...uh...at a loss.

What do I do?  I need to get that Ultimate Boot Disc burned; short of finding another computer, is there any way to burn a disc in a Live session?  Or is there another solution?  Thanks.

---

### Post by carverj on 2008-01-15
Yeah, I would either burn on another computer or install a secondary drive, install k3b and burn from live CD!
Hope this helps!!
Have fun
:)

---

### Post by shinythings on 2008-01-15
Yeah, I don't think you can burn a CD in the live session. Can you boot from any other kind of device (USB stick, floppy)?

---

### Post by VortexSpin on 2008-01-15
I might be able to boot USB.  How do I make the UBCD work on a flash drive?

---

### Post by carverj on 2008-01-15
> I have a single physical hard drive with two partitions. One has Windows, the other was just personal files until I wiped it and put Ubuntu on. I decided Ubuntu wasn't for me (vital software is unsupported by WINE)

Vital software?? as in system rescue type thing?

> 
What do I do? I need to get that Ultimate Boot Disc burned; short of finding another computer, is there any way to burn a disc in a Live session? Or is there another solution?

What I would probably do in your situation (assuming I wanted to go Windows) is to re-install linux to the spare partiton and start downloading and burning the necessary Ultimate Boot Disc from there!

---

### Post by VortexSpin on 2008-01-15
Vital as in 'necessary for my continued existence on planet Earth'.  Anyway, I guess that's what I'll do.  Thanks for the help.

---

### Post by shinythings on 2008-01-15
There are ways of getting DOS onto a bootable USB stick if you want to try it (it's a Gentoo guide, but should work for Ubuntu as well): [http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive](http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive)

Probably more trouble than it's worth though, reinstalling is probably easier and quicker.

You could also make a bootable Ubuntu flash stick, which should allow you to burn CDs: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Good luck!

---

