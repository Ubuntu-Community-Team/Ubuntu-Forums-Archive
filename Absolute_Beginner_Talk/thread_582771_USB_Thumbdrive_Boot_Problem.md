---
title: "USB Thumbdrive Boot Problem"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by J_C on 2007-10-20
Hello.  Complete Noob here.

I've ran the Ubuntu 7.10 LiveCD ok.  I "thought" I had successfully installed to a USB Flash Thumbdrive per this article, [this Pendrivelinux article]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"), but when it comes time to boot it, I get "This is not a bootable disk" when the bios POST is finished. 

The system in question is a Via C3/CLE266 based, and formerly before Ubuntu FDISK and format (and Lilo attempt, "seemed" to work) it did boot the thumbdrive to DOS when it was formatted using an HP tool to FAT16, it booted to DOS fine using the mobo's bios setting (also how the bios autodetected the thumbdrive) "USB RMD-FDD).  When it formerly booted to DOS ok, I had tried other bios settings and only "USB RMD-FDD" worked.

So I have established the system can boot the thumbdrive before using Ubuntu, but now it won't boot.  I might've missed some step in how to get Lilo working right but I just don't know.

I looked at the /etc/fstab file, one article seemed to suggest it might be important but I saw nothing in the file referring to /dev/sda  (sda1 is the thumbdrive OS partition and sda2 is the casper-rw partition?)

Thanks for any thoughts on this.  Please keep in mind I have no idea what I'm doing, (LOL, I wanted to believe I did, but then it didn't work, so,) a general description of a process won't help as much as exact text lines I need to use to correct the problem if it's possible.

If this post is better made in a different forum group please advise on that.

Thank you.

---

