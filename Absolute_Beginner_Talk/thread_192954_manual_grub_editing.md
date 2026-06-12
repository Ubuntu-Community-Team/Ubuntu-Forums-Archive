---
title: "manual grub editing ???"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by sotonin on 2006-06-09
ok here's my problem. i have windows xp on another hardrive in my machine. I want to dual boot to it. but here's the kicker, i couldnt let grub auto detect it during install. i had to physically unplug the drive during the install. (i tried 3 times with it plugged in.) after the ubuntu install EVERY time it would give me an error about incorrect os or bad install or something bizarre. 

so at this point i have a machine running latest dapper install great. with one of my drives accessible for read (ntfs) and the other drive (with windows) sitting in there doing nothing.

I tried to manually add an entry in grub. but i dont know what exactly i need to add. and how do i figure out what its position is.... like hd(0,0) etc ??? 

oh maybe i should mention ... ubuntu was installed on a sata drive. so the grub is too i assume. the other 2 drives in my machine are IDE. one has the OS and another is data storage. i dont know if any of that matters. just trying to provide as much info as i can.

right now i added this to the end of my /boot/grub/menu.lst

title        	Microsoft Windows XP Professional
root        	(hd2,0)
savedefault
makeactive
chainloader    +1

i tried hd1,0 and hd2,0 since all my other entrieds use hd0,0

anyways neither worked. said unrecognized filesystem upon loading and just hangs.


thanks, i appreciate any help i can get!

---

### Post by Luke771 on 2006-06-09
Is your Grub installed in the Master Boot Record of the first drive?
(it should be, no matter which is the linux drive)

If you have the two OSes on two drives (hda, hdb) you need to install Grub in the MBR or it won't work properly.
I don't know if it's supposed to be that way, I just know that I wanted to insatll Grub somewhere else than the MBR so I could skip running Win install CD in rescue mode to restore MBR in case I wanted to uninstall Linux, so I installed Wion first on the master drive, then Linux on the slave drive, and Grub in 1,0 (first partition of the second drive, the linux partition)
Didn't work.
I had to run the Ubuntu install in rescue mode (type "rescue" at boot prompt and hit enter) and use the command grub-install (I dont rememer the whole command, you should check better, the exact line must be in these forums)
That re-installed Grub in the MBR and then everything worked fine.
.

---

### Post by sotonin on 2006-06-09
"first drive" lol. yeah this doesnt make sense to me. theres not really an order ... uh.. they're just in there :) 2 IDE and 1 SATA.

anyways my grub works fine. i can pick from all the flavors of linux i want. i just dont know how to manually configure it to load the IDE drive instead of the ubuntu drive

---

### Post by sotonin on 2006-06-09
nobody has ANY idea how to somehow list the drives actual locations??

hd0,1 hd0,2 etc ? i tried settings > disks but it shows its name not its location

---

### Post by catlett on 2006-06-09
Post the output of this ```
sudo fdisk -l
``` A regular grub entry won't do. Windows has to be tricked intoi thinking it is the first partition of the first drive.
I'll pull up the proper grub entry with the mapping but in the meantime post that output so we know where windows is.

---

### Post by catlett on 2006-06-09
In case I miss your post later, here is the basic idea. I'm going to assume windows is on (hd2,0). Sudo fdisk -l will let you know where it is.
```
title           Windows
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
``` Hopefully this works. It definately works when grub is on a slave to ubuntu's master. In that case using this always works 
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
``` Good luck

---

### Post by sotonin on 2006-06-09
hmm ok. im still confused. here this is what the output i get is...

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    7  HPFS/NTFS


SDA (the sata ubuntu drive, grubs loaded on this).

the hda1 is the windows drive and hdb1 is my ntfs data storage drive (i plan to eliminate but need it for the time being until i can transfer stuff off)

thanks for the assistance i really appreciate it!

---

### Post by confused57 on 2006-06-09
What is the output of?:

```
cat /etc/fstab
```

I'm not sure if this will help us any or not.  Catlett's given you some great things to try, but SATA drives are a little difficult to configure.

---

### Post by sotonin on 2006-06-10
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /mnt/ntfs1      ntfs ro,nls=utf8,umask=0222 0 0

i dont have the windows drive mounted in linux cause i dont have any need to read or browse the drive it only contains windows, nothing i need to grab from inside linux. i dont know if that matters or not.

---

### Post by confused57 on 2006-06-10
[QUOTE=catlett]In case I miss your post later, here is the basic idea. 
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
``` [/QUOTE]

This entry in your grub looks like the one that would work, you could try "rootnoverify" in the place of "root"...Hopefully, someone experienced with SATA drives and grub can help...I only have IDE drives.  I assume your system is set to boot first from the SATA drive with all drives connected.  Good luck... wish I could help you more.

---

### Post by sotonin on 2006-06-10
that exact entry worked fine! thank you so much everybody who attempted to help me out. Windows XP on my IDE is dual bootable now :)

---

### Post by confused57 on 2006-06-10
[QUOTE=sotonin]that exact entry worked fine! thank you so much everybody who attempted to help me out. Windows XP on my IDE is dual bootable now :)[/QUOTE]

Great, I'm glad it worked out...mostly thanks to catlett, who gave the suggestion originally.   Thanks for letting us know, it's good to hear a success story.

---

