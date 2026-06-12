---
title: "How to do dual boot with raid ?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by jam_1410 on 2006-12-11
Hi

I would like to try Linux for the first time in my life. I've heard great things about Ubuntu so decided to start with it. I'm absolute beginer as far as Linux goes. I'm planning to fresh install my Windows XP this holiday break and decided that it would be a great time to add Linux to try.

Here is my problem:

I'm planning to run Windows on the software RAID 0 (nvidia) - two SATA drives. This is my bread and butter and I would really, really, really like to keep them as a single NTFS partition unaffected by Linux whatsoever.

For the Linux part I'm prepared to buy ~60 to ~80 GB drive (doesn't matter if it is PATA or SATA) that will be dedicated strictly for Ubuntu Linux and a FAT32 partition to exchange files with Windows. It will not be in any RAID configuration.

My question is, how that can be done to dual boot ? Is it possible ?

If it is not possible, is it possible to go to BIOS at the power up time and switch between hard drives to select one that is bootable and suceed that way ?

Any help will be appreciated. Please, use simple terms since I know almost nothing about Linux and I'm not a big expert on Windows or PC construction either.

Jack

---

### Post by syrleb on 2006-12-11
you could always just keep ur ubuntu one unplugged unless u wish to use it, and ur windows hard drive unplugged when using ubuntu, this way nothing will intefere with the two operating sytems and nothing can possibly go wrong...i have seen this being done at my friends house and he still does it

---

### Post by psusi on 2006-12-12
Yes, you can easily install ubuntu to the stand alone drive and dual boot.  If you want ubuntu to recognize the windows raid array, you will need to roll up your sleeves and try to follow [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  If you are running edgy you will need to download and install the fixed dmraid package attached to the bug report linked to in the howto.  

Done correctly, you can even shrink your windows partition on the raid array, and dual boot with windows on it, and forget about the spare slow drive.

---

### Post by gn2 on 2006-12-12
So long as you don't need to access files on the RAID array from Ubuntu it's simple enough, here's one way: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Nachtengel on 2007-01-29
Is there a way to do something similar only running Ubuntu on a linux software RAID and installing Windows on spare space at the end of these drives?

---

