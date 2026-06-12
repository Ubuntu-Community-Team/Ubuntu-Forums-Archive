---
title: "Lost Hard Drive"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by mdfenley on 2006-11-23
Just installed ubuntu 6.10 - accidently installed over my windows xp - ooppss - no biggy, didn't like it that much anyway.  So far, I am sold on ubuntu.  Have tried different flavors in the past (Mepis, Redhat, Fedora), but so far ubuntu is working great.  Here is my problem

I have 3 hard drives on my computer - 1 hard drive is usb, the other 2 are ide drives.

The 1st drive 80 gig - ubuntu is installed on. 
2nd drive is 500 gig - Can't find it anywhere. 
Usb Drive is 200 did - Identified as usb drive and is mounted.

If I run gparted, I can see the 2nd hard drive as /dev/hdc but I can't access it.  It shows that it is an NTFS partition.  I really need to access it as all my backup files, family photo's and such are on that drive.  Is there a way that I can make that drive accessable??  

Any advice/instructions would be greatly appreciated.  Thanks in advanced...

MD

---

### Post by taurus on 2006-11-23
Paste the output of this command here and I will walk you through it!!!

Applications -> Accessories -> Terminal:

```
sudo fdisk -l
```

---

### Post by mdfenley on 2006-11-23
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9542    76646083+  83  Linux
/dev/hda2            9543        9729     1502077+   5  Extended
/dev/hda5            9543        9729     1502046   82  Linux swap / Solaris

Disk /dev/hdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       55575   446406156    7  HPFS/NTFS

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS
dad@dad-linux:~$ 

I think this is what you wanted.  I hope.  By the way, thanks for the help.

MD

---

### Post by taurus on 2006-11-23
So, /dev/hdc1 is the one want to mount and copy stuff over!  Edit your /etc/fstab to include an entry to mount it...

```
sudo cp /etc/fstab  /etc/fstab.bak <-- make a back up copy first...
gksudo gedit /etc/fstab
```
Scroll all the way down to the bottom and add this line.

```

/dev/hdc1  /media/windows  ntfs  nls=utf8,umask=0222 0  0

```
Now, create a mount point and mount it.

```
sudo mkdir /media/windows
sudo mount -a
df -h <-- you should see /dev/hdc1 mounted on /media/windows...
```

---

### Post by mdfenley on 2006-11-23
Thank you, Thank you, Thank you.  I know my wife would kill me if I lost everything.  Gonna burn a DVD of all that stuff now.  Again, Thanks.

BTW, is there a book or e-book or pdf document that tells how to do stuff like this.  I am pretty sure I am going to stick with Ubuntu, so I would love to learn more about stuff like this.

MD

---

### Post by aidanr on 2006-11-23
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
is probably the best reference out there

---

### Post by taurus on 2006-11-23
It's Thanksgiving so nobody is going to kill anybody.  Maybe tomorrow when the malls open when people step over others to get to the new toys...  ;) 

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://tldp.org/](http://tldp.org/)

---

