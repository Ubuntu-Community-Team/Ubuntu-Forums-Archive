---
title: "[SOLVED] Ubuntu 7.04 on internal (ext3), NTFS on External - issues"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by sekelly on 2007-07-31
Hey all,

Just wanted to start off by saying I've only been using ubuntu for approximately 2 days, so please bare with me as I'm sure most of my questions will be incredibly newbish. 

I recently decided to make the jump from Windows to Ubuntu. On my old Windows machine, I had 2 drives, a 160 Gb WD Internal, and a 320 Gb Seagate External. 

Before making the jump I moved all of my files that I wanted to keep (pictures, music, docs, etc.) over to my Storage Drive, the 320 Gb External.

I was reading on here that in order for ubuntu to write to ntfs (I have no problem reading, I have been using my ntfs drive to play my mp3's for the last couple days) you need to install ntfs-3g.

I have installed the package from add/remove and I opened it up after, enabled writing on my external drive, and closed it. I then tried to save an .otd file to my ntfs file system, and got a couple errors.

1st Error:

Error saving Document entitled Untitled1:media\storage\test.odt does not exist

and my 2nd error

Error saving the document Untitled1
General Error
General Input/Output Error

I am not sure if I simply need to reboot or if there is some other dependency I need to install (I've done some reading but I'm not entirely sure how dependencies work other than they are required, I'm just not sure how to determine if a program has dependencies.)

I thank anyone who is able to help me in advance.

P.S. Sorry if the post is too long, I just wanted to make sure I explained everything fully.

---

### Post by nitro_n2o on 2007-07-31
what is the output of ```
sudo fdisk -l
``` I'm not sure what u've installed from synaptic, but the one that works fine is the "NTFS configuration tool"

---

### Post by sekelly on 2007-07-31
the output is 

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18700   150207718+  83  Linux
/dev/hda2           18701       19457     6080602+   5  Extended
/dev/hda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

I did a restart and it appears to be working now. I'm not sure what the problem was.

I am using NTFS Configuration Tool (aka ntfs-3g)

Sorry, I'll mark as solved. Thanks for the reply.

---

