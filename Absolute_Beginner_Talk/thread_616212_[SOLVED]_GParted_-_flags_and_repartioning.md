---
title: "[SOLVED] GParted - flags and repartioning"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by SFinn on 2007-11-18
I started off with a dual-boot XP and Ubuntu system. My comp was getting pretty filled with Windows files, so I only put 5GB for Ubuntu. Then I destroyed my Windows installation - about 30GB partition, at the front of the hard drive.

Now I want to make my computer an Ubuntu-only computer. I've installed gparted, but I'm not sure about how to use it.

My plans are to delete the windows partition and redistribute the space to the ubuntu partition and a new data partition.

The windows partition is flagged as 'boot'. The Ubuntu partition is not. Should I do something about this? Also, does it matter that the ubuntu partition is right at the end of the hard drive?

---

### Post by geirha on 2007-11-18
> **SFinn said:**
> The windows partition is flagged as 'boot'. The Ubuntu partition is not. Should I do something about this?

No, windows needs the boot flag, ubuntu doesn't.

> **SFinn said:**
> Also, does it matter that the ubuntu partition is right at the end of the hard drive?

Yes, it does matter. You can only resize to the "right". To resize to the "left" you need to move the whole partition to the "left" and then resize it to the "right", which takes a lot of time (probably hours, depending on the size). You shouldn't do this from ubuntu (which is running on that disk) I suggest you use the liveCD which has gparted installed, or download the gparted liveCD (only ~60MiB in size)

If you paste your /etc/fstab, and the output of ```
sudo fdisk -l
``` we might help you further.

---

### Post by SFinn on 2007-11-18
OK, thanks. Here goes:

/etc/fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c555da17-0dce-463e-9d96-5e72f5ebae77 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=24048D38048D0DCC /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=C08D-CC82  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=13C2FC0782F71939 /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=260add58-ece6-40c3-9cd7-9d60e1f39d9d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

sudo fdisk -l:
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e543336

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/sda2            4517        4864     2795310   1c  Hidden W95 FAT32 (LBA)
/dev/sda3            2806        4516    13743607+   f  W95 Ext'd (LBA)
/dev/sda5            2806        3315     4096543+  83  Linux
/dev/sda6            3316        3436      971901   82  Linux swap / Solaris
/dev/sda7            3437        4516     8675068+   7  HPFS/NTFS

Partition table entries are not in disk order
```


Also, what's the difference between using the gparted live cd and the gutsy live cd?

---

### Post by mike555 on 2007-11-18
If your getting rid of Windows , just back up your stuff and do a clean install ...... you can just tell it to use all of the harddrive , or do a manual partition if you want a separate  /home .........  this can be done from the live CD .

---

### Post by Pumalite on 2007-11-18
You might want to use Live Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Use it for the following scheme:
10 GB for '/'
2x RAM up to ! GB for /swap (except in laptop, where /swap=RAM)
The rest for /home.
Then install Ubuntu. Go Manual and use partitions already prepared.

---

### Post by glotz on 2007-11-18
The gparted live cd contains the latest version of the software. It's recommended.

---

### Post by geirha on 2007-11-18
> **SFinn said:**
> 
sudo fdisk -l:
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e543336

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/sda2            4517        4864     2795310   1c  Hidden W95 FAT32 (LBA)
/dev/sda3            2806        4516    13743607+   f  W95 Ext'd (LBA)
/dev/sda5            2806        3315     4096543+  83  Linux
/dev/sda6            3316        3436      971901   82  Linux swap / Solaris
/dev/sda7            3437        4516     8675068+   7  HPFS/NTFS

Partition table entries are not in disk order
```

What is the hidden fat32 partition sda2 for? 

Seeing as your linux-partition is inside an extended partition like this, I would recommend just leaving the linux partition as is. And then remove the big windows partition and create a linux partition in it's place, which you mount as your /home. You don't need much space for /, 10-15GB is more than enough in most cases, but /home is where you put all your files, so you need the most space there.

If you choose to do it like this, you would need to move the files you have in /home allready. You do this the first time you boot after altering the partitions. The following few commands should copy the current home-dirs to the new partition

```
sudo mount /dev/sda1 /mnt
sudo cp -a /home/* /mnt/

```

