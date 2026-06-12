---
title: "Mounting partition"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by el mariachi on 2007-06-12
Just bought a new HD and made an ext3 partition. It's mounted in /media/ but I want it to appear either in root or home. 

It also doesn't give me permission to read/write (only root can) and although gparted says it has 180gb of free space, nautilus, in the status bar and proprieties window, says it only has 20gb.

My other partitions (/, /home, /usr and /windows) were made during the installation and are exactly like I want.

Thanks for your help!;)

---

### Post by Skrynesaver on 2007-06-12
Where do you wish to mount the partition?
As a second home directory?
As a ~Mariach1/data directory?
This is the first thing you need to decide.

Having made that decision you should mount it under media first and copy over any data it will be holding. To do this in a terminal 
```

mount -t ext3 /dev/hdb1 /media/temp
cp -Rp <data-files> /media/temp
umoount /media/temp

```
Then add the following line to your /etc/fstab file as root.
/dev/hdb1 /home/mariach1/data ext3 defaults 1 0

NOTE change the values to reflect your situation.
Any questions please ask ;)

---

### Post by Wim Sturkenboom on 2007-06-12
Output of *sudo fdisk -l* will show you how it's partitioned. You will / should see hda/sda and hdb/sdb. To see it as a directory in /root or /home, you have to modify /etc/fstab. You will see you mountpoint in there. 'Simply' change the mountpoint. You will also find the permissions there (change the word 'root' to 'user')

```

/dev/sda1        [COLOR="Green"]/mnt/cruzer2[/COLOR]     vfat        noauto,[COLOR="Red"]user[/COLOR]      0   0

```The green text is the moint point, the red one is the permission.
Your line will look different (this comes from a Slackware box and is for my memory stick), but it gives the idea where to look.

If in doubt, post the output of both commands here.

---

### Post by el mariachi on 2007-06-12
Thanks for the quick reply!

I want it to be inside my home partition and, for starters, empty - I'll add stuff later - if that's possible. 

So I wanted it to be placed like this /home/mariachi/stuff

---

### Post by antoz on 2007-06-12
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm) this link may be helpfull

---

### Post by el mariachi on 2007-06-12
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401   83  Linux

```

This is the output of [I]fdisk -l (only the hd in question).

[/I]

---

### Post by el mariachi on 2007-06-12
> **antoz said:**
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm) this links may be helpfull

that seems to be for temporary mount. I want it to be permanent

---

### Post by Princey on 2007-06-12
> **Skrynesaver said:**
> Where do you wish to mount the partition?
As a second home directory?
As a ~Mariach1/data directory?
This is the first thing you need to decide.

Having made that decision you should mount it under media first and copy over any data it will be holding. To do this in a terminal 
```

mount -t ext3 /dev/hdb1 /media/temp
cp -Rp <data-files> /media/temp
umoount /media/temp

```
Then add the following line to your /etc/fstab file as root.
/dev/hdb1 /home/mariach1/data ext3 defaults 1 0

NOTE change the values to reflect your situation.
Any questions please ask ;)

Correction, it's ```
umount /media/temp
``` not > umoount /media/temp

---

### Post by Princey on 2007-06-12
One method is to create a directory in home, like in your case ```
mkdir stuff
``` then mount the drive in the folder. Say for example sakes, it's listed as sdc1. You'd edit your fstab file like this. First the command: ```
sudo gedit /etc/fstab
```

Then edit the lines that would most likely look like this > /dev/sdc1  /media/stuff to look like this > /dev/sdc1  /home/mariachi/stuff save and close then type ```
sudo umount
``` followed by ```
sudo mount -a
```

---

### Post by el mariachi on 2007-06-13
I did a simple ```
 sudo mv /media/Tralha ~
``` and now it's where I want it. 

Problems:
-I don't have permission to write to the disk, only root has
-The proprieties window says that it only has 20Gb of free space, while gParted says 180Gb (this being the truth)
-"Tralha" (stuff in portuguese) was the name the disk had when it was used by Windows, as a backup disk (NTFS). I did a Zero-fill, or low-level type format and also erased the MBR, so how come it still has this name?

Thanks for the help so far!

---

### Post by Princey on 2007-06-13
For the permissions section, please paste the output of > sudo cat /etc/fstab -l

For the second issue, the partition table is still set. Low level format does just that, it doesn't delete the partition table. You have to completely delete all partitions and reformat otherwise, the name will still remain.

---

