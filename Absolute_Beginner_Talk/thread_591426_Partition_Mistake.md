---
title: "Partition Mistake"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by jkim588 on 2007-10-25
Hey.
I tried to Install ubuntu and I selected a certain amount of space. When I booted windows I only had 2gb left of mt 500gb hard drive. So I asked my friend what to do and he came over and deleted my partitions in the disk management of windows. Now when I restart I get Grub 17 error. 

I have no idea what to do. Im on the live cd right now. All I want is my space back on my windows partition and ubunutu to have 10 gb.

---

### Post by MegaJim on 2007-10-25
please post the output of 

```
sudo fdisk -l
``` from the command line

---

### Post by jkim588 on 2007-10-25
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


?

---

### Post by MegaJim on 2007-10-25
That is an excerpt from the standard help text.

Please make sure you type in** exactly** this:

```
sudo fdisk** -l**
```

"**-l**" is a **lower case L**, not the number one.

---

### Post by logos34 on 2007-10-25
Do you have an XP install CD?

---

### Post by jkim588 on 2007-10-27
Disk /dev/hda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f1f5f1f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23601   189575001    7  HPFS/NTFS
/dev/hda2           60046       60801     6072570    5  Extended

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aac2aab

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       48640   390700768+   7  HPFS/NTFS



I do have a XP boot but its in iso format on 1 partition

---

### Post by meierfra on 2007-10-27
You will have to fix the MBR. Since you don't have the WIndows CD available I recommend [ Supergrub]("http://supergrub.forjamari.linex.org/"). 

For information on subergrub see [ Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by jkim588 on 2007-10-27
is it still possible to get my partition back to windows?

for example instead of having 180 for ubuntu, make it have around 15 and the rest goes back to windows?

---

### Post by meierfra on 2007-10-27
Yes, but  if you  want Ubuntu  your will have to reinstall it (Your friend deleted it.) 
Reinstalling Ubuntu will also solve your boot problem.

---

### Post by jkim588 on 2007-10-27
I just checked my partitions on the live cd and windows has 194 of 195 free and there is 300 gbs of free space. I'd like to put the 300 back into windows.

---

### Post by sneezymelon on 2007-10-27
Use GNOME Partition Manager in from the live CD. It's simple to use and you can resize partitions according to your will. After that, reinstall Ubuntu and that will automatically bring back the grub

---

### Post by sneezymelon on 2007-10-27
umm...sorry, it's the GNOME Parition "Editor"

---

### Post by jkim588 on 2007-10-27
I treid that but it doens let me put it back to the partition. it says unallocated space or something. I am doing this while im in the instialled ubuntu. 

I just wanted to thank you guys for the help! I really appericate it.

---

### Post by jkim588 on 2007-10-27
I also tried to run PCLinuxOS and that partition didnt work either. When I try to resize it the space doesnt go any further then what it already is

---

### Post by pdlethbridge on 2007-10-27
If you can't resize the XP, add a ntfs partition of 300 gig. XP will see that and it should work fine

---

### Post by jkim588 on 2007-10-28
I made another partition in NTFS and I cant put it back into my hard drive. I can use it as 2 on my pc but thats kind of sloppy. Well, if thats the only way I guess It will have to do. Thanks for your help

---

