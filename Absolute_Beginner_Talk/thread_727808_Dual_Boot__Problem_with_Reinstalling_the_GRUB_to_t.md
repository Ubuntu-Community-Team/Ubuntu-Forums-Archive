---
title: "Dual Boot / Problem with Reinstalling the GRUB to the MBR"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by LisaDusk on 2008-03-18
Hi!
I started using Ubuntu 7.04 on my Laptop a while ago (without really knowing that much about it, I went to a one-week course about Linux in general).
So, now I tried to install a Dual Boot with Ubuntu and Windows XP using this guide: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

My problem lies with "Reinstall GRUB to the MBR":
"find /boot/grub/stage1" returned "(hd0,1)" instead of the expected (hd0,0) . For some reason the windows partition is /dev/hda1 and the ubuntu partition is /dev/hda2 (reversed in the guide). I don't know how this happened, I thought I followed the instructions to the letter. 
So, anyway, I changed the Ubuntu partition to be the boot partition (via manage flags, as instructed), but after I enter root (hd0,0) and setup (hd0) I get the error "Error 17: Can't mount selected partition".
If I enter root (hd0,1) and then setup (hd0) I get the same error after I remove the CD and try to boot Ubuntu. 
Can anybody help me? I'm new to Linux/Ubuntu and this is probably an easily solvable error if I new what values to enter after root and setup ...

---

### Post by Berean on 2008-03-18
Hi, I'm new myself, but you may be successful if you use the install disk to reinstall GRUB, and then boot normally from the hard drive install.  I seem to remember posting on a thread that had a similar GRUB error and got thanked that it worked.  Hope this is of some help, but if not I'm sure someone with more experience and knowledge will soon post.  You may want to look up GRUB 17 error and see if that answers you query.  Good luck and God speed, LisaDusk.  Regards

---

### Post by wblancqu on 2008-03-18
So you first installed linux, then windows. As a consequence windows overwrited the MBR, so GRUB is "gone". You can indeed fix it by doing some more difficult stuff, but the most easy way I always use is making use of the Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Just burn the cd, boot your pc with that cd, and let it reinstall the MBR itself.

Grtz

---

### Post by Berean on 2008-03-18
wblancqu, does one have to make a separate disk, or is it included on the Ubuntu installation disk?  I'm obviously still learning myself and don't want to mislead anyone!  Regards.

---

### Post by wblancqu on 2008-03-18
Download the ISO file from here:

[http://forjamari.linex.org/frs/download.php/832/supergrubdisk_0.9677.iso]("http://forjamari.linex.org/frs/download.php/832/supergrubdisk_0.9677.iso")

Burn to a CD. Put CD into your computer. Reboot, and the Super Grub Disk will load. Eventually you will get a GRUB menu with various options. I don't know exactly the right option, but it should be something like "MBR-Linux-Windows (AUTO)".

This should restore the grub to the MBR which was installed before installing Ubuntu.

Feel free to ask if any more trouble (or say thanks if it works ;))

Good luck!

---

### Post by cj2003 on 2008-03-18
Another guide is [How to fix your Windows MBR with an Ubuntu liveCD]("http://ubuntu-news.net/modules/news/article.php?storyid=3894"), but I think it better to go with wblancqu's advice.

---

### Post by Berean on 2008-03-18
cj2003, I think I might have given the correct advice but didn't expand upon it!  Thanks for your clarification.  Regards.

---

### Post by LisaDusk on 2008-03-18
> **wblancqu said:**
> Download the ISO file from here:

[http://forjamari.linex.org/frs/download.php/832/supergrubdisk_0.9677.iso]("http://forjamari.linex.org/frs/download.php/832/supergrubdisk_0.9677.iso")

Burn to a CD. Put CD into your computer. Reboot, and the Super Grub Disk will load. Eventually you will get a GRUB menu with various options. I don't know exactly the right option, but it should be something like "MBR-Linux-Windows (AUTO)".
This should restore the grub to the MBR which was installed before installing Ubuntu.
Feel free to ask if any more trouble (or say thanks if it works ;))
Good luck!

Thanks a lot for the really fast help everybody! 
I'm gonna try using the Super Grub Disk. Will this just solve the "Reinstall GRUB to the MBR"- issue or will it create a system in which I can decide which OS to boot every time I start the Laptop (the final stage I'd like the Laptop to be in). In other words, do I have to continue with the other steps from the guide at [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) or not?

---

### Post by wblancqu on 2008-03-18
If it only let you boot into linux upon reinstalling, you should alter the /boot/grub/menu.lst file and append something like:

