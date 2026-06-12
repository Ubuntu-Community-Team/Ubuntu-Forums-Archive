---
title: "[SOLVED] External USB HDD mounting"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-27
Please help me understand .....   I have several hdd's which are plugged into the PC by USB when needed.   Plug in and the drive is detected and an icon appears on the desktop.....  so I conclude that it is auto-mounting.  After use I right click the drive icon and select Unmount.  The message appears that it is safe to remove and I take the drive away.

However, if a few hours later I want to use the same drive again it is not detected when I plug in the drive.  I can only gain access to the drive if I reboot the system.

Why does this not detect?  How can I avoid rebooting to detect the drive on the second connect?

---

### Post by taurus on 2007-10-27
Or you can just mount it by hand from a terminal without rebooting your machine.

---

### Post by eph1973 on 2007-10-27
Yes, but it will require creating a rules.d command that runs a script.  See [this]("https://help.ubuntu.com/community/UsbDriveDoSomethingHowto")

---

### Post by expatCM on 2007-10-27
taurus - what is the syntax of the command to follow please?  I guess I could even put this as a script on the desktop.....  

eph1973 - thanks for sharing the link.  I had a look and with my luck / ability it appears to be an invitation to tempt fate.

---

### Post by taurus on 2007-10-27
Plug in your external harddrive.  Then, find out what device it is, usually a /dev/sdb1 but better be sure. 

```
sudo fdisk -l
```

Now, mount it with

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
(Assuming it's a ntfs filesystem.)
df -h
```

---

### Post by expatCM on 2007-10-29
real value for the money with this one .....  a friend has an identical problem and so your response will help both of us.  Thank you for your help ...  it is really appreciated :)

---

### Post by Mjölner on 2007-11-04
> **taurus said:**
> Plug in your external harddrive.  Then, find out what device it is, usually a /dev/sdb1 but better be sure. 

```
sudo fdisk -l
```

Now, mount it with

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
(Assuming it's a ntfs filesystem.)
df -h
```




Thanks. Worked. :grin:

---

### Post by jordank on 2007-11-04
Hey there, i have a similar problem.  When i connect my external harddrive, i can view it, however, if i fail to "unmount volume" before i disconnect the drive, it will fail to recognize the drive the next time i plug it in.  
i did the command:
sudo fdisk -l
figuring maybe i could mount it through the terminal next time it doesn't recognize.

at the time being, it is plugged in and recognized, but i can't distinguish which of the things listed is my external harddrive.  Anyone help me interpret this? (it's a 500gb external)

code:

jordan@jordan-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc25a6858

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab426633

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

---

### Post by Mjölner on 2007-11-15
Hi jordank

as far as I can see it is

> Disk /dev/sdb: 500.1 GB, 500107862016 bytes

and its the
> 
Device Boot Start End Blocks Id System
[COLOR="Red"]/dev/sdb1[/COLOR] 1 60801 488384001 7 HPFS/NTFS

underneath that will show you  the partitions. 



and you would need to input
[COLOR="RoyalBlue"]
sudo mount -t ntfs /dev/sdb1 /media/sdb1 [/COLOR]

if you where following the the original post.



The thing is...
there is a good possibility that your system will give your external HDD a new name in the /dev directory every time you plug it in, and it could become eg: /dev/sda1  or /dev/sdg1  
so enter 

[COLOR="RoyalBlue"]sudo fdisk -l[/COLOR]

again, to find out what its been named

Mjölner

---

