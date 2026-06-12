---
title: "Can't boot from xp partition nor my xp cd"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by h_howee on 2007-09-28
I've read other threads but I couldn't find a solution that works

first of all, booting from the CD:
[LIST]
[*]The boot order is as follows
[LIST]
[*]Floppy
[*]CD/DVD Drive
[*]HDD
[*]Network Group
[/LIST]
[/LIST]
I checked the boot order
I tried disabling all but CD drive
the cd works on another comp si I know it has nothing to do with the cd
i tried using other CDs with the drive and they work so there's nothing wrong with the CD drive either
tried installling XP with Wine but it crashes

Booting from the XP partition:
I still have all the Windows files from before I installed Ubuntu
I tried appending this to the end of the menu.lst file
```

title           Microsoft Windows XP 0 0
root            (hd0, 4)
savedefault
makeactive
chainloader +1

```
and everything from (hd0, 0) to (hd0, 5)
but I get an error when I try to boot it (I'll edit this post when I get the exact error message)

I've noticed that in most threads, the OP was asked for the output of sudo fdisk -l so here it is
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         967     7302960    5  Extended
/dev/sda2   *         968        2259     9767520   82  Linux swap / Solaris
/dev/sda3            2260       25840   178272360   83  Linux
/dev/sda5               2         967     7302928+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)

```

IDK if this would help or not but the directory with the Windows files is /media/sda5

How should I go about getting XP back?

---

### Post by h_howee on 2007-09-28
idk if bumping is against the forum rules or not but this thread went to the 2nd page in half an hour with only 2 views

---

### Post by bodhi.zazen on 2007-09-28
The grub entry for windows XP should be :

> title           Microsoft Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader +1

Note, no space in (hd0,4)

Other then that, please post the error message, that is most helpful

---

### Post by h_howee on 2007-09-28
idk if bumping is against the forum rules or not but this thread went to the 2nd page in half an hour with only 2 views

[edit]
my internet keeps disconnecting...
the error was
```
Error 11: Unrecognized device string
```

after removing the space, it turned into
```
Error 12: Invalid device request
```
[/edit]

---

### Post by Pumalite on 2007-09-28
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, burn to CD, boot from, program)
Boot from it.
Remove the bootflag from sda2 and place it in sda5

---

### Post by h_howee on 2007-09-28
> Remove the bootflag from sda2 and place it in sda5
Done. Now what?

---

### Post by Pumalite on 2007-09-28
I hope you have edited your menu.lst and done what bohdi.zazen suggested.

---

### Post by h_howee on 2007-09-28
I did

I now have
```

title           Microsoft Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader +1

```

and sudo fdisk -l gives
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         967     7302960    5  Extended
/dev/sda2             968        2259     9767520   82  Linux swap / Solaris
/dev/sda3            2260       25840   178272360   83  Linux
**/dev/sda5   *           2         967     7302928+   7  HPFS/NTFS**

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)

```

It still gives error 12 when i select Microsoft Windows XP

---

### Post by Pumalite on 2007-09-28
You probably have Windows installed in a logical partition. Windows can only function  in a primary partition, and it likes to be sda1.

---

### Post by bodhi.zazen on 2007-09-28
Ah, I see the problem ...

Windows does not like to be on an an extended partition, at least last time I looked ....

Windows wants to be on a primary partition.

So, with gparted, you will have to make a new primary partition and move windows onto it. If you downloaded the latest version of Gparted you can copy-paste partitions ...

[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

See how helpful those error messages are ? :twisted:

Edit: Beaten by Pumalite :redface:

---

### Post by h_howee on 2007-09-29
When i open gParted, it shows something like

[list]
[B][*]sda1
[list]
[*]sda5[/B]
[/list]
[*]sda2
[*]sda3
[/list]

What's that supposed to mean?

and where do the screenshots go when you click the screen shot icon?

---

### Post by bodhi.zazen on 2007-09-29
> **h_howee said:**
> When i open gParted, it shows something like

[list]
[B][*]sda1
[list]
[*]sda5[/B]
[/list]
[*]sda2
[*]sda3
[/list]

What's that supposed to mean?

and where do the screenshots go when you click the screen shot icon?

I assume that means sda5 is an extended partition ...

I do not know off the top of my head where to find screnshots. /home/<username> or /root

---

