---
title: "[SOLVED] A ton of problems!!!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Beatbreaker on 2007-06-28
hey guys, 

everything on my system was working sweet lastnight (well apart from Amarok) and now nothing is working properley - totem crashes, Amrok crashes (the splash screen starts and that's it), VLC crashes, the sound only works sometimes, - what's gone on??

i'm supposed to spend tonight fixing fireworks and dreamweaver to work with wine but i've spent all this time wasted on getting things that did work to work again. 

Should i try the obvious solution and reinstall these programs?

basically the only things that don't crash are firefox and thunderbird. - even trying to enpty my recycle bin is crashing. just before i couldn't get and right click menus to work either - id right click, a menu would come up (for eg: on a panel) but then it wouldn't work - and then clicking on anything in a panel wouldn't work - if i tried to log off those buttons didn't work again

is my gnome stuffed? what's going on?

---

### Post by louieb on 2007-06-28
With that many applications going wrong at the same  time. 1st find out hardware or software.  Run the memtest program. and boot to a live CD and run fsck on your Linux partitions.

---

### Post by Beatbreaker on 2007-06-28
ok i tried this:


> memtest all

and it spewed out some info then crepped itself

should i use memtest differently?

---

### Post by Beatbreaker on 2007-06-28
i tried to enpty the recycle bin again and the pop up confirmation window crashed just cos of that - i tried to get a screenshot but then that didn't respond and i couldnt use the any buttons at all after that

---

### Post by CheeseEatingBulldog on 2007-06-28
If you have multiple Ram modules that are big enough on their own to run ubuntu, take one out and try booting again. I have had erratic behaviour in the past due to faulty memory and a failing hard disk.

---

### Post by eljalill on 2007-06-28
Probably it would be good to boot from a live CD and then do a check on the file system (fsck) and such.. 
You might also want to look at the swap partition then.

---

### Post by Beatbreaker on 2007-06-28
> **eljalill said:**
> Probably it would be good to boot from a live CD and then do a check on the file system (fsck) and such.. 
You might also want to look at the swap partition then.

ok i'll use the CD and try fsck with the live CD

I've just reinstalled metacity so i'll try that first.  I've been reading this and i'm hoping that it's the same thing

[http://ubuntuforums.org/showthread.php?t=483128](http://ubuntuforums.org/showthread.php?t=483128)

---

### Post by ^rooker on 2007-06-28
I agree: If so many programs fail at once it's good to check your hardware first.

**- Memtest:**
Boot from a live CD (e.g. Ubuntu installation CD, Knoppix, Phlak, etc... ) - They usually have "memtest" as one of their boot options. Do not run it while your system's booted. 

If an errorneous RAM module is found, take all of them out and test them 1 by 1.

**- Check for overheat:**
Check if all the fans in your system are running properly (Especially graphic card fans like to cause behavior like this).

**- Check your harddrive(s):**
Boot a live CD and run fsck (as already suggested by eljalill above).

**- Check if it's related to your installation:**
Boot a live CD and check if that's running stable. 


Good luck.

---

### Post by Beatbreaker on 2007-06-28
> **^rooker said:**
> I agree: If so many programs fail at once it's good to check your hardware first.

**- Memtest:**
Boot from a live CD (e.g. Ubuntu installation CD, Knoppix, Phlak, etc... ) - They usually have "memtest" as one of their boot options. Do not run it while your system's booted. 

If an errorneous RAM module is found, take all of them out and test them 1 by 1.

**- Check for overheat:**
Check if all the fans in your system are running properly (Especially graphic card fans like to cause behavior like this).

**- Check your harddrive(s):**
Boot a live CD and run fsck (as already suggested by eljalill above).

**- Check if it's related to your installation:**
Boot a live CD and check if that's running stable. 


Good luck.


thanks this looks really helpful - I've done memtest86 from the boot CD - i checked it for 7.5 hours last night and did not get a single error.

i'll check for overheat after i boot from the live CD and check fsck

...how do i run fsck though? just from the terminal type "fsck"?

it's a real shame because everything was working perfectly then all of a sudden it's throwing errors everywhere. I guess if i have to do a reinstall i might try Kubuntu out instead.

---

### Post by Beatbreaker on 2007-06-29
ok quick update:

i've checked how everything funcitons on the live CD and it's all good, i didn't get any freezes or anything at all.

i'll try fsck after i do some more testing on my installed ver now - i just received some autuo updates that will hopefully resolve the issues.

---

### Post by Beatbreaker on 2007-06-29
...ok i tried fsck from the live CD (i've got 5 hard drives so this may take a while) and i got the following errors

> ubuntu@ubuntu:~$ fsck /dev/sdc
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Permission denied while trying to open /dev/sdc
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ fsck /dev/sdc1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Permission denied while trying to open /dev/sdc1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ gksudo fsck /dev/sda1
fsck 1.40-WIP (14-Nov-2006)
fsck: Error 2 while executing fsck.ntfs for /dev/sda1


---

### Post by Beatbreaker on 2007-06-29
ok now i tried to boot in Ubuntu safe mode from grub... i got this (this is not exactly what came up, but more of a brief version

> devide SDC2 is_boot_sector_NTFS: invalid boot sector checksum
...primary boot sector is inbvalid
mount option errors= recover is not used - aborting without tring to recover
not an NTFS volume

mount: wrong fs type, bad option. bad super block on missing code page or other error (arent you trying to mount an external partition, instead of some logical partition inside?)
in some cases useful info is found in syslog - try dmesg | tail or so


ok i didn't edit fstab properley... i've edited it back to it's .bak file backup (thank god i backed up) but it's still playing up

i went into recovery mode again and not a new wrror

> activating swap file swap [fail]

what's going on?

---

### Post by MenZa on 2007-06-29
Right, what you want to do is boot the LiveCD, then open a terminal and run:

```
sudo fdisk -l
```

This should give you some output similar to this:

```

[13:19:02] menza@alderaan - ~ $ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156   af  Unknown
/dev/sda2            6376       29644   186908242+  83  Linux
/dev/sda3           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

```

Now, on this drive here, you can tell that my ext3 partition (marked as 'Linux') is /dev/sda2. fsck will only check ext2 and ext3 devices, as far as I know.

So in the same terminal I type:

```
sudo fsck /dev/sda2
```

Wait a few moments and fsck should check your disk and fix any errors that might pop up.

**Edit:** I was a bit slow here. The error you're having with your swap appears to suggest you've broken your swap partition. I'm not entirely sure fsck will check/fix swap, but on that same live cd, I suggest you run fsck on your swap as well (it'll tell you if it can't do that). Find the *Linux swap/Solaris*-entry in *sudo fdisk -l* and run:

```
sudo fsck /dev/device
```

Substituting 'device' for device name.

---

### Post by Beatbreaker on 2007-06-29
My sudo fdisk -l

> Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   42  SFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      620181   312571192+  42  SFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9352    75119908+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321   42  SFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650       36480   231585007+   f  W95 Ext'd (LBA)
/dev/sdc5            7650       36480   231584976    7  HPFS/NTFS


when i tried i got this

> fsck 1.40-WIP (14-Nov-2006)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/hdc5


---

### Post by Beatbreaker on 2007-06-29
i also tried the following and got this...

> ubuntu@ubuntu:~$ sudo fsck /dev/hdc1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hdc1: clean, 146905/9404416 files, 1815852/18779977 blocks


---

### Post by Beatbreaker on 2007-06-29
sorry guys i couldn't figure it out, i figure that i never thought that this instillation would work anyway since it's my first time using Ubuntu I achieved a lot, i installed it, got HDD's to auto mount, got the Intel mouse to work, printer working, grub working, and beryl working (along with heaps of other stuff)

i consider that an achievement in it's self. I'm now installing Kubuntu instead over the Ubuntu instillation hopefully this will fix the problems and onto bigger and better things!

---

