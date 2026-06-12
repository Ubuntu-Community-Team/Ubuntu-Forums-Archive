---
title: "Ntfs!"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by JoeZ on 2006-01-13
Okay... So I have a partion that is NTFS, which I dont want...
I want to format it and have it easy acceible on Ubuntu...
How do I do this... I dont seem to can work it out?
And how do I make it easy to go in and out of it?
Like have an shortcut on the desktop?
But I want to completly wipe out the NTFS part...

---

### Post by stuporglue on 2006-01-13
In System-->Administration-->Disk Manager select the partition and select "format". Use Extended 3, unless you need to get at it from Windows (then use FAT). Give it a mount point, and you should be good. The icon may even show up on your desktop automatically

---

### Post by JoeZ on 2006-01-13
Okey! How exactly do I mount... I think I&#228;ve done it?
But the format goes VERY fast... Like two seconds, is this right and when I write
sudo fdisk -l in the terminal it still says that it is NTFS....
And when I restart its not activated anymore...

---

### Post by Mr_Grieves on 2006-01-13
Check out the NTFS-progs.
[http://www.linux-ntfs.org](http://www.linux-ntfs.org)

To install:
```

sudo apt-get install ntfsprogs

```

In this tool package there is something called mkntfs wich can format the ntfs partition for you.

[http://man.linux-ntfs.org/mkntfs.8.html](http://man.linux-ntfs.org/mkntfs.8.html)

---

### Post by cotcot on 2006-01-14
Another way is in command mode : 
parted

this gives you the "parted" prompt

print

this gives you a list of your partitions; each line start with a number. Look for the number of the partition you want to reformat and double check this !

mkfs x fat32

this makes a filesystem type fat32 on partition x whereas x is the number you of your partition

---

### Post by GreyFox503 on 2006-01-14
I like the program 'gparted' for managing partitions.  It is a nice graphical one.  I forget if it comes default with Ubuntu.  If it's not in Applications > System Tools, then just

```
sudo apt-get install gparted
``` 
It can format partitions for you, but for mounting, you will need to do that yourself by editing your /etc/fstab file.

---

