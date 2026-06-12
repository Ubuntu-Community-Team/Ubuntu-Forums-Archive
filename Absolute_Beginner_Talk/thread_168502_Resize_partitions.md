---
title: "Resize partitions"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by TheTux on 2006-04-30
how do u guys manage ur partitions??i have 2 partitions.. root and /home partitions...4.9gb for / and 1gb for home...and i think i should give more space to home partition...how to resize root partition so i can give some space to home partition....is it safe to resize partition...will it affects grub??bcos b4 this i've tried to format my vfat partition and give it to root partition and afterthat i was not able to boot...i used installation cd to restore grub but i could not..so i installed back my ubuntu...pls help bcos i don't want to lose my installation again

this is my fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        4831    23446867+   f  W95 Ext'd (LBA)
/dev/hda4            4832        4864      265072+  82  Linux swap / Solaris
/dev/hda5            1913        4079    17406396    7  HPFS/NTFS
/dev/hda6            4712        4831      963868+  83  Linux
/dev/hda7            4080        4711     5076508+  83  Linux

can i resize them using partition magic? and if resized them...will the partition numbers change?i mean like hda7 turn to hda8..

---

### Post by AnRuaRi on 2006-04-30
DONT DONT DONT use Partition Tragic (oops did I say that?)

There are lots of more suitable partition editors available for the Linux file systems.

any partition re-size runs the risk of trashing all your data so make sure you've backed up fully first.

GParted is in the Ubuntu Repositories. you can install it using your prefered Graphical tool if you like. I have used this and find it's quite easy to use.

if this is already installed it will be in

Applications -> System Tools -> GParted

I'd be VERY carefull about resizing partitions which have NTFS partitions mixed in with the others.

Personally I use 2 separate hard drives. these are prety cheap these days. I have one for windows, (30GB) and one for Linux (200GB) this latter ahs both a Linux SWAP, and a NTFS partition which is used as a dedicated windows swap. (this massivly reduces fragmentation)

---

