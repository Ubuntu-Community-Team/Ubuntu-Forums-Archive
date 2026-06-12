---
title: "Need help with &quot;fdisk -l&quot; output"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by Luffield on 2005-10-21
Hi everyone,

After a few unsuccessful attempts to install Ubuntu on my computer's 30GB hard drive, on which Win2K is istalled, I decided to try installing it on my other hard drive, a 3GB one. Both Ubuntu and Win2K work fine now (had to change Win2K's hardware profile to ignore the other disk as it caused some problems, but I don't think it's relevant). Then I wanted to mount the Win2K disk on Ubuntu, and ran "sudo fdisk -l" in order to find out the name of that disk. The result looks like a hell of a mess to me, but frankly I don't know the first thing on this subject and I'm a bit worried about this output. Do I have a reason to worry? Should I go ahead and mount the disk, or try to fix something?

Thanks!

```
Disk /dev/hdc: 30.6 GB, 30606151680 bytes
255 heads, 63 sectors/track, 3720 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3719    29872836    7  HPFS/NTFS
/dev/hdc2            3720        3720        8032+  83  Linux

Disk /dev/hdd: 3249 MB, 3249340416 bytes
255 heads, 63 sectors/track, 395 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1          31      248976   83  Linux
/dev/hdd2              32         395     2923830    5  Extended
/dev/hdd5              32         395     2923798+  8e  Linux LVM

Disk /dev/sda: 131 MB, 131072000 bytes
5 heads, 50 sectors/track, 1024 cylinders
Units = cylinders of 250 * 512 = 128000 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?     7679804     9857553   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(7679803, 4, 9)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(9857552, 1, 1)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?     5320737     7476642   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(5320736, 4, 3)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(7476641, 4, 40)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?     2155958     7749410   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(2155957, 2, 42)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(7749409, 1, 3)
Partition 3 does not end on cylinder boundary.
/dev/sda4   *     5578511     5578596       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(5578510, 3, 14)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(5578595, 4, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by patrick295767 on 2005-10-21
Did you try : gparted or qtparted ?

Regards, 

patrick

---

### Post by Kyral on 2005-10-21
Whatever sda (Most likely a SATA drive), its partition table got really screwed up. I don't mean to sound accusing, but mind telling us what you have been doing on that drive?

---

### Post by Luffield on 2005-10-21
Patrick, I never heard about the commands you mentioned before. I'll try to read about them and try them. Thanks.

Kyral, it's alright, I didn't take it as an accusation and know that the problematic part in my system may well be the user :D

First, As far as I know there *isn't* any SATA drive on my computer. there are the 30GB and 3GB drives I mentioned before (and a CD drive). I don't know for sure because it's a used computer, but since it's pretty old - 1 GHz Pentium III - and since I know the guy who owned it before me, and he isn't a bleeding-edge kind of guy, so I really don't think any of these drives is a SATA one.

Now, what exactly did I do there...
Well, what I originally wanted to do was to install Ubuntu on the 30GB drive. I deleted some files and unistalled some programs in Win2K and ended up with just over 11GB of free space. I defraged the disk and almost all of that free space was contiguous. My intention was to use something like 6GB for Ubuntu+Home+swap.

When I ran the Ubuntu installation disk, for some reason it insisted that the EXT3 partition I was trying to make should be at least 8.2GB, and when I tried to change that value it went back to  "8.2GB" on the summay screen. I didn't want to give up so much disk space so I aborted the installation before the changes were written to the disk. or so I thought... :). I tried again with the same results.

Third time, same thing happens, but then I said "what the hell, I'll let it use 8.2GB" and went on with the installation. But the installaion failed - I can't remember what the error message was, but with what I know now I can only assume that the partitioning failed because that 30GB disk seems to have the original NTFS file system on almost all of it.

Then I moved all my files from the 3GB drive to the 30GB drive, and tired to install Ubuntu on the 3GB drive. I didn't think it was enough disk space, but it looks like Ubuntu is pretty happy with that and I still have over 900MB of free space on that drive.

One more thing - and don't know if it has anything to do with that problem or not - during the installation Ubuntu said it detected firewire on my computer and asked if I intend to use it for networking (I don't have a network card on that computer, it's on a diap-up modem). As far as I know, I don't have firewire. So it looks like that hardware detection on my computer was a bit problematic. Same happened with the Ubuntu 5.10 Live CD.

---

### Post by Jussi Kukkonen on 2005-10-21
[QUOTE=Luffield]After a few unsuccessful attempts to install Ubuntu on my computer's 30GB hard drive, on which Win2K is istalled, I decided to try installing it on my other hard drive, a 3GB one. 
...
Then I wanted to mount the Win2K disk on Ubuntu, and ran "sudo fdisk -l" in order to find out the name of that disk. The result looks like a hell of a mess to me, but frankly I don't know the first thing on this subject and I'm a bit worried about this output. Do I have a reason to worry? Should I go ahead and mount the disk, or try to fix something?
[/QUOTE]

Well, both the 30GB and 3GB disk look fine to me. If your question was should you mount */dev/hdc1*, I'd say try it. There is the odd ~8MB partition *hdc2*, which leads me to suspect that maybe you tried to install Ubuntu into 8MB, not 8GB?

The strange output for */dev/sda* is indeed ... strange. It could be a 128MB memory stick or a digital camera that had something bad happen to it: You wouldn't have anything like that connected?

---

### Post by Luffield on 2005-10-21
[QUOTE=Jussi Kukkonen]Well, both the 30GB and 3GB disk look fine to me. If your question was should you mount */dev/hdc1*, I'd say try it. There is the odd ~8MB partition *hdc2*, which leads me to suspect that maybe you tried to install Ubuntu into 8MB, not 8GB?[/QUOTE]

I honestly can't remember... But I'll go ahead and try mounting that 30GB hard drive, because I'm much more relaxed after I read this:
[QUOTE=Jussi Kukkonen]The strange output for */dev/sda* is indeed ... strange. It could be a 128MB memory stick or a digital camera that had something bad happen to it: You wouldn't have anything like that connected?[/QUOTE]

Oh yes I *did* have my 128MB memory stick connected! ](*,)
I ran "fdisk -l" again after unmounting it and all is well. The momory stick works fine, BTW, I don't think anything bad happened to it.

Thanks Jussi, your help is much appreciated. Thanks Kyral and Patrick for giving it a shot too :cool:

---

