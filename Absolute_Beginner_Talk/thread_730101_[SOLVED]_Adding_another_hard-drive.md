---
title: "[SOLVED] Adding another hard-drive"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by jjbro on 2008-03-20
New to Linux - appreciate some help with a problem that is bugging me right now.
Just finished installing xUbuntu on my PC, I have abandoned Windows totally, so no dual-boot issues here.

My initial xUbuntu installation was done on a 40 Gb harddrive.
It is partioned as follows (Gnome Partition Editor - info):
Partition         Filesystem Mountpoint Size              Used          Unused         Flags
/dev/sda1      ext3             /boot            243,14 MiB 53,71 MiB  184,43 MiB   boot
/dev/sda2      extended                          37,03 Gib    ---                ---
     /dev/sda5 linux-swap                        1,44 Mib      ---                ---
     /dev/sda6 unknown                           35,59 Gib    ---                ---                  lvm

After the initial installation, I chose to add a 200 Gb harddrive, installed as a slave.
Partition         Filesystem Mountpoint   Size              Used        Unused         Flags
/dev/sdb1      ext2             /media/disk  184,87 GiB  2,90 GiB  181,97 GiB   boot
/dev/sdb2      extended                            1,44 Gib      ---              ---
     /dev/sdb5 unknown                            1,44 Gib       ---              ---                  lvm

xUbuntu mounts the second drive as it should. However, I thought that Linux wasn't oriented towards drives like Windows. I thought Linux used volumes/folders that could have underlying several physical harddrives.
So based on this I am trying to get the second harddrive integrated into the first, to be seen as a single volume/folders.

So my questions are:
1. how to "melt" the second harddrive together with the first?
2. how to make sure that filesystem ext3 is used on both?

:confused:

---

### Post by Therion on 2008-03-20
If I understand you correctly, you have two hard drives on your system now; the 40GB Master and the 200GB Slave.  Both volumes mount individually, as they should, but you want Ubuntu to "see" them both as a single 240GB drive?  If that's what you want, I'll be watching this thread closely because I don't think you can do that.  IF you can, I certainly don't know how.

---

### Post by jjbro on 2008-03-20
Yes - this is exactly what I would like to be able to do.:)

---

### Post by stchman on 2008-03-20
> **jjbro said:**
> New to Linux - appreciate some help with a problem that is bugging me right now.
Just finished installing xUbuntu on my PC, I have abandoned Windows totally, so no dual-boot issues here.

My initial xUbuntu installation was done on a 40 Gb harddrive.
It is partioned as follows (Gnome Partition Editor - info):
Partition         Filesystem Mountpoint Size              Used          Unused         Flags
/dev/sda1      ext3             /boot            243,14 MiB 53,71 MiB  184,43 MiB   boot
/dev/sda2      extended                          37,03 Gib    ---                ---
     /dev/sda5 linux-swap                        1,44 Mib      ---                ---
     /dev/sda6 unknown                           35,59 Gib    ---                ---                  lvm

After the initial installation, I chose to add a 200 Gb harddrive, installed as a slave.
Partition         Filesystem Mountpoint   Size              Used        Unused         Flags
/dev/sdb1      ext2             /media/disk  184,87 GiB  2,90 GiB  181,97 GiB   boot
/dev/sdb2      extended                            1,44 Gib      ---              ---
     /dev/sdb5 unknown                            1,44 Gib       ---              ---                  lvm

xUbuntu mounts the second drive as it should. However, I thought that Linux wasn't oriented towards drives like Windows. I thought Linux used volumes/folders that could have underlying several physical harddrives.
So based on this I am trying to get the second harddrive integrated into the first, to be seen as a single volume/folders.

So my questions are:
1. how to "melt" the second harddrive together with the first?
2. how to make sure that filesystem ext3 is used on both?

:confused:

I don't believe there is a way to do what you want.  Remember Linux give designations to physical hdds like hda, hdb, hdc, etc. or sda, sdb, sdc, etc. for SATA.

Then each partition has a number associated like hda1, hda2, etc.

---

### Post by ELF_O8 on 2008-03-20
the easy part of this problem is to ensure the ext3 filesystem integrity.
just open Gparted and format as such.

as for the merging, I would advise against such an action.
it does not yeild good performance on the host machine.
moreover it requires RAID, which you should also avoid.
the process of 'melting' as you put it wipes both disks as well.

---

### Post by Bright Hammer on 2008-03-20
What you are asking is possible but trick for a novice if you are doing this on your main box and don&#8217;t want to lose data. Here is a link that can help. 

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

My suggestion is to try it on test box first so you get comfortable with LVM.


Here is another link that can help. [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

Just be careful when working with LVM because it is not for beginners.

---

### Post by halitech on 2008-03-20
you could always use a mount point for the slave drive as something like 
```

/home/{username}/data

```

to make it seem like you have a single drive but to physically make them 1 drive, I can't see any way of doing that.

---

