---
title: "mount a FAT32 partition at startup"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-12-07
Hi
While installing Ubuntu Gutsy dual booting with XP, I created a parttiion for Gutsy (ext3, swap), and also created a FAT32 for data sharing on the same hdd as a logical partition.; but did not provide information for mounting it at installation ("do not mount..." ).

I can mount the partition when logged in by right clicking /media/disk and mounting it.

I wish to :

1. Relabel the partition from "disk" to "DATA"
2. reformat to NTFS (for security reasons)
3. Have it mount automatically at login

Is this possible?

Thanks
S

---

### Post by kpkeerthi on 2007-12-07
Yes it is possible. First, can you post the output of
```

sudo fdisk -l

```

---

### Post by kpkeerthi on 2007-12-07
sudo fdisk -l lists out the partitions in your disk. In the explanation that follows, I assume /dev/sda3 is the FAT partition that you wish to format to NTFS. I advice you to change /dev/sda3 to the appropriate partition in your setup.

1. Boot with Ubuntu Live CD. From terminal type
```

gparted

```

2. **Partitioning with gparted**
gparted is a partition editor. It is graphical and its operations are fairly intuitive. See [gparted documentation]("http://gparted.sourceforge.net/documentation.php") and [NTFS partitioning with gparted]("http://www.mepisguides.com/Mepis-6/Install/gparted/gparted-oem-ntfs.html") to get an idea of what it takes to partition with gparted. 
I will outline the steps involved here:
```

1. Click to select /dev/sda3.
2. Click "Delete" from the toolbar.
3. Click "Apply".
4. This will produce "Unallocated Space".
5. Click to select "Unallocated Space".
6. Click "New" from the toolbar.
7. In the dialog that pops up, select "NTFS" for Filesystem option. Verify and adjust the partition size if required. 
8. Click "Add".
9. Click "Apply" and wait till it finishes.
If all goes well, your new NTFS partition (/dev/sda3) is now ready. 

```

3. Boot normally from hard disk and open a terminal.

4. Make folders where the partions will be mounted
```

sudo mkdir /media/DATA

```

5. Make a backup of /etc/fstab
```

sudo cp /etc/fstab /etc/fstab.backup

```

6. Open /etc/fstab
```

gksudo gedit /etc/fstab

```

7. Add the following line at the end of the file
```

/dev/sda3 /media/DATA ntfs-3g defaults 0 0

```

8. Save and Exit. **Restart**. You should now see shortcut to DATA on your desktop.

---

### Post by shuttleworthwannabe on 2007-12-07
It worked perfectly thanks
S

---

