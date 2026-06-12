---
title: "Another dual boot question"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by rancid98 on 2007-05-25
I have installed ubuntu on a 160gb drive on my PC.  I set up a dual boot as in the thread [http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902").  The windows slave drive has a partition thanks to HP which is for system recovery.  When I start the PC now, everything works exactly as desired when I boot to ubuntu.  If I let it boot to Windows, it boots into the recovery system and not the normal windows bootup.  I expect is something to do with the map entries put into menu.lst file, but not being a programmer, I don't know what to change it to.

Thanks for any help.  Personally, I wouldn't care if I could never get into Windows again, but the rest of my family would want to tear me a new one:(

---

### Post by bodhi.zazen on 2007-05-25
Well, you do not need to be a programmer to fix that. Configuring an OS is not the same as programing ...

[end rant]

The fix should be easy, you will need to edit /boot/grub/menu.lst

post the output of this command : ```
sudo fdisk -l
```

Note: that is a small "L" and not the number 1

---

### Post by rancid98 on 2007-05-25
Thanks.  I guess I'm displaying my complete ignorance - the configuration of the OS looked liked programming to me:confused:  Hopefully after a couple of weeks I might know what I'm talking about.

Ok..I typed in the command and got:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19269   154778211   83  Linux
/dev/sda2           19270       19457     1510110    5  Extended
/dev/sda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         568     4294048+   b  W95 FAT32
/dev/sdb2   *         569        5168    34776000    7  HPFS/NTFS


Hope that helps.

---

### Post by dstew on 2007-05-25
It looks like /dev/sdb1 might be the recovery partition. If so, we only need to change your grub menu.lst file to boot the proper partition, which seems to be /dev/sdb2. You can change the partition number from the grub menu temporarily to test it, by entering 'e'. If you want more specific directions, post the output of the following command to the forum```
cat boot/grub/menu.lst
```

---

### Post by rancid98 on 2007-05-25
Geeze I'm sorry.  I know I'm probably missing the most basic things.  I typed in the code and got this:
cat boot/grub/menu.lst
cat: boot/grub/menu.lst: No such file or directory
brad@IrwinPC:/boot/grub$ 

Is there somewhere I can read about this and perhaps learn something rather than annoy you guys, and learn by working it out which always makes for good experience?  I've searched the forum under the terms "map" and "menu.lst" without getting any helpful threads.  I do not want to be a member of this forum that asks questions that I could have the answer to if I spent 5mins reading documentation or help files or something.

---

### Post by bodhi.zazen on 2007-05-25
Open a terminal.

Enter this command :

```
gksudo gedit /boot/grub/menu.lst
```

Look for this section :

> title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

And change it to :

> title              Windows XP
root               [color=red]**(hd1,1)[/color]**
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

> Geeze I'm sorry. I know I'm probably missing the most basic things. I typed in the code and got this:
cat boot/grub/menu.lst
cat: boot/grub/menu.lst: No such file or directory
brad@IrwinPC:/boot/grub$ 

:lolflag:

boot/grub/menu.lst is not the same as /boot/grub/menu.lst (note the initial / in the second)


> Is there somewhere I can read about this and perhaps learn something rather than annoy you guys, and learn by working it out which always makes for good experience?

:lolflag:

We like to be annoyed.

There are many, many guides out there. Stay with it and it will become much easier over time but give yourself a few weeks or months and in the mean time feel free to ask all the questions you have.

Welcome to Ubuntu.

---

### Post by bodhi.zazen on 2007-05-25
Duplicate post

---

### Post by rancid98 on 2007-05-25
Thanks:redface:

---

### Post by Carlos Santiago on 2007-05-25
From the size of the partitions, your recovery partition is sdb2 and the normal windows partition is sdb1.
And you are booting to sdb2.

So, in the boot/grub/menu.lst file you must change

sdb2 to sdb1

or,

(hd1,1) to (hd1,0)

That should do!

---

### Post by bodhi.zazen on 2007-05-25
> **Carlos Santiago said:**
> From the size of the partitions, your recovery partition is sdb2 and the normal windows partition is sdb1.
And you are booting to sdb2.

So, in the boot/grub/menu.lst file you must change

sdb2 to sdb1

or,

(hd1,1) to (hd1,0)

That should do!

Hi Carlos :)

FYI, just for education :

1. With windows we chainload so there is no kernel line like when we boot Linux so no sdb1 or sdb2 (grub uses (hdx,y)

2. We know the partition to boot from the fdisk command via the *

> Device **Boot** Start End Blocks Id System
/dev/sdb1 1 568 4294048+ b W95 FAT32
/dev/sdb2 [color=red]*****[/color] 569 5168 34776000 7 HPFS/NTFS

The * flags the partition as bootable (in the "boot" column)

also sdb2 is > sdb1 and sdb2 is NTFS, the defalut for windows ...

---

