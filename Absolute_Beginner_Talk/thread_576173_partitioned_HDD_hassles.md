---
title: "partitioned HDD hassles"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Jason Weiss on 2007-10-14
Hi,

I partined my hard drive into 2 partions and I have been using one partion to store my photos music etc. 

However everytime I want to access the drive I need to type in my password 

I would like to be able to access this drive via samba. 

Is there a way that I can set this drive up so that I do not need to type in my password to access it, and can I change the name of this, at the moment it is just called "disk"  can i give it a more meaninful name?

---

### Post by juantovarm on 2007-10-15
can you post your /etc/fstab ? in the terminal type: pico /etc/fstab and post it here

---

### Post by Jason Weiss on 2007-10-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb4
UUID=06eb0e31-93f3-40e7-a490-be1c1b51b000 /               ext3    defaults,erro$
# /dev/hdb6
UUID=79ae7446-e5e4-46cc-935b-6a9e3dc18615 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by monado on 2007-10-15
Sorry, but I fail to see your partitioned drive. Well I see fstab, but it's puzzling. So you have a root partition mounted at / and a swap partition. Don't see your music/photos partition. Can you make it a bit clearer?
Please post your output of fdisk. In the terminal enter:
```
sudo fdisk -l
```

---

### Post by Jason Weiss on 2007-10-16
[QUOTE=monado;3536202]Sorry, but I fail to see your partitioned drive. Well I see fstab, but it's puzzling. So you have a root partition mounted at / and a swap partition. Don't see your music/photos partition. Can you make it a bit clearer?
Please post your output of fdisk. In the terminal enter:
```
sudo fdisk -l
```[/QUOT

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       13873   111434841   83  Linux
/dev/hdb2           38361       38913     4441972+   5  Extended
/dev/hdb3           13874       34393   164826900   83  Linux
/dev/hdb4   *       34394       38360    31864927+  83  Linux
/dev/hdb5           38537       38913     3028221   82  Linux swap / Solaris
/dev/hdb6           38361       38536     1413657   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by juantovarm on 2007-10-16
if i am not mistaken /dev/hdb3 should be your other partition, so you can edit your 
/etc/fstab by typing in the terminal: sudo pico /etc/fstab  and then this at the end of your fstab file:

/dev/hdb3        /media/disk          ext3          user,auto          0       0


use the tab key to align them 


If you would like to to change the name of your disk, you have to rename the folder where it is going tho show the contents of /dev/hdb3. In the terminal type: sudo cp /media/disk   /media/music (if that how you want to name it), 

BUT remember that the mount point in your filesystem must be the same as the one in the fstab file, so if you rename it to /media/music in your file system, in the fstab file it should be 

/dev/hdb3        /media/music         ext3          user,auto          0       0

I don't think i am missing anything...

Hope it helps

Juan

---

### Post by Jason Weiss on 2007-10-16
You Rock Juan, 

Thanks for your help.

---

### Post by Jason Weiss on 2007-10-17
I just realised you missed a step 

> sudo mkdir /media/share


---

