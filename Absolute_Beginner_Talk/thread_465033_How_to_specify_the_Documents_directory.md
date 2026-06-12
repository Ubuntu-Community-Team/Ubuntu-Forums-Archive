---
title: "How to specify the Documents directory?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-06-05
I made a separate partition for Documents.  How do I identify it to Ubuntu?

---

### Post by taurus on 2007-06-05
Do you mean how to mount it?  What filesystem is that partition?

applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mikewhatever on 2007-06-05
If that's a partition, not a directory, you'll need to mount it.
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by lazyart on 2007-06-05
Go to Computer and see if it isn't already mounted.

---

### Post by earobinson on 2007-06-05
I think the user may be asking how to make programs auto save there instead of the home directory?

---

### Post by bettyhills on 2007-06-05
This is a dual boot set up with Windows NTFS 35GB, FAT32 Shared Data Partition 80GB, and Ubuntu Ext3 31GB.  All are mounted, plus 2 other mysterious Dell primaries.  The only partition I want to see on the desktop is the FAT32 Shared Data Partition.  I tried to unmount Windows and the other 2 but they keep coming back next boot.  So I was trying to hide all icons but the FAT32 (by making_ it _a Documents directory) in Nautilus.

I should have asked "how best to accomplish making everything but the Shared Data partition disappear from the desktop?"

P.S.  I have managed to find my way to Terminal, but not much more.  Be gentle...

---

### Post by taurus on 2007-06-05
Mount it somewhere else like /mnt/Documents instead of /media/Documents.

```
gksud gedit /etc/fstab
```

---

### Post by vanadium on 2007-06-05
I&#314;l try to be gentle ;) indeed:

BEFORE WE PROCEED:

make a backup of your /etc/fstab: this way you can blame me. Then use the magic command of mr taurus (gksudo, not gksud)

```

cp /etc/fstab  /etc/fstab.backup
gksudo gedit /etc/fstab

```

With this command, you will load gedit as superuser with the file /etc/fstab. That file tells the sytem what to mount where. You will now tell it to mount the windows partitions under /mnt instead of under /media.

Look for the lines pointing to your windows partitions. Take note of the mount points, i.e  the second entry on the line that contains /media. This will read like /media/mydisk with mydisk the labels used for your disks. Change the /media to /mnt

When done, save the file and close gedit.

Next, you need to create the new mount points! A mount point is nothing else than an empty directory somewhere in the file system. In your case, you will create two of these (to mount two disks, one of which will be /media/mydisk -> obviously subtitute your actual label for mydisk).

```

sudo mkdir /mnt/mydisk
sudo mkdir /mnt/<label of your second disk>

```

Next, you could just restart and see it work, but restarting is the Windows way and we stay away from that. Therefore: unmount your two disks (right-click their icons and select unmount or

```

sudo umount /media/mydisk
sudo umount /media/<label of your second drive>

```

Finally remount all according to your new fstab

```

sudo mount -a

```

Your drives should now be accessible from the file system in /mnt.

If you are smart and want to do it the Linux way, then create directories in your drives and create links from within your home directory to them. You can also create a link to the mount point to have all of your disk on a convenient location in your home directory. the transparant and flexible way these things work in Linux leave Windows far behind...

---

