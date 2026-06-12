---
title: "can't access hard drive"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by andrewpb on 2006-12-31
so the only hard drive i can save things to is the swap drive, and needless to say it doesn't have a hell of a lot of space.  i partitioned the main drive to have 18 gigs and when i try saving things to it it says i don't have access.  i can see the look at the contents to the main drive (filesystem) but can't save stuff to it.  what could be the problem?

---

### Post by meng on 2006-12-31
What do you mean by "swap drive"? The term "swap partition" in Linux refers to virtual memory, and you can't save anything to it, so I assume you're using the term to mean something else.

What is this "main drive"? Is it where Windows is located?

Perhaps you could go back to the beginning and describe in more detail how you installed Ubuntu.

Also the output of this command might help:
sudo fdisk -l
(that's l as is leadfoot)

---

### Post by andrewpb on 2006-12-31
so when i installed ubuntu i went in and partitioned the drives myself, because when i tried to have ubuntu do it for me, it didn't work very well.  i partitioned the drives so that i would have one windows drive (hdc2) with 18 gigs, a swap partition (hdc4) with 2 gigs, and what i hoped to be a ubuntu partition (hdc3)  i partitioned hdc3 several times in various forms but it never worked when i installed ubuntu so i formatted it to be a JFS filesystem.  i have a feeling that is where i went wrong.

here is the fdisk output
Disk /dev/hdc: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           8       64228+   b  W95 FAT32
/dev/hdc2   *           9        2048    16386300    7  HPFS/NTFS
/dev/hdc3            2570        4864    18434587+  83  Linux
/dev/hdc4            2049        2569     4184932+  82  Linux swap / Solaris

Partition table entries are not in disk order

(on a side note, is it just me or do i need another hard drive, this dell inspiron needs a little extra storage space, and would the extra space speed up the computer?)

thanks as always

---

### Post by meng on 2006-12-31
I'm not sure that JFS is causing your problem, although ext3 (perhaps reiserfs) is a more popular choice. Anyway, you can't save to an NTFS partition by default (it's mounted as read-only), so in this respect there's nothing "wrong" with your system.

Write access to NTFS through Linux is still experimental and requires ntfs-3g (search the forums for an ntfs-3g howto if you really want to do this).

---

### Post by andrewpb on 2006-12-31
i'm not trying to save to ntfs, i'm trying to save to hdc3 the JFS and it says i don't have permission and that's where it's getting funky because that's the partition that i was hoping to be used for ubuntu.

---

### Post by taurus on 2006-12-31
Where do you mount /dev/hdc3 to?  You just change the permission of that mount point with chmod command...

---

### Post by andrewpb on 2006-12-31
how do i find the mount point, and then how would i change the permission.

---

### Post by taurus on 2006-12-31
```
df -h
```

---

### Post by andrewpb on 2006-12-31
this is the output

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc3              18G  2.2G   16G  13% /
varrun                252M   76K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  124K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hdc1              62M   30M   33M  48% /media/hdc1
/dev/hdc2              16G   11G  5.2G  67% /media/hdc2

and now i should...?

---

### Post by taurus on 2006-12-31
/dev/hdc3 is your / so if you want to write to it, you need to use the sudo Ior gksudo) command!  I would strongly recommend you don't change the permissions to / because bad things will happen to your machine, like dead in the water...

---

### Post by andrewpb on 2006-12-31
hmmmm.....i understand now what the problem is thanks.
however if hdc3 is the partition with the most free space on it, where can i save files and such without reeking havoc on the computer?  could i retool the partitions so that hdc3 has less space and hdc4 more?  i don't know i'm just fishing around now.

---

### Post by taurus on 2006-12-31
Well, you can create a /opt/share and let people write to it...

Applications -> Accessories -> Terminal
```
sudo mkdir /opt/share
sudo chmod -R 777 /opt/share
```

---

### Post by andrewpb on 2006-12-31
so since i did this where can go to save things and so forth?

---

### Post by taurus on 2006-12-31
You can save things to /opt/share!

---

### Post by andrewpb on 2006-12-31
thank you very much for all your help today with both of my problems!  have a great new year, and sooner or later i'll get the hang of this linux stuff.:-D

---

### Post by taurus on 2006-12-31
It takes a little of practice and get used to.  Soon, you can do all of this and more in your sleep!

---

### Post by meng on 2006-12-31
> **andrewpb said:**
> so since i did this where can go to save things and so forth?
Data and configuration files can end up all over the place (potentially) but a lot of it ends up in your home directory (e.g. it may be named something like /home/andrew). So one popular way of storing data separately is to create a new partition which mounts/maps to /home/andrew. It's still at the same place in the filesystem, but at a different or separate physical location on the hard drive.

But don't be too concerned about your system becoming gunked up with files. It's not the same as Windows! For starters, there's essentially no issues with fragmentation, because files are written to disk in a completely different way compared to Windows; also, if there's a sudden failure (such as a power outage) then the journaling on the filesystem makes it easier for data to be recovered.

And you can't save data to what is currently /dev/hdc4, that's a swap partition or virtual memory, not a permanent location for data.

There are many things to get used to in transitioning from Windows. You can forget most of the old paradigms. I think that among the more difficult ideas to embrace are, that in most cases (some users have very special needs, so I can't say this for everybody): you don't need antivirus, you don't need defrag, you don't have "separate drives", and you don't need to configure a firewall, you don't have to manually retrieve or install applications (the list goes on).

---

