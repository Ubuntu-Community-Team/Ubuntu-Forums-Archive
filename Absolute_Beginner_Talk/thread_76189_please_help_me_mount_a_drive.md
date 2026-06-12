---
title: "please help me mount a drive"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2005-10-14
I have a computer that is dual booting xp and ubuntu 5.10. I have 2 drives and 4 partitions. I have mounted the windows partition. I have a 160 gig ntfs drive I would like to mount. how would I go about this. 


see my failed attempts [http://www.ubuntuforums.org/showthread.php?t=75966](http://www.ubuntuforums.org/showthread.php?t=75966)

---

### Post by musicman2059 on 2005-10-14
How many partitions are there on each drive (2 drives and 4 partitions is kind of hard to picture as there are so many variations of it) and which one is your Windows partition?

---

### Post by John.Michael.Kane on 2005-10-14
Try this [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

hope it helps

---

### Post by onesojourner on 2005-10-14
[QUOTE=musicman2059]How many partitions are there on each drive (2 drives and 4 partitions is kind of hard to picture as there are so many variations of it) and which one is your Windows partition?[/QUOTE]

I have a 100gig drive with 3 partitions one with windows one with ubuntu and one for storage. the 160 gig is a single partition. 

SD-Plissken thanks for the link. I will read it over and see if it helps.

---

### Post by brentoboy on 2005-10-14
mounting ntfs is not 100% reliable. (that's becuase it is 100% proprietary)
You can mount it read only without issues, but read/write might be a litte bit "beta" - ntfs is complicated, and the only way to make linux see it is trial and error.  Resizing files is not always perfetly safe.

anyway.  in synaptic, there is a package called ntfsprogs. that might help.

you can mount it like any other drive (you need to know the name of the partition like: /dev/hda1 or something)  using the mount command.

you have to mount it to an existing folder, the right place to put it is in the /media folder. make a subfolder in there called win-c or something like that

# sudo mkdir /media/win-c

that makes the folder that you will end up using as the base folder for your windows C drive

then, to mount it... run this command
# sudo mount /dev/hda1 /media/win-c
Actually that command wont work, becuase you will need to specify the parameters that tell it exactly what you want mounted.

use "man" to read the manual about mounting:

# man mount

the man page is huge, but that is becuase there is so much that potentially could be done.

sorry I know just enough to get you started, not enough to walk you through it - anyone with more experience care to chime in and correct my seriously mixed up "help"

---

### Post by SilentCacophony on 2005-10-14
[QUOTE=onesojourner]peter@peterLinux:~$ fdisk -l

Disk /dev/sda: 524 MB, 524025856 bytes
17 heads, 59 sectors/track, 1020 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/sda1 ? 775809 1913904 570754815+ 72 Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(357, 116, 40) logical=(775808, 8, 13)
Partition 1 has different physical/logical endings:
phys=(357, 32, 45) logical=(1913903, 14, 4)
Partition 1 does not end on cylinder boundary.
/dev/sda2 ? 168185 2098423 968014120 65 Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
phys=(288, 115, 43) logical=(168184, 16, 27)
Partition 2 has different physical/logical endings:
phys=(367, 114, 50) logical=(2098422, 8, 24)
Partition 2 does not end on cylinder boundary.
/dev/sda3 ? 1864289 3794527 968014096 79 Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
phys=(366, 32, 33) logical=(1864288, 10, 12)
Partition 3 has different physical/logical endings:
phys=(357, 32, 43) logical=(3794526, 1, 20)
Partition 3 does not end on cylinder boundary.
/dev/sda4 ? 1 3626348 1818613248 d Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
phys=(0, 10, 0) logical=(3626347, 7, 42)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order[/QUOTE]

I find that odd in two ways:

1) You should have to ***sudo* fdisk -l** to get any output at all, in my experience. Really odd.

2) That's a complete mess! I've never seen anything like that. I would think that the partition tables are completely messed up, looking at that. Hopefully not.

Maybe try fdisk with **sudo**, if you hadn't before.

Also, it may help to see the output of:

**df -h**

---

### Post by musicman2059 on 2005-10-14
[QUOTE=onesojourner]I have a 100gig drive with 3 partitions one with windows one with ubuntu and one for storage. the 160 gig is a single partition. 

SD-Plissken thanks for the link. I will read it over and see if it helps.[/QUOTE]

Try using the mount command again, but with /dev/hdb1, with the help of the other people so far.  (this is pretty much all I know, though.)

---

### Post by onesojourner on 2005-10-14
Ok I will try all this. 

musicman2059 where are you getting the hdb1?

---

### Post by onesojourner on 2005-10-16
Thank you guys so much. I found all my partitions. :D  now I get to start getting into more trouble. I hope you guys are ready to answer some more dumb questions...:rolleyes:

---

