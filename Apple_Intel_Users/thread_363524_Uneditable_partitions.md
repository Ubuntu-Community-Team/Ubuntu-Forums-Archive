---
title: "Uneditable partitions"
date: 2007-02-17
forum: Apple Intel Users
---

### Post by ronocdh on 2007-02-17
I have for a while successfully dual booted OS X and Windows XP. Wanting to add (K)Ubuntu to the mix, I followed the popular guide available at [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp). I also looked at this one: [http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453).

I wasn't able to get it working. My problem now is that the partitions I made in OS X via diskutil seem unchangeable; when I try to edit them, even give the command to make the drive one cohesive volume again, I get this error:

> sudo diskutil resizeVolume disk0s2 110G
Password:
Started resizing on disk disk0s2 Pelennor
Verifying
Resizing Volume

Resizing encountered error The chosen size is not valid for the chosen filesystem (-9962) on disk disk0s2 Pelennor

How the heck can I resolve this? It happens also when I try to adjust partitions to different values; I cannot get my hard drive back to one volume! I even tried QTParted, but to no avail.

Please advise. =)

---

### Post by meng on 2007-02-17
Try GParted LiveCD to repartition.

---

### Post by Gen2ly on 2007-02-17
yes ronocdh, I've tried this too.  Once the diskutill command seems to partition it does not seem to be able to do it again. (at least thats been my experience).  diskutils command (however) isn't well documented.

---

### Post by ronocdh on 2007-02-17
Thank you for the replies, guys. Dirk, what did you do in the end? I'm certain that if I completely reformat and reinstall OS X, that would reunite the drive, but I really don't want to take it to that extreme!

Also, if I do get it working again, should I create four partitions if I plan to triple boot, the fourth being for a Linux swap? Because my problem at the moment is that Ubuntu won't install without a swap partition, and I cannot create one in the installer's GUI partition editor.

I'm downloading GParted now, I'll give that a spin, meng.

---

### Post by ronocdh on 2007-02-17
The GParted Live CD did not work for me; it kept hanging when I tried to load the GUI. I was able, however, to boot to the Ubuntu Live CD and erase the Linux partitions there. Once back in OS X, I could not reunite the volume via diskutil, but I was able to repartition into 4 parts (large for OS X, small for Linux, smaller for Linux swap file, small for Windows).

I then booted again into the Ubuntu CD and ran the installer, but I failed on the GRUB installation, and was not able to acquire LILO for some reason. Argh!

But for whoever's interested, that's how I got around my partition trouble.

Thanks for your help!

---

### Post by MeltingPoint° on 2007-02-17
You should try iPartition by coriollis systems. Worked great for me to destroy a partition w/out loosing data. It comes with iDefrag (defragmentation).
With ipartition, you have to run your machine in target disk mode, or off of a separate physical disk to be able to edit the target one.
Sorry for product promotion (I dont work for them dont worry):KS

---

### Post by Gen2ly on 2007-02-18
spend money why?  rono, u may have a probelm with that!  currently the EFI-MBR partitioning format apple uses only supports 4 partitions!  One of them has to be for EFI too or Mac OSX won't boot.!

---

### Post by ronocdh on 2007-02-19
Dirk, hm, well I formatted 4 parts, one for OS X, one for Linux, one for Linux swap, and the last for XP. I wasn't able to get Ubuntu going because of GRUB failure, but I was able to boot to OS X when I needed. And I'm using rEFIt.

I have since taken out that swap part, because a new guide I read recommended I install from the Ubuntu DVD and ignore the request for a swap file... now I just have to download the ISO over 768kbps DSL. ;)

---

