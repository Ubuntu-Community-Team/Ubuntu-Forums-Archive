---
title: "Hard drive crashed, partition gone"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2007-05-21
Hiya,

For some obscure reason, my NAS drive kinda died. I say kinda, because i can still see 2 of the 3 partitions..

The data on the 3rd partition ( around 230 GB) is what i would like to recover. My partition is gone, as like i said.

fdisk -l
> Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   82  Linux swap / Solaris
/dev/sdb2             132       30515   244059480    5  Extended
/dev/sdb5             132         392     2096451   83  Linux
/dev/sdb6   ?       69589      138785   555819297   42  SFS


But i don't have a /dev/sdb6 file (or folder, don't know what those things are :oops: )!

My hard drive was partitioned in the following way:
2GB root on a primary partition, 233GB extended partition wich is divided by my swap (1GB i think) and the Ext3 partition (should be around 230GB)

Testdisk (a repo program) doesn't find my partition aswell..

Does anyone know how i could get my stuff back?


Iarwain

---

### Post by justleen on 2007-05-21
acuh.. I saw the title, and thought " Testdisk!"  but you've tried that.. how about foremost or autopsy?
The require another 230gb for imaging.. but there good tools..

---

### Post by starcraft.man on 2007-05-21
Hmmm, maybe this has to do with low level errors... drives can be tricky. My suggestion would be spinrite (not free or open source but is both effective and has saved my old 6 year drive twice from scrap pile).

It's made by steve gibson, it reads and writes to the lowest level of drive and can recover bad/corrupt sectors of data. It is also very good at it. I don't know if it will fix your problem, and while I don't condone piracy really... you can get spinrite for free that way and see if it works. If so, and you feel like supporting the product you can always purchase a license. The fun thing is Steve doesn't mind, I've seen at least 30 testimonials of people who used a friends/pirate copy and then bought the real thing.

It is of course indexed on sites like isohunt, up to you... you then just burn it as a CD/floppy and reboot into it. Then you can use the menus to recover data.

Hope it gets fixed.

---

### Post by BHelts on 2007-05-21
the previous poster is right, spinright is incredible.  the first thing to check is the smart data for the selected drive.  if your reallocated sectors count is above 2 or 3 it's time to get a new drive.  the only other thing to be aware of is spinright spins the disk, for an extended period of time.  IF the drive is bad or going bad, and you want to perform data recovery, the more the disk spins, the harder it may become.  you may be better off creating a clone of the drive so you have a backup of what is visible, then give it a go on the live drive.

---

### Post by starcraft.man on 2007-05-21
> **BHelts said:**
> the previous poster is right, spinright is incredible.  the first thing to check is the smart data for the selected drive.  if your reallocated sectors count is above 2 or 3 it's time to get a new drive.  

Wasn't the SMART data proven though conclusively (I thought) to be unreliable at best and useless at worst in the google labs paper on their mass hard drive test? Are you certain thats a good barometer?

---

### Post by BHelts on 2007-05-21
it is a horribly terrible barometer.  s.m.a.r.t only reports what the manufacturers tell it to report, and there isn't any consistency.  however, smart is a great place to start, because reallocated sectors have been reallocated and are no longer usable.  The other good thing about spinrite is this:  it will tell you if the system BIOS has turned smart reporting off, and it will turn it on.  you are correct, smart data should not be used as a conclusive diagnostic tool, but it is a good start.

---

### Post by Iarwain ben-adar on 2007-05-21
Quick question (looking at Spinrite atm)

How should i go about this, if the drive mentioned is a USB-attached drive, and my pc is a laptop?


Iarwain

---

### Post by starcraft.man on 2007-05-21
> **Iarwain ben-adar said:**
> Quick question (looking at Spinrite atm)

How should i go about this, if the drive mentioned is a USB-attached drive, and my pc is a laptop?


Iarwain

Uhhhhh... darn, I believe spinrite is pretty much designed for use with internal drives >.>. Thats mostly to do with how low it must access... not sure if ya can get it to work on a USB drive. Download the torrent, there is a pdf inside, maybe steve included instructions that can help. I've only ever run it on internal drives.

---

### Post by Iarwain ben-adar on 2007-05-21
Luckily i'm such a pc-freak, that i have another pc somewhere..

I'll try that, probabely tommorrow (got much homework to study :( )

Thanks for the replies everyone,
it gave some hope!


Iarwain

---

### Post by starcraft.man on 2007-05-21
> **Iarwain ben-adar said:**
> Luckily i'm such a pc-freak, that i have another pc somewhere..

I'll try that, probabely tommorrow (got much homework to study :( )

Thanks for the replies everyone,
it gave some hope!


Iarwain

Good luck with fixing it and exams? I'm sure it will all work out :D.

---

### Post by Iarwain ben-adar on 2007-05-22
Just tests, exams starting the 7th of June :s

So, i tried 'fixing' my drive with Spinrite..

Level 2 doesn't find anything fishy, so i tried it at level 5. It takes about 10 hours or so, and it's halfway :D

I don't hold my hopes high no more. Seems al lost to me (pretty annoying actually, because school-files are/were also on that drive ;o )


Iarwain

---

