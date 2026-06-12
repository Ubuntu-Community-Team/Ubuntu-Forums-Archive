---
title: "cant boot mac"
date: 2008-12-10
forum: Apple Hardware Users
---

### Post by cysilver on 2008-12-10
i have a new mac intel based and i installed ubuntu with bootcamp.
when i restarted the computer i didnt saw the boot for mac and now i cant go to mac os :S
i didnt erase the mac os drive
is there a way to boot the mac again?

help me plz

---

### Post by aysiu on 2008-12-10
When you're booted into Ubuntu, can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
sudo fdisk -l
```

---

### Post by cysilver on 2008-12-10
't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156290903+  ee  GPT

---

### Post by aysiu on 2008-12-10
Yeah. Looks as if you wiped out OS X completely.

---

### Post by cysilver on 2008-12-10
but in linux i can see the mac hdd drive
:S

---

### Post by pxwpxw on 2008-12-10
> **aysiu said:**
> Yeah. Looks as if you wiped out OS X completely.

No no, that is just the MBR, everything is still there. The usual effect is failure to load grub and linux, and the cure is to run the refit partiton tool to sync the mbr.

---

### Post by cysilver on 2008-12-10
how can i do that? plz help me i dont want to lose my data on mac :S

---

### Post by pxwpxw on 2008-12-10
Have you got rEFIt?

---

### Post by cysilver on 2008-12-10
yeah but i cant access mac

---

### Post by cysilver on 2008-12-10
my mac is a intel based :S

---

### Post by pxwpxw on 2008-12-10
Are you using the ubuntu Desktop CD now, or what?

You can download refit in ubuntu and run gptsync.
But it shoud not stop you from booting macosx.
First try restarting while pressing 4 keys command-option-P-R
That might reset so Macosx starts.
Also the Macosx install DVD would be another way tocheck what happened.

---

### Post by pxwpxw on 2008-12-10
If you have the Macosx install DVD, you can use that to set the startup disk to your Macosx, that may be it.

---

### Post by cyberdork33 on 2008-12-11
> **aysiu said:**
> When you're booted into Ubuntu, can you paste this command into [the terminal]("http://www.psychocats.net/ubuntu/terminal") and then post the output back here? ```
sudo fdisk -l
```

fdisk does not support GPT formatted hard drives such as those found in Intel Macs. It can only read the MBR partition table. parted does support gpt though:
```
sudo parted /dev/sda print
```would list the partitions correctly.

---

### Post by cysilver on 2008-12-12
sorry for bothering you guys but i needed the computer fast and i gain the data from the mac dvd install disk but i lost lots of data but thx alot

---

