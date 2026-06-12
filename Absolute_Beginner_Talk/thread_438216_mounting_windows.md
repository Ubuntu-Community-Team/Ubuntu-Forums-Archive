---
title: "mounting windows"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-05-09
I'm trying to mount windows.  I'm following [pychocat's]("http://psychocats.net/ubuntu/mountwindows") instructions of pasting "sudo fdisk -l" in terminal and I get the following.  Did I lose windows and my data?

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3946    31696213+  83  Linux
/dev/sda2           18699       19452     6056505    5  Extended
/dev/sda3   *        3947       18698   118495440   83  Linux
/dev/sda5           19076       19452     3028221   82  Linux swap / Solaris
/dev/sda6           18699       19075     3028189+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by hyper_ch on 2007-05-09
It seems you deleted windows :(

---

### Post by Acglaphotis on 2007-05-09
Yeah, you lost your windoze partition and data. Sorry to hear that, but, there is no ntfs/fat32 partition where windoze could be installed, and sda1 isnt windows (it only works there aka C drive).

-Acgla

---

### Post by ZeroWing on 2007-05-09
> **hyper_ch said:**
> It seems you deleted windows :(

 Um, I belive that I can speak for ammmom on this partitcular response...

 Ah, crap!

---

### Post by ammmom on 2007-05-09
Gulp.  Okay.  My back up is at my office and I'm home. Is there anyway to "rescue" any of the data?

---

### Post by ammmom on 2007-05-09
> Yeah, you lost your windoze partition and data. Sorry to hear that, but, there is no ntfs/fat32 partition where windoze could be installed, and sda1 isnt windows (it only works there aka C drive).

-Acgla

when you say there is no ntfs/fat 32 partition....... does that mean I could have data or something hidden or does that mean that I have more additional problems.

---

### Post by ammmom on 2007-05-09
> Um, I belive that I can speak for ammmom on this partitcular response...

Ah, crap!

Thanks, better me than you.:confused:

---

### Post by ZeroWing on 2007-05-09
> **ammmom said:**
> when you say there is no ntfs/fat 32 partition....... does that mean I could have data or something hidden or does that mean that I have more additional problems.

 It's just a fancy way of saying that you've erased what windows would be on. :)

---

### Post by ammmom on 2007-05-09
> **ZeroWing said:**
> It's just a fancy way of saying that you've erased what windows would be on. :)
Thanks for the translation.  Is data gone, gone or are there any search and recovery programs to get it back?

---

### Post by Campingman on 2007-05-09
When installing Ubuntu you are given options on the particular method of partitioning of your hard drive.  You can make room for Ubuntu and leave Windows on or another option would be to format the whole drive and install Ubuntu, there is also a custom option which will open Gparted and you can manually adjust the partition.  Which one did you select?

---

### Post by Acglaphotis on 2007-05-09
He has 2 swap partitions so i think he selected manual.

-Acgla

---

### Post by alienexplorers on 2007-05-09
Your Windows stuff is gone.  Your choice now is to reinstall Windows.  This will mean setting up a NTFS/FAT32 partition from on of your ext3 partitions.  You will then have to reload grub to allow for dual booting since Windows will overwrite the MBR.

---

### Post by hyper_ch on 2007-05-09
Well, the windows data is gone... I don't think there is any chance to get it back except paying very, very, much to highly specialized labs that can recover it...

If you are unsure what to do now and need immediate feedback, then use IRC.

You should already have an irc client installed.

Connect to the Ubuntu IRC Server ( irc.ubuntu.com or irc.freenode.org [both the same]) and then join the channel  #xubuntu

Highlight me by typing my name in there.

---

### Post by ammmom on 2007-05-09
> **hyper_ch said:**
> Well, the windows data is gone... I don't think there is any chance to get it back except paying very, very, much to highly specialized labs that can recover it...

If you are unsure what to do now and need immediate feedback, then use IRC.

You should already have an irc client installed.

Connect to the Ubuntu IRC Server ( irc.ubuntu.com or [both the same]) and then join the channel  #xubuntu

Highlight me by typing my name in there.
I'm feeling stupider, by the second.  I went to aplications -> internet and I didn't see any connections for IRC.  To be honest, I don't know what IRC is or how to get to it.  When I type in irc.freenode.org I get forwarded to the "it works" page.

Can you tell me where I would find IRC on my comp or let me know where I can get it from?

I *had* some of my kids pictures that weren't backed up.  Would it be best to buy a new hard drive? Then in 10-20 years when (hopefully) the price comes down on recovery, from the super duper labs, I can try to recover then?

TIA...........

---

### Post by hyper_ch on 2007-05-09
well, gnome is a protocol like HTTP or EMAIL or FTP or ....

The default gnome irc client should be "Xchat". If you are using Ubuntu then check the internet folder if you have Xchat.

In Kubuntu it's "Konversation"

If you haven't got any, install them through Add/Remove Software :)

well, you can wait 10-20 years for prices to come down :)

---

### Post by ammmom on 2007-05-09
> **hyper_ch said:**
> well, gnome is a protocol like HTTP or EMAIL or FTP or ....

The default gnome irc client should be "Xchat". If you are using Ubuntu then check the internet folder if you have Xchat.

In Kubuntu it's "Konversation"

If you haven't got any, install them through Add/Remove Software :)

well, you can wait 10-20 years for prices to come down :)

Thanks, I got it through add/remove software. 

Do you  know of an Ubuntu dictionary.  I feel like I'm learning another language, that has no similarities that I know?

Do you agree that the best thing to do is buy another hard drive and re-install.  Hopefully, I won't have to wait 10-20 years, just long enough for my boys to become hacks.................

---