Next, you figure out what it's universally unique identifier is, by doing ```
ls -l /dev/disk/by-uuid | grep sda1
```

Use the uuid to make an entry in fstab: ```
UUID=<the_uuid> /home ext3 defaults 0 2
```

Reboot and check that everything is working.

---

### Post by SFinn on 2007-11-19
Hidden Fat32 partition: This came with the laptop so that I could boot to it and reinstall everything as it was right out of the box.

GParted liveCD: Ok, thanks. That looks the best way then. I'll download that now.

Just to confirm: my / partition would remain as is, is that right? Then I would shift /home to sda1? Does this mean that / would remain inside a logical partition?

Because of the suggestion to make sda1 = /home, I will add sda7 to sda1. sda7 was a makeshift /home partition, but putting the two together seems best. This will shift the Ubuntu / partition further back. Is this fine? Is there any problem about where Ubuntu is installed on the hard drive at all?

Thanks

---

### Post by Pumalite on 2007-11-19
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by geirha on 2007-11-20
> **SFinn said:**
> Hidden Fat32 partition: This came with the laptop so that I could boot to it and reinstall everything as it was right out of the box.

GParted liveCD: Ok, thanks. That looks the best way then. I'll download that now.

Just to confirm: my / partition would remain as is, is that right? Then I would shift /home to sda1? Does this mean that / would remain inside a logical partition?

Because of the suggestion to make sda1 = /home, I will add sda7 to sda1. sda7 was a makeshift /home partition, but putting the two together seems best. This will shift the Ubuntu / partition further back. Is this fine? Is there any problem about where Ubuntu is installed on the hard drive at all?

Thanks

The / partition can be anywhere on the partition. So what you want is to 
- remove the two NTFS partitions, 
- make a 30GB /home at the start
- in the extended partition keep a 4 GB / and a 1GB swap? 

I don't see any problem with that, other than that I think the / partition is a little bit small, I would go for a little bit larger one, like 10GB or so to be on the safe side. Alternatively, you could seperate it further, into / and /usr. (On my current Edgy installation, ubuntu is using 800MB of / and 5.2GB of /usr. I've installed a lot of stuff I never really use though :) )

---

### Post by SFinn on 2007-11-21
OK, I'll make the / partition 10 GB then. That sounds a good idea. I'm not really knowledgeable enough thought to even know what to do with a separate /usr partition  :P  so I think I'll leave it as part of my / partition.

What filesystem should the /home partition be? NTFS? Fat32? Or something different?

---

### Post by Pumalite on 2007-11-21
ext3

---

### Post by SFinn on 2007-11-23
OK I have repartitioned the disk with the GParted live CD, which worked fine. However, now my laptop is lagging really badly. With more than two tabs open Firefox, it becomes unuseable. Any ideas how to fix this?

---

### Post by geirha on 2007-11-24
Is it only lagging when firefox is running?

Oh and, when you copied the content of /home/* to your new partition, did you remove that content from your / partition? There's nothing wrong with having it on both partitions, other than that it will take up twice the space.

---

### Post by SFinn on 2007-11-25
/home is separate from /, so that's good, thanks.

Ubuntu lags for all programs. Firefox is just one example. The add/remove programs is even worse...

---

### Post by Pumalite on 2007-11-25
Post:
df -h

---

### Post by SFinn on 2007-11-26
df -h:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              11G  2.0G  7.7G  21% /
varrun                109M   92K  109M   1% /var/run
varlock               109M     0  109M   0% /var/lock
udev                  109M   72K  109M   1% /dev
devshm                109M     0  109M   0% /dev/shm
lrm                   109M   34M   75M  32% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              26G   11G   14G  43% /home

```

---

### Post by geirha on 2007-11-26
How powerfull is your graphics card?

Try disabling visual effects System->Preferences->Apperance->Visual Effects->None.

---

### Post by SFinn on 2007-11-28
Graphics card? :P My laptop is closely related to an etch-a-sketch, I think. It's not at all powerful.

For some reason, my computer has stopped lagging, although I haven't changed any settings. I've been restarting alot, though, because its been crashing. Maybe that has something to do with it...

Thanks everyone for helping me with repartitioning my hard drive. Everything's working well now.

---

### Post by Folk Theory on 2007-12-24
im following this guide to move my /home to a new partition i just made. my question is though, how do you add entries to fstab?

---