```
title Microsoft Windows
rootnoverify (hd0,0)
makeactive
chainloader  +1
```

Grtz

---

### Post by LisaDusk on 2008-03-18
The options are

Grub > MBR & !LINUX! (1)      AUTO
Grub > MBR & !LINUX! (>=2) MANUAL
!LINUX! (1)          AUTO
!LINUX! (>=2)     MANUAL
!WIN!
WIN > MBR & !WIN!
EASY LIVE SWAP

I tried "Grub > MBR & !LINUX! (1)      AUTO" and it tries to boot the Ubuntu kernel 2.6.20-16-generic and gives the same error message as before "Error 17: Cannot mount selected partition", I get into a menu where I can choose between different kernels and recovery modes, but they all give the same Error 17. :(

---

### Post by LisaDusk on 2008-03-18
I went through all the steps to restore the Grub mentioned here ( [http://supergrub.forjamari.linex.org/?section=documentation#quick_guide](http://supergrub.forjamari.linex.org/?section=documentation#quick_guide) )
I get the "SGD has succeeded" message, but when I enter "Quit" and start the system without the CD, I get the same message as before "Error 17: Cannot mount selected partition", so I guess I didn't fix the Grub.

---

### Post by wblancqu on 2008-03-18
I remember I had this problem also. Although now you're MBR should be fixed. To fix the cannot mount partition problem, you should play with the parameters in the /boot/grub/menu.lst file. Probably GRUB didn't detect your HD's well, and assigned some wrong parameters in his config. When in GRUB menu, press 'e' and try editing the root (hd0,0) to something like root (hd0,1), just play with it. Once you stop receiving the error, it is possible the second line is also wrong. try changing the "root=UUID=..." to "root=/dev/hda2" or wherever your linux boot partition is.

Once you got it working, make the changes permanent by editing the /boot/grub/menu.lst file.

Grtz

---

### Post by Duck2006 on 2008-03-18
From the live ubuntu cd in the terminal type

sudo fdisk -l

and post the output.

---

### Post by LisaDusk on 2008-03-18
> **Duck2006 said:**
> From the live ubuntu cd in the terminal type

sudo fdisk -l

and post the output.

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes 
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         960     7711168+   7  HPFS/NTFS
/dev/hda2   *         961        4707    30097777+  83  Linux
/dev/hda3            4708        4870     1309297+   5  Extended
/dev/hda5            4708        4870     1309266   82  Linux swap / Solaris 
Disk /dev/sda: 493 MB, 493879296 bytes
16 heads, 32 sectors/track, 1884 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1884      482288    e  W95 FAT16 (LBA) 

Well, I hope this helps you solve my problem, because it doesn't really tell me anything. :confused:

> play with the parameters in the /boot/grub/menu.lst file. Probably GRUB didn't detect your HD's well, and assigned some wrong parameters in his config. When in GRUB menu, press 'e' and try editing the root (hd0,0) to something like root (hd0,1), just play with it. Once you stop receiving the error, it is possible the second line is also wrong. try changing the "root=UUID=..." to "root=/dev/hda2" or wherever your linux boot partition is.

Once you got it working, make the changes permanent by editing the /boot/grub/menu.lst file.

I'm afraid you'll have to dumb this down for me. How do I change the parameters of that file? How do I get into the GRUB menu? I'm a little confused here.

---

### Post by Duck2006 on 2008-03-18
> find /boot/grub/stage1" returned "(hd0,1)" instead of the expected (hd0,0)

The find command returned the write partition, your linux / partition is (hd0,1)
You can read up on grub on this page.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

or you can use this supergrub disk to set up grub..

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by LisaDusk on 2008-03-19
> **Duck2006 said:**
> or you can use this supergrub disk to set up grub..

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Well, as I said before, it gave the "SGD has succeeded" message, but produced the same error as before upon reboot without the CD. 

> The find command returned the write partition, your linux / partition is (hd0,1)
You can read up on grub on this page.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) 

I'm afraid that's a little over my head. I don't think I'll have the time to work out the GRUB syntax (I'm currently writing my M.A. thesis). I thought it'd be an easily solvable problem and somebody just had to tell me the right values to enter for the "root" and "setup" commands in the grub menu, but since it's apparently a much more difficult problem, I think I'll just format and install only Windows (I need a statistics program for my thesis which only runs under Windows, otherwise I'd just have kept Ubuntu in the first place).

Thanks for all your suggestions, but I'm afraid they're a little ahead of my current Linux skills.

---

