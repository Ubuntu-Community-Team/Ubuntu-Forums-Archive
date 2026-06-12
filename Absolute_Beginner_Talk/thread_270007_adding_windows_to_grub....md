---
title: "adding windows to grub..."
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by rabid9797 on 2006-10-02
i know its been done before, but i can't seem to find a straight from scratch configuration example of waht windows should look like in the menu.lst for grub.

right now i have a windows partition on my first hardrive, 5th partition(hda5)

and one on my second hardrive, 6th partition(hdb6)

my windows mbr is on the first hardrive...


so what entry would i put in grub so i can boot those partitions?

---

### Post by divague on 2006-10-02
title		Microsoft Windows XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1


title		Microsoft Windows XP
root		(hd1,5)
savedefault
makeactive
chainloader	+1

---

### Post by rabid9797 on 2006-10-02
did not work =/

i was reading some stuff on the internet, is there a problem with one of the partitions not being the primary?

i was looking here: [http://www.linuxquestions.org/questions/showthread.php?t=375198](http://www.linuxquestions.org/questions/showthread.php?t=375198)

also, i found this off another website, and i when i boot with it, i get a "NTDLR boot was not found"

title WinXP pro 3 Disks
map (hd0) (hd1)
map (hd1) (hd2)
map (hd2) (hd0)
rootnoverify (hd2,0)
chainloader +1
makeactive
boot

can i use that nad just change stuff around till it works?

---

### Post by bulldog on 2006-10-02
You have to keep in mind that the boot records of windows need to be on a primary partition.

If you put windows in an extended partition there should be a FAT32 or NTFS primary to be the first partition on that disk.

can you give the outcome of```
sudo fdisk -l 
```

---

### Post by rabid9797 on 2006-10-02
sure

```

Disk /dev/hda: 61.4 GB, 61475807232 bytes
240 heads, 63 sectors/track, 7941 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         697     5269288+   b  W95 FAT32
/dev/hda2             698        7940    54757080    f  W95 Ext'd (LBA)
/dev/hda5             698        7940    54757048+   7  HPFS/NTFS

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2             132        3648    28250302+   f  W95 Ext'd (LBA)
/dev/hdb5             263        3648    27198013+   7  HPFS/NTFS

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       27403   220114566   83  Linux
/dev/hdd2           27404       30251    22876560   83  Linux
/dev/hdd3           30252       30401     1204875   82  Linux swap / Solaris
rabid9797@rabid9797-ubuntu:~$
```

---

### Post by rabid9797 on 2006-10-02
bump

---

### Post by rabid9797 on 2006-10-02
re-bump

i really need an answer here.

---

### Post by pay on 2006-10-02
title Microsoft Windows XP
root (hd0,5)
savedefault
makeactive
chainloader +1

title Microsoft Windows XP
root (hd1,6)
savedefault
makeactive
chainloader +1

Try that. I think that Grub uses 0 for your hda device and 1 for your hdb device etc but uses 1 for your 1st partition etc. I could be/most likely wrong though.

---

### Post by jaboua on 2006-10-02
Yeah it counts from 0 in partitions too - (hd0,0) is hda1, (hd1,1) is hdb2 etc

---

### Post by pay on 2006-10-02
Thanks for clearing that up for me.

---

### Post by rabid9797 on 2006-10-02
thanks, i'll try that out.

---

### Post by rabid9797 on 2006-10-03
no luck, can anyone else help me?

---

### Post by pay on 2006-10-03
Does this work?

title Microsoft Windows XP
root (hd0,4)
savedefault
makeactive
chainloader +1

title Microsoft Windows XP
root (hd1,5)
savedefault
makeactive
chainloader +1

---

### Post by rabid9797 on 2006-10-05
no, i just get an "invalid device selected" error after makeactive is ran

---

### Post by bulldog on 2006-10-05
I think it should point at (hd0,0) not at the partition windows is.

Your windows start by reading startup info on the first NTFS partition.

Did you try,```
sudo upgrade-grub
```to see if GRUB can do it by itself?

---

### Post by duan on 2006-10-05
Silly question but how is your BIOS set to boot?
I have two disks ubuntu on the 1st and windows on the second.
windows is on the first partition of my second disk. there is no grub there  it was a pure windows install in the absence of the linux disk.

My BIOS is set to boot from the second disc first. grub is installed there and it will give the bootmenu. if this disc is removed windows still boots.

For some reason windows needs to think it is on the first drive otherwise it won't boot.

to boot your second disk's windows the disk needs to be remapped to look like it is the first, then grub just bumps the boot over to that disk.

here's what my menu.lst looks like:

<first linux stuff here>
title           Windows XP
#windows is on the second disk. I found it easier to hack grub than mtab.
rootnoverify            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader     +1
boot

You would still need to sort out booting from the correct partition. But I understand that it will not boot at all if not remapped. That's what happended to me.

---

### Post by rabid9797 on 2006-10-05
ok, so if on my second partition windows is at hd1,4, where would i stick that in the list you got there?

---

### Post by duan on 2006-10-06
make that line:
rootnoverify (hd1,4)

- if you can actually boot from the second disk( if you unplug the first.)
I mean, if you can't boot of the second disk then there's no us in this. 

This was why I'm asking how your BIOS is set.

It is quick to adjust your BIOS, and see if you can boot from your second disk. You might find that it boots just straight into that windows. Then this would be the way to boot from your second disk.

---

### Post by rabid9797 on 2006-10-06
ah, i never thought about doing that. i'll try it out.

---

