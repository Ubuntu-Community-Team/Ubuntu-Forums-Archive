---
title: "dual-boot --&gt; only Ubuntu"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by jkreef on 2008-01-18
I want to get rid of my dual boot as I find that I rarely use windows, is there any way besides dumping my hard-drive and re-installing Ubuntu to get rid of my windows?

---

### Post by p_quarles on 2008-01-18
Yes, but you'll still want to have everything backed up, and be *prepared* to reinstall if anything goes wrong. 

1) Get the [GParted live CD]("http://gparted-livecd.tuxfamily.org/")
2) Boot using that
3) Delete the Windows partition
4) Expand the Ubuntu partition into the newly freed space
5) [Reinstall GRUB]("http://ubuntuforums.org/showthread.php?t=224351") 

Optionally, you don't need to reinstall GRUB if you simply edit the Windows entry out of /boot/grub/menu.lst. But, reinstalling is the more sure-fire way of doing it.

---

### Post by jordanmthomas on 2008-01-18
1.  ```
gskudo gedit /boot/grub/menu.lst
```
comment out / delete the windows part (near the end)
Mine looks like this
```
title windows
rootnoverify (hd0,0)
chainloader +1
boot

```
Yours should be similar.

Now, you have two options:  
**First**:  you can just format the old windows partition and use it in Ubuntu however you please.  Run
```
mount
```
To see if your windows partition is mounted.  If it is,
```
sudo umount /path/to/mountpoint
```
and then you can run gparted to reformat it (or fdisk if you prefer, whatever)
**Second**:  This will only work easily if Ubuntu was installed on your disk BEFORE Windows.  You can completely remove the Windows partition and resize your Ubuntu one to refill the rest.  To do this, just use the Ubuntu LiveCD and run gparted from it.

If you're confused, just post the output of 
```
sudo fdisk -l
```
and someone will be able to help you out.

---

### Post by monte48lowes on 2008-01-18
A more simple method would be to unmount the windows partition, then format as ext3 and add the new partition to the filesystem tables and use it as extra storage or backups.

Mike

If you need help with the above... post back.

Happens everytime... lmao. What ^ the above poster said.

---

### Post by jkreef on 2008-01-18
So I should just do what Jordan says in his post after getting various files that I need and backing up everything I need? If so do I need to replace certain things in the terminal commands or just type them exactly as they are? Thanks for the great help here. It is partially why I decided to get rid of windows. That and my HD is full. Mostly the community.

---

### Post by monte48lowes on 2008-01-18
Open a terminal and input this code:

```
sudo fdisk -l
```

copy the output and paste into a reply.

Mike

---

### Post by jordanmthomas on 2008-01-18
> **jkreef said:**
> So I should just do what Jordan says in his post after getting various files that I need and backing up everything I need? If so do I need to replace certain things in the terminal commands or just type them exactly as they are? Thanks for the great help here. It is partially why I decided to get rid of windows. That and my HD is full. Mostly the community.

You would need to replace things in them.  Otherwise, they wouldn't work right.
Specifically, you'd need to replace /path/to/mountpoint with where your windows partition is mounted.

---

### Post by jkreef on 2008-01-18
I did the sudo fdisk -l and came up with:
> joe@joe-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12422    99772226    7  HPFS/NTFS
/dev/sda2           12933       14462    12289725    7  HPFS/NTFS
/dev/sda3           12423       12903     3863632+  83  Linux
/dev/sda4           12904       12932      232942+   5  Extended
/dev/sda5           12904       12932      232911   82  Linux swap / Solaris

Partition table entries are not in disk order


---

### Post by monte48lowes on 2008-01-19
It doesn't appear that you have much room for linux. My recommendation now would be to back up the data you need, and reinstall ubuntu. If you use the guided disc partitioning during install it will use the whole disk. Just a lot going on there...

Mike

---

### Post by jkreef on 2008-01-19
So the easiest thing would be to just pop in the live CD again and reinstall Ubuntu? And thanks for all this help.

---

### Post by ugm6hr on 2008-01-20
> **jkreef said:**
> So the easiest thing would be to just pop in the live CD again and reinstall Ubuntu? And thanks for all this help.

That is a reasonable suggestion.

The other option is to *delete partition sda1*, then create a new partition *sda1* in its place (as ext3).

Then use this: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) to create a separate /home partition for ubuntu (on sda1).

This would free up space on your "Ubuntu" partition (by removing /home), as well as giving direct access to the previous Windows space as /home.  

Potentially, you could also delete sda2 (at end of disc - is this a restore partition or something?), and move the swap into it, to allow sda3 (Ubuntu) to be a bit bigger too.

Don't want to confuse things.... Just giving options.

---

### Post by monte48lowes on 2008-01-20
Make sure you have the data you need saved somewhere else. Then use the install CD and reinstall.

Mike

---

### Post by bwtranch on 2008-01-20
boy, you guys go to a lot of trouble to do this,

all you have to do is tar the files and burn

---

