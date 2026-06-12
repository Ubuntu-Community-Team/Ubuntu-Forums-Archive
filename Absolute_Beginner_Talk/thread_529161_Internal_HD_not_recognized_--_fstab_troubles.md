---
title: "Internal HD not recognized -- fstab troubles"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-08-18
my internal ntfs drive cannot be recognized.  I cannot manually mount it and if I try to boot to it I get an error 13.


 if I # comment out two lines in fstab the external flash loads .

sudo fdisk 
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7944    63810148+  83  Linux
/dev/sdb2            7945        9768    14651280   83  Linux
/dev/sdb3            9769       10011     1951897+  82  Linux swap / Solaris

Disk /dev/sdd: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)

Disk /dev/sdc: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         232     1863508+   b  W95 FAT32
/dev/sdc2             233         250      144585    5  Extended
/dev/sdc5             233         250      144553+  82  Linux swap / Solaris
kooz@kooz-laptop:~$ 


```


fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3a79ad82-eb61-4d85-a3b3-08b8e5396b4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=eeb84bb0-7e4e-463a-8ad3-916bf67774c1 /home           ext3    defaults        0       2
# /dev/hda1
#/dev/hda1 /media/i80  ntfs    nls=utf8,umask=0222 0       1
# /dev/sda3
UUID=087fa5ff-dd64-478e-9343-257b9765c2f8 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

#/dev/sdc1 /media/e2 vfat iocharset=utf8,umask=000 0 0
```


The main problem is 
#/dev/hda1 /media/i80  ntfs    nls=utf8,umask=0222 0       1

Also, unless

#/dev/sdc1 /media/e2 vfat iocharset=utf8,umask=000 0 0[/CODE] 

is the way it is -- commented out, it says "You are not privileged to mount this volume" whenever I insert the flash.  Again, with the above commented out, the flash works, though.

---

### Post by oilchangeguy on 2007-08-18
don't create two threads on the same subject:
[http://ubuntuforums.org/showthread.php?t=527918](http://ubuntuforums.org/showthread.php?t=527918)

---

### Post by johntkucz on 2007-08-18
no one responded to the other one.  if a thread is dead, it's perfectly fine to start a new one especially when it's a serious issue.

---

### Post by johntkucz on 2007-08-18
> **oilchangeguy said:**
> don't create two threads on the same subject:
[http://ubuntuforums.org/showthread.php?t=527918](http://ubuntuforums.org/showthread.php?t=527918)


instead of trying to exert your control over the forum etiquette, why don't you try actually helping me out?!

---

### Post by oilchangeguy on 2007-08-18
and you're answering my post twice, because? there were answers in your other thread, so how was it dead? and how will this thread be any different?

---

### Post by johntkucz on 2007-08-18
you need to spend less of your time monitoring the behavior of of others and more time actually providing some help!

---

### Post by johntkucz on 2007-08-18
no one's responded in a day to the other thread except me!:mad: I post here, atleast I get a response.

---

### Post by oilchangeguy on 2007-08-18
yes, ma'am.

---

### Post by johntkucz on 2007-08-18
that's sir, you ****.  I don't like you oilchange, you're a conceited idiot.  You think you're the "big brother" of the forum trying to control everything.  You already tried to exert your idiotic "so-called advice" in another of my threads:
[http://ubuntuforums.org/showthread.php?t=513305](http://ubuntuforums.org/showthread.php?t=513305).

You're loser. stay off my threads; you don't contribute anything other than frustration.  you're pathetic troll, too.

---

### Post by oilchangeguy on 2007-08-18
ah, yes. i remember you. you really have no business even owning a computer.

---

### Post by johntkucz on 2007-08-18
I've read your other posts on the board.  All of them treat people like idiots.  In reality, you apparently don't seem to know anything.

> now that's a new term i've not heard before. zero the disk. what do you mean?????? if the user actually knows what they are doing. and correctly deletes the partitions already on the drive. then there should be no problems in installing xp.

All your posts have the same ridiculous tone: "it Should work if you weren't an idiot...".  but you, my little pathetic forum friend, are the idiot.

---

### Post by oilchangeguy on 2007-08-18
> **johntkucz said:**
> I've read your other posts on the board.  All of them treat people like idiots.  In reality, you apparently don't seem to know anything.



All your posts have the same ridiculous tone: "it Should work if you weren't an idiot...".  but you, my little pathetic forum friend, are the idiot.

you have fun little boy, run along now and play. and to quote ron white, you can't fix stupid.

---

### Post by oilchangeguy on 2007-08-18
and you have the balls to talk about me. i just found this from one of your threads:

 Who thinks GNUcash rocks

I seriously LOVE This program.[COLOR="Yellow"] I know some idiots [/COLOR]who didn't switch to linux/ubuntu because of lack of a "quickbooks" equivalent. Gnucash is far superior! I love having an open source financial managament program because financial management is all about "tweaking exactly every detail" of financial input and output, so why not have access to the program that does that's input and output. Anyways, like most ubuntu/linux open source stuff I constantly feel astounded at its simplicity, lucidity, and advanced features.

---

### Post by johntkucz on 2007-08-18
STrangely,

Whenever I pull the command 
sudo gedit /etc/fstab

the command terminal spews this:

```
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
kooz@kooz-laptop:~$ 


```

---

