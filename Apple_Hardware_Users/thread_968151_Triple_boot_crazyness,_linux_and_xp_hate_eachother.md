---
title: "Triple boot crazyness, linux and xp hate eachother."
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by dustynus on 2008-11-02
I used to have a triple boot with Tiger OSX, Ubuntu, and XP going fine. I decided to go single boot which lasted about 6 months until I needed xp back for some programs (matlab and autocad).

Now I've tried to reproduce the triple boot again using Refit, and it seems impossible to do for me.

I've been trying the following:

Format entire disk, put in osx cd, using disc utility, format as follows:

osx = 9GB
windows/linux = the rest of the drive.

I install osx, then i throw in the xp cd, install that to the big partition, letting windows format as XP the short way.

I then throw in ubuntu, use gparted to split the big windows partition in 2, making windows 16GB, and ubuntu around 50GB.
I select ubuntu to install grub to /dev/sda3, and every time it tries to install, it will fail at 94% with " FATAL: grub-install /dev/sda3 failed"
After this, osx, and windows xp work fine still, while ubuntu can't load because grub failed.


I managed to fix this, by install refit in osx, then running the gpt-mbr update with refit, then going back into the live cd and installing to the linux partition. 
and bam, linux loads up grub fine with a brand new install. But now, xp won't load, it gives me a hal.dll error.

I've tried installing all 3 more than 5 times now with slightly different ideas, and I end up with the same thing. I feel like im going crazy trying to do this, there must be something crutial I'm missing. I've tried following some examples only to end up with the same sort of thing, either xp starts and linux won't install properly, or xp won't boot and I'm allowed linux.


cheers:guitar:

---

### Post by keisunesu on 2008-11-02
I just solved the hal.dll error by opening Windows's boot.ini in Linux and changing the 3s to 2s.

However, now when Windows starts to boot, my Macbook will suddenly restart.

---

### Post by WaeV on 2008-11-02
Does ubuntu work without XP?  You could try using wine.  I Just looked matlab and autocad up and depending on your version compatibility ranges anywhere from gold to garbage.  Check the database out and see what the compatibility is for your specific versions.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by cyberdork33 on 2008-11-02
> **dustynus said:**
> I've been trying the following:

Format entire disk, put in osx cd, using disc utility, format as follows:

osx = 9GB
windows/linux = the rest of the drive.

I install osx, then i throw in the xp cd, install that to the big partition, letting windows format as XP the short way.

I then throw in ubuntu, use gparted to split the big windows partition in 2, making windows 16GB, and ubuntu around 50GB.
I select ubuntu to install grub to /dev/sda3, and every time it tries to install, it will fail at 94% with " FATAL: grub-install /dev/sda3 failed"
After this, osx, and windows xp work fine still, while ubuntu can't load because grub failed.
You can typically prevent these weird partitioning problems by creating all the partitions before you install anything...  Split the disk into the two major partitions as you did already osx / windows and ubuntu. Then boot the Ubuntu CD and use gparted to delete the "extra" partition you created and create new partititons for the Ubuntu root partition, windows, and a swap partition at the end.

Then you can start installing OSX / ubuntu / windows making sure to put grub on the ubuntu root partition as you already have.

good luck

---

### Post by dustynus on 2008-11-02
> **cyberdork33 said:**
> You can typically prevent these weird partitioning problems by creating all the partitions before you install anything...  Split the disk into the two major partitions as you did already osx / windows and ubuntu. Then boot the Ubuntu CD and use gparted to delete the "extra" partition you created and create new partititons for the Ubuntu root partition, windows, and a swap partition at the end.

Then you can start installing OSX / ubuntu / windows making sure to put grub on the ubuntu root partition as you already have.

good luck


I think I tried something like that already, and Windows XP's partitioner gives me a "Can't install because Too many partitions exist" type error.

Windows won't install when there's already 3 partitions... I think.

Correct me if I'm wrong, I'll try it regardless when I get home.

---

### Post by bmc5311 on 2008-11-02
xp will only recognize 4 partitions.
efi (mbr) partiton (hidden)
osx
ubuntu
xp

Which means no swap or seperate root & home partitions.  I've read severl posts with people who have been successful - you can try this one - [http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/](http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/)

Instead of messing with it, I reformated my nacbook (with the os x install disk) as a mbr type hard drive.  I installed xp ( 12 gb - If it wasn't for frickin rim and their blackberry software I wouldn't even have installed xp), then ubuntu (seperate swap, home and root partitons).  I moved my os x install to an external firewire drive since I hardly ever use it.  

Works for me..

---

### Post by dustynus on 2008-11-02
> **bmc5311 said:**
> xp will only recognize 4 partitions.
efi (mbr) partiton (hidden)
osx
ubuntu
xp

Which means no swap or seperate root & home partitions.  I've read severl posts with people who have been successful - you can try this one - [http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/](http://www.anomalousanomaly.com/2008/10/31/triple-booting-your-mac/)

Instead of messing with it, I reformated my nacbook (with the os x install disk) as a mbr type hard drive.  I installed xp ( 12 gb - If it wasn't for frickin rim and their blackberry software I wouldn't even have installed xp), then ubuntu (seperate swap, home and root partitons).  I moved my os x install to an external firewire drive since I hardly ever use it.  

Works for me..

I never use osx so I might try something like this. Does it book directly to grub, then you access xp from that ?

Thanks

---

### Post by alwayshere on 2008-11-02
Try Virtualbox [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) 
worked on my macbook easy as!

---

### Post by cyberdork33 on 2008-11-02
> **bmc5311 said:**
> xp will only recognize 4 partitions.
efi (mbr) partiton (hidden)
osx
ubuntu
xp

Which means no swap or seperate root & home partitions.
You can have a swap and home as well, Windows just can't see them. Windows will only recognize the first 4 partitions on the disk.

---

