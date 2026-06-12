---
title: "How to figure out which is hd0 and hd1, etc?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by civilmonkey on 2007-04-25
If I enter the command:

```
 sudo fdisk -l
```

1.  Will the output be listed sequentially in order of drive #'s.  I.e. hd0, hd1, etc?  

2.  If I add a hard drive to my system will Ubuntu auto recognize it as the next hd#, I.e. would I potentially need to edit boot/grub/menu.lst?

Thanks,

---

### Post by Pobega on 2007-04-25
You can either check from what type of filesystem it is, or by manually mounting it and checking out what is inside of it. It's generally smart to memorize your partition tables, so that if you ever have any problems you know exactly what to do.

---

### Post by xboxbman on 2007-04-25
> **civilmonkey said:**
> If I enter the command:

```
 sudo fdisk -l
```

1.  Will the output be listed sequentially in order of drive #'s.  I.e. hd0, hd1, etc?  

2.  If I add a hard drive to my system will Ubuntu auto recognize it as the next hd#, I.e. would I potentially need to edit boot/grub/menu.lst?

Thanks,

if you add an ide harddrive, than ubuntu will most likely call it hdb, then hdc, then hdd.  If it's a sata harddrive, it will call it sda, then sdb, then sdc.  THEN, each partition is numbered, so you'll have hda1,hda2,hda3, etc.  It's a little confusing at first, but it becomes more logical as you use it more.

---

### Post by Dirk Gardner on 2007-04-25
As of Feisty hda,hdb e.t.c have been replaced with sda,sdb e.t.c.   IDE drives are now listed alongside SATA drives.  When I upgraded, the install mixed up my drives because of this.

The easiest solution i have found to identify and repair my mounts is by using pysdm.

```
sudo aptitude install pysdm
```

```
sudo pysdm
```

Hit the triangles to the left of the drives to expose partitions and mount them however you want.

This nifty program makes things real simple by modifying fstab perfectly for you.

---

### Post by civilmonkey on 2007-04-26
I will keep your ideas in mind and look into pysdm.

The reason I asked was because originally when I installed Ubuntu I had 2 hard drives installed and they were listed at /dev/hda and /dev/sda.  I understand mounting and filesystems but I had problems installing the GRUB bootloader when it came to choosing (hd0,1) or (hd1,1) for instance.  Win XP has the 1st bootable partition, and Ubuntu has the 2nd.

I didn't want to overwrite my Win XP MBR and didn't know how to figure out if /dev/sda was hd0 or hd1 in GRUB.

---

### Post by Dylnuge on 2007-04-26
Partition and hard drive numbers are in order of how they are connected and stored.

(For the purpose of this demonstration, all hard drives are listed as SATA or Fiesty IDE and are designated by sd).

sda is the first hard drive. This will be an internal hard drive, most likely the master drive on your first drive cable.
sdb is the second hard drive. If you have any external drives, they will be dealt with after internal drives. 
sdc is the third hard drive. Lets say all of your external and internal hard drives have been delt with. If you attach a new drive (jump drive, external, etc) this will be it.

Now these are mapped to hd0, hd1, hd2, etc. Usually, these will be equivilent (sda = hd0, sdb = hd1).

Each drive has partitions. These are numbered like such-sda1, sda2. Once again, these are eqivilent.

Hope this helped.

(PS: your device.map file will tell you exactly how drives are mapped).

---

### Post by civilmonkey on 2007-04-26
Clears it all up!  I thought I remembered that I had a /dev/hdA and a /dev/sdA, but perhaps not.  I'll re-install my drive and see what it appears as.

Thanks everyone.

---

### Post by Dylnuge on 2007-04-26
> **civilmonkey said:**
> Clears it all up!  I thought I remembered that I had a /dev/hdA and a /dev/sdA, but perhaps not.  I'll re-install my drive and see what it appears as.

Thanks everyone.

You could have both, if you have both an IDE and SATA drive attached. This is most likely if you have an internal IDE (common) and an external drive like a flash drive commected.

---

