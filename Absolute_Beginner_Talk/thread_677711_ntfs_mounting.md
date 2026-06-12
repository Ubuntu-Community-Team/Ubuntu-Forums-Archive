---
title: "ntfs mounting"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by mdewet on 2008-01-25
I dual boot Gutsy & Vista with 2 NTFS partitions..after startup the one NTFS partition is mounted and on the desktop, but everytime I have to enter the admin password to use the other partition.  I suppose it is mounted because it shows when I go to >Places>Computer, it's just annoying to enter the password everytime I want to access it. 

Is there some setting that I have missed?  Can the HD be mounted and accessed without having to enter the password?

---

### Post by kpkeerthi on 2008-01-25
Find the NTFS partition names using
```

sudo fdisk -l

```

Assuming you want to mount /dev/sda1 and /dev/sda1 to Windows1 and Windows2...

1. Create the folder where you want the partions mounted
```

sudo mkdir /media/windows1
sudo mkdir /media/windows2

```

2. Add entries to fstab so ubuntu automounts at startup
```
gksudo gedit /etc/fstab
```
Then add the entries to the end of the file
```

/dev/sda1 /media/windows1 ntfs-3g defaults 0 0
/dev/sda2 /media/windows2 ntfs-3g defaults 0 0

```
If you find one of your NTFS partitions already listed in fstab comment it out. Save and Exit.

3. Test ```
sudo mount -a
```. You should now see the discs (icons) on your desktop. (Report the errors if any)

**Note:** Change /dev/sda1 and /dev/sda2 to whatever you discovered with **sudo fsdisk -l** command above.

The partitions should be automounted upon next boot.

---

