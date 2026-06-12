---
title: "Dual-Booting, simple question"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by blackbeastofaarrgh on 2005-07-29
Hey,
I'm a total newbie to Linux, and I just tried Ubuntu Live today, which was also my first time with Linux. I love it, and I want to know if there's a simple way to have Windows XP on one hard drive, and Ubuntu on another, for a dual-boot system.
Thanks in advance!

---

### Post by Sam on 2005-07-29
No problems, if you install Ubuntu after Windows. You'll be asked during the installation if you want to keep Windows and how to do a dual boot menu.

Read this: [Wiki WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by blackbeastofaarrgh on 2005-07-29
Thanks!
Ubuntu is so much easier than the other distros . . . .

---

### Post by byen on 2005-07-29
yup! during windows installation, windows is automatically detected and it will ask you if you wanna keep it.just say yes..and use the other HD to install linux.

A world of advice:
- Please allow ample space to be given to for swap. Maybe your RAM x 2
- If you regularly switch between Windows and Linux.. you might wanna create a Fat 32 drive as well so that you can have common files down there..you can read/write from both OS's on an FAT 32.(this option is provided during install as well!)

goodluck. If any issue arises...we are always here!

---

### Post by blackbeastofaarrgh on 2005-07-30
Okay . . . when booting my machine the GRUB bootloader gives me an 'Error 21' and I can't boot into Ubuntu or Windows. I know there's probably a stupidly simple solution to this, but I can't figure it out.
I installed Ubuntu on my slave harddisk, in case that might have something to do with it.
Would my BIOS settings have anything to do with it?
And I REALLY don't want to re-install XP again . . .
Anyone have any ideas?

---

### Post by Sam on 2005-07-30
It's a BIOS problem. Try [this](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html).

---

### Post by blackbeastofaarrgh on 2005-07-30
Thank you so much! I thought I was totally screwed . . .
Everything works wonderful, XP and Ubuntu work perfectly.
Thank you!!!

---

### Post by Sam on 2005-07-30
You're welcome! Enjoy your new OS.

---

### Post by mental_noise on 2005-08-01
hello. i'm a new user and tried Ubuntu live just yesterday. i'm just wondering of dual booting will work with a partitioned HD? :roll:

---

### Post by kaffeend on 2005-08-01
Hey everyone, like so many others, I too am a Linux n00b... But I am hoping that Ubuntu will be a whole new world of opportunity for me.  Unfortunately, as a gamer and modder I need to hang onto Windows for those things, so I would like to setup a dual boot system. Here's where I'm having trouble: I have a SATA hard drive, and Windows setup cannot detect the device - I have to use a floppy to tell it that I have a SCSI ( ? ) device installed... I'm told that Linux distros don't have this problem, so I would like to install Ubuntu first - not Windows. Now, from what I have read, I gather Windows is typically, if not exclusively installed first in dual boot configurations. Can anyone confirm this for me please?

Also, I am way lost when it comes to filesystems - even after reading every link from this thread! - so can someone please tell me if I can install Ubuntu on NTFS partitions, and what the default names for these partitions would be? Thanks in advance.

kaffeend

---

