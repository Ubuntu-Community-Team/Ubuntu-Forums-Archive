---
title: "Help, windows no longer boots!"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by shaner12 on 2007-05-01
Hello, I'm just going to say right off that I'm very new at Linux. To begin with, I installed Dapper Drake on my SATA hard drive a while back, while i had a windows install on my IDE hard drive. Everything worked well, and I was able to boot both operating systems.  I decided to switch the installs so i could have more room for games on my windows install. I reformatted both and installed windows on the SATA, and it has been running fine. I just got around to reinstalling ubuntu on the smaller IDE drive, and now windows no longer shows up on the boot list, and I have no idea on how to get it to show back up again. Ubuntu recognizes the hard drive, and shows that it isn't empty, but I would like to be able to boot either one, and I can no longer use windows. Help me please!

---

### Post by starcraft.man on 2007-05-01
I think, you may need something a bit more than grub. I personally haven't used this but friends who have say it works well. [Here.]("http://gag.sourceforge.net/") Boot it up and then it should detect both your OS and then generate a bootloader for both and install it to the MBR. Hope that helps. Read the documentation first just to be sure you do it right.

---

### Post by shaner12 on 2007-05-03
I guess I just don't understand linux. I followed the instructions perfectly and it won't even let me install the thing.  I just keeps saying " sudo: gag-install: command not found"

---

### Post by Billy McCann on 2007-05-03
shaner12,

Post the output of these two commands for us.  

Either copy-paste or type these into the terminal.  (Applications > Accessories > Terminal)

```
cat /boot/grub/menu.lst
```

```
sudo fdisk -l
```

Note: Those are both "ell's" (not one's) in those code boxes.  Just copy and paste if you aren't sure.  :)

---

### Post by shaner12 on 2007-05-03
The /dev/sda is the one that won't show up on the boot list, can't figure it out for the life of me

title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro quiet sp lash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19366   155557363+   7  HPFS/NTFS
/dev/sda2           19367       20023     5277352+   5  Extended
/dev/sda5           19367       20023     5277321   82  Linux swap / Solaris

Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3582    28772383+  83  Linux
/dev/hda2            3583        3738     1253070    5  Extended
/dev/hda5            3583        3738     1253038+  82  Linux swap / Solaris

---

### Post by joramdam on 2007-05-03
why do you want to boot windows ? (i have to with you)

---

### Post by shaner12 on 2007-05-03
world of warcraft! i know its a sad thing to say but its true. I like linux for its (free) office programs and the like. I realize i could probably run wow on wine, which i was planning on trying, but if i lose my windows install in the process i may become very angry and have to swear off linux forever :(

---

### Post by joramdam on 2007-05-03
Ok sorry for joking with you (sorry my english) . Put in your xp cd and boot with it ( i suppose you have notjing inportant in your home directory) Let the boot process wit your xp do the job for you. When you come to something like repair manualy (i think E option ) you select E) and you get a black screen. You  do this : first Write Fixboot, and answer yes and yes i really whant this. Then you write fixmbr and write yes. Afrer this you write exit, and you will boot only windows...But i really wonder why it went wrong with your dual boot ????

---

### Post by joramdam on 2007-05-03
Leave the XP cd in the pc after reboot !! and let the pc do the job...

---

### Post by joramdam on 2007-05-03
Next time you want a dual boot  i am sure it will be OK !!!! And you wil see you dont need Windows at all.................

---

### Post by shaner12 on 2007-05-03
I've actually already tried that. After I did the fixMBR command and rebooted, the grub loader came back up and told me it was unable to mount the partition.

---

### Post by Billy McCann on 2007-05-03
shaner12,

Try adding this to the bottom of your /boot/grub/menu.lst.

1. Code to put into the terminal to allow you to edit the file:
```
gksudo gedit /boot/grub/menu.lst
```

2. The text that you want to add to the file:
```
title=Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1
```

Be sure to report back if this helps or not.  Also, you know those little pins that are on the back of your hard disk drives that determine whether the drives are master or slave?  You know, I always just take those things off. Since you've swapped them around, that may be one of your problems. I don't know if it's the "recommended" thing to do, but it worksforme.   ;)


On another note, World of Warcraft is playable in Ubuntu.  The gamers around here chat about it all the time.  You may have some glitches with your own unique setup, but it seems that many folks around here are successful at playing WoW.  

Just do a search.  Or try some of these threads that my search pulled up.  


[http://ubuntuforums.org/showthread.php?t=312482&highlight=World+of+Warcraft](http://ubuntuforums.org/showthread.php?t=312482&highlight=World+of+Warcraft)

[http://ubuntuforums.org/showthread.php?t=425382&highlight=World+of+Warcraft](http://ubuntuforums.org/showthread.php?t=425382&highlight=World+of+Warcraft)

[http://ubuntuforums.org/showthread.php?t=428828&highlight=World+of+Warcraft](http://ubuntuforums.org/showthread.php?t=428828&highlight=World+of+Warcraft)

[http://ubuntuforums.org/showthread.php?t=416565&highlight=World+of+Warcraft](http://ubuntuforums.org/showthread.php?t=416565&highlight=World+of+Warcraft)

[http://ubuntuforums.org/showthread.php?t=28882&highlight=World+of+Warcraft](http://ubuntuforums.org/showthread.php?t=28882&highlight=World+of+Warcraft)

---

### Post by shaner12 on 2007-05-04
yeah, that method isn't working for me either. it just sits there saying loading... in the corner of the screen until eternity comes. I'm about to crack open my case and take off the jumpers and see what happens, but I doubt if thats what my issue is. Since one is SATA and one is IDE I dont think its an issue. I had a dual boot, with windows on the IDE and ubuntu on the SATA beforehand and it worked fine, without any switching of cables or whatnot. I've been trying to install WOW also haha. Its taking forever for burning crusade to dl though

---

### Post by shaner12 on 2007-05-04
oh and one more question, I've tried to find sound blaster audigy drivers, (so i can switch between 5.1 and headphones) but their website says they don't support linux on my card. Is there some workaround for this?

---

### Post by shaner12 on 2007-05-04
ok so i removed the jumpers and set my sata as my primary, it said invalid executable and refused to boot. it seems that grub has ingrained itself even in my windows hard drive. I have tried to the fixboot command, but that just makes my linux drive inaccessible, with the same outcome on my windows drive.

---

