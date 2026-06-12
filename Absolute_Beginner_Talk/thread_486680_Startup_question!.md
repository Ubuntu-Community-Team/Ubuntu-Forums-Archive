---
title: "Startup question!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by jonttix on 2007-06-28
When the startup comes to the "checking file systems" phase, it stops for several minutes. I have windows installd on an other partition simultaniously, I think it is that partition that makes it take so long. What can I do to make it faster, other than delete windows?

---

### Post by Seisen on 2007-06-28
Does it do it everytime you boot up ubuntu or is it periodically?

---

### Post by Cypher on 2007-06-28
The checking filesystem should only be touching Linux (EXT3) partitions, it should/does not do anything with Windows partitions. This check should only be happening once every 20-30 bootups and not every single time. If the check is happening even single time, you should see how you go about shutting down the machine which is a key reason for the need to check the filesystem on every bootup..

---

### Post by jonttix on 2007-06-28
It does it every time I start!! How do I check the shutting down?

---

### Post by ITdrummer on 2007-06-28
Im assuming that he is asking you if you press the power button, use the menu, or unplug the power cable to shut down your system.

---

### Post by Cypher on 2007-06-28
Do you shutdown using the proper Shutdown button and then letting the PC turn itself off? Also show the contents of your "/etc/fstab" file..

---

### Post by jonttix on 2007-06-28
I am shutting down properly with the button in the upper right corner!

My etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=7bdd0233-2b8d-453c-907d-2d2a43867ed3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0E4E-05CE  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=376B-10F3  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=696ca0df-e69e-4247-afd9-7f03c7952972 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by ajgreeny on 2007-06-28
If it really is the windows fat32 partitions being checked every bootup, then something is severely wrong.  Why do you think it is the windows partitions being checked?

I think also that the two lines in your fstab file shown here should end with a 0 not a 1.  Open the file as root, (gksudo gedit /etc/fstab) and change the lines to 0(zero) and save then see if it does the trick.
UUID=0E4E-05CE /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1

UUID=376B-10F3 /media/hda2 vfat defaults,utf8,umask=007,gid=46 0 1

Also worth checking your settings for the check with:-
sudo tune2fs -l /dev/hda1
The output from this will say near the bottom something like
Mount count:              6
Maximum mount count:      60
This shows my machine is set to check every 60 boots and was last checked 6 ago.  By default ubuntu sets 30 as the Max number but you can change that with:-
sudo tune2fs -c60 /dev/hda1
as I have, if you wish.

---

### Post by jonttix on 2007-06-28
I had wrong about the windows partition, it is the hda1 where it stops!

---

### Post by Cypher on 2007-06-28
Yes, as **ajgreeny** suggested, change the /dev/hda1 and /dev/hda2 entries to "0 0", as they are VFAT filesystem you don't want Linux doing anything with them short of mounting them..

---

### Post by ajgreeny on 2007-06-28
OK, the rest of my post still stands.

---

### Post by jonttix on 2007-06-28
I changed the 1 to 0 and it worked!! Thank you guys!!!

---

