---
title: "Forced fsck on Dual Boot System"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by kevmartin on 2007-03-02
Hello all - my first post :-)

My third look at Linux over the years and this time I think I am impressed enough with Ubuntu I will be making it my major OS of choice.  Unfortunately I can't ditch XP completely as I need it to both test drive web pages created for clients, which have to work for everyone, and because the 3D software options are looking a bit slim on Linux (Poser, Vue, Bryce, etc .. where are you? :-) )

But I digress.

I have the system set up and working as a dual boot arrangement.  But boots to linux are horrendously slow (20-30 minutes) unless I unplug my external USB HDD, in which case, that brings it down to an acceptable 3-4 minutes.

The reason for this seems to be the system insists on running fsck on all partitions before booting.  I checked with the server techs at work and they said - delete the file forcefsck from / - but unfortunately that file doesn't exist, so something else must be causing this.

Can anyone suggest how to stop this forced fsck from happening?

For the record, the system is very young and plenty of grunt I think:
Dell 9150 Dimension with Dual Core Pentium D 3 GHz and 3 Gb RAM, 250 Gb internal HDD plus the 80 Gb external one.

Thanks in advance.

---

### Post by kevmartin on 2007-03-02
I kept searching in the forums and found quite a few others have had similar problems - but no clear solutions.  Some mentioned using tune2fs to force the system to only check a drive every x number of reboots.  SO I thought I would give that a go.

Firstly, the external drive that takes so long to scan was unplugged so as to avoid taking 30 minutes to reboot.

When I got booted up, I went to text mode, and ran:

tune 2fs -c 30 /dev/sda2

This what I got as a response:

tune2fs: Bad magic number in super-block while trying to open /dev/sda2
Couldn't find valid filesystem superblock

It occurred to me this might be because the drive was unplugged.  SO I plugged it back in and got a further error and the text mode window hung.

I was still able to switch back to graphics mode though, so I did that and came back here to report.

I guess I could go without the external HDD as I rarely use it anyway, but still - it's the principle isn't it? :rolleyes:

If I do go that route, what should I do to tell Linux that drive no longer exists? Do I need to run the partitioner software or something?

Thanks.

---

### Post by mcduck on 2007-03-02
What files system your drives are?

Could you run 'sudo fdisk -l' and 'cat /etc/fstab', and post the output of those commands here? :)

(Btw, tune2fs only works for Ext2/Ext3 file systems. You can't use it if your drive is FAT or NTFS or some other type..)

---

### Post by kevmartin on 2007-03-02
Thanks for your input McDuck :)

Sure thing - I knew there would be some pertinent info  I could post - just had no idea what it was.  What you said certainly explains the error from tune2fs as the file system on the external drive is (IU think) VFAT.

There's 2 partitions used up by the Dell system restore system, a main partition on the main hard disk for Windows, a FAT32 partition I made for shared data, and a 128Mb Flash drive also in the mix.

Here's the output of the commands (looks like the external HDD isnt showing on the fdisk list, but is on the fstab as /sdb1):
fdisk:
```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       16702   134110620    7  HPFS/NTFS
/dev/sda3           29788       30393     4867695   db  CP/M / CTOS / ...
/dev/sda4           16703       29787   105105262+   f  W95 Ext'd (LBA)
/dev/sda5           16703       25830    73320628+   b  W95 FAT32
/dev/sda6           25831       25894      514048+  82  Linux swap / Solaris
/dev/sda7           25895       29787    31270491   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 132 MB, 132251648 bytes
8 heads, 32 sectors/track, 1009 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1009      129136    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 7, 32) logical=(1008, 7, 32)

```

fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdc1       /media/sdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Please just let me know if I can provide anythign else useful.

Thanks again
Kev
(going to bed now - getting late here in Australia)

---

### Post by mcduck on 2007-03-02
Ok, the first thing you should try is to edit your fstab so it looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
To open the file for editing run 'gksudo gedit /etc/fstab' (in Gnome & XFCE4) or 'kdesu kate /etc/fstab' (in KDE).

This should disable fsck for all your FAT/NTFS paritions on the internal hard disk. I also removed entries for your external drives, as they should be mounted automatically anyway.

If the external drives don't work correctly this way then post here and I'll help you to make new entires for them using UUID numbers instead of the old /dev/xxxx-style (which doesn't really work for removable drives as their device number can change depending on in which order they are recognized).

---

### Post by kevmartin on 2007-03-02
Wonderful!  From the time of my last post until 5 minutes ago I was rebooting with the extrnal HDD plugged in - thats how long it was taking.  I then came back to post a full list from fdisk in case you needed it.

Meanwhile you had provided a great solution .  I made the change to fstab, rebooted in about ... hmmmm ... 75 seconds I would say.  Removable drives seem to be responding fine - I can read and write to them.

I am forever in your debt McDuck - Thanks again!

I have a big learning curve ahead but I believe it will be an enjoyable one.

Kev

---

### Post by mcduck on 2007-03-02
Hey, no problem. Great that it worked.

Anyway, the best way to learn is to read these forums, and help other people when you can. It's amazing how much you can learn new things that way :)

---

### Post by renaud.denis on 2007-03-04
Thanks for me too :)

---

### Post by jvc26 on 2007-03-04
I'm shocked your boot times are so slow! I tend to be gutted beyond about 9 seconds! I'm surprised you're still in the 75s bracket and your pc is much more pumped up than mine. Ah well, at least its now much more acceptable!
Il

---

### Post by kevmartin on 2007-03-04
Well I haven't timed it or anything - it may be less than that.- I'll try to remember to time it some time (could be tricky since I don't wear a watch lol ).  Also, I'm not sure what people refer to with the boot times, as in from when to when - I was referring to fromtelling the system to reboot, to reaching the ubuntu login prompt.  Just the shutting down part seems to take maybe 20 seconds.  But anyway, anything that takes down in the range of 1 minute seems just fine to me - I've never seen a computer do much better than that.

---

### Post by kevmartin on 2007-03-04
OK you got me curious with talk of 9 second boot times :-)

I rebooted and counted (couldnt be bothered digging up a watch to time accurately.  I closed all windows on the machine first. Then this is what I saw:

[LIST]
[*]14 seconds to shut down (to reach the final "rebooting now" message on screen)
[*]11 seconds in BIOS screen etc
[*]1 second at grub prompt while I hit Enter
[*]40 seconds in Ubuntu graphic login process.
[/LIST]

So, total of 66 seconds from telling system to restart to get back to the 'enter your login' screen. I think I can live with that :-)

---

