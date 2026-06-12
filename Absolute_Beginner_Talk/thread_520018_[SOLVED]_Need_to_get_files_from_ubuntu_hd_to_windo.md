---
title: "[SOLVED] Need to get files from ubuntu hd to windows 2000 hd"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by captainwitherspoon on 2007-08-07
I need to get some files from my ubuntu hd to my win2k hd. I've tried ntfs-config but it won't allow me to check the box that says 'enable write support for internal hd' and I've tried fsdriver for windows which says there are no [ext3?]partitions to configure. 
here is the output for fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24133   193848291   83  Linux
/dev/hda2           24134       24321     1510110    5  Extended
/dev/hda5           24134       24321     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2494    20033023+   7  HPFS/NTFS

```
My ubuntu drive is set to master, win2k is slave. Any help greatly appreciated.

---

### Post by stchman on 2007-08-07
> **captainwitherspoon said:**
> I need to get some files from my ubuntu hd to my win2k hd. I've tried ntfs-config but it won't allow me to check the box that says 'enable write support for internal hd' and I've tried fsdriver for windows which says there are no [ext3?]partitions to configure. 
here is the output for fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24133   193848291   83  Linux
/dev/hda2           24134       24321     1510110    5  Extended
/dev/hda5           24134       24321     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2494    20033023+   7  HPFS/NTFS

```
My ubuntu drive is set to master, win2k is slave. Any help greatly appreciated.

So ntfs-3g is installed as it is a dependency of ntfs-config.

Try this in your fstab:
```

/dev/hdb1       /media/windows ntfs-3g  defaults  0   0

```

Remember you must make a mount point somewhere.

Then do a:
```

sudo mount -a

```

Let us know of that worked.

Refer to my webpage:

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by mc4man on 2007-08-07
both ext2fis and ntfs-config work on my 2 dual boot/2 hdd systems With ntfs-config you have to set a mount point 1st before you can enable write support
 using ext2fis are you accessing it thru the control panel?

edit:i have both os's on the same hdd versus separate hdd's as you

---

### Post by captainwitherspoon on 2007-08-07
I copied and pasted your code into /ect/fstab then ran the command with the following results. I'm not sure how a mount point works, I will look it up but if you tell me what to type that would be awesome. 

```
root@xZx:~# mount -a
fusermount: failed to access mountpoint /media/windows: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 ()

```

---

### Post by stchman on 2007-08-08
> **captainwitherspoon said:**
> I copied and pasted your code into /ect/fstab then ran the command with the following results. I'm not sure how a mount point works, I will look it up but if you tell me what to type that would be awesome. 

```
root@xZx:~# mount -a
fusermount: failed to access mountpoint /media/windows: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hdb1 ()

```

You have to create a mount point.  Assuming the fstab still has the line do the following:

```

sudo mkdir /media/windows
sudo mount -a

```

---

### Post by captainwitherspoon on 2007-08-14
thankyou for the help, that worked perfectly!

---

