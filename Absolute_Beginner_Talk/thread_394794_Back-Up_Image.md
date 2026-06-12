---
title: "Back-Up Image"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by zuesko on 2007-03-27
Hi Guys,
Can anyone suggest a stable image backup programe.

I used R-Drive image to back up my HD under windows but I do not have Windows Installed.
R-Drive does not work under Ubuntu 6.06

Thanks to everyone in advance who can help.:confused:

---

### Post by compmodder26 on 2007-03-27
Never used it before, but I hear partimage is great.  It's in the repositories.

---

### Post by aysiu on 2007-03-27
I'd recommend PartImage, but there other options.

Read more here:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by zuesko on 2007-03-30
Hi compmodder26,
Thanks for pointing me in the right direction

---

### Post by zuesko on 2007-03-30
Hi aysiu,

Thanks for the link. I was able to download and burn SystemRescueCd and it works fine.
Just the operator.From a windows environment and not a tech everything was point and click.
I have read all how to's and still only come up with how not's.
This is what I have:

Disk /dev/hda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1190     9558643+  83  Linux
/dev/hda2            1191        1245      441787+   5  Extended
/dev/hda5            1191        1245      441756   82  Linux swap / Solaris

Disk /dev/hdb: 8622 MB, 8622931968 bytes
255 heads, 63 sectors/track, 1048 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1048     8418028+  83  Linux

With my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /storage	ext3    defaults	0	0

So I have a permanent mount point /storage on my slave.
The 64 million dollar question is how do I copy /dev/hda1(my ubuntu install) to  
/dev/hdb1/storage/rescue:     :confused: /rescue is the dir I created.
Ihave tried to mount everything, including the kitchen sink, but all I get is error messages.
If you could step it out for me I would be most grateful. Remember to KISS, you are not dealing with a rocket scientist.
Cheers:confused:

---

