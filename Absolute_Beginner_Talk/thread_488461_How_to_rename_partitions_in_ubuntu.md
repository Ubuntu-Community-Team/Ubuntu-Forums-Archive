---
title: "How to rename partitions in ubuntu"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by newoldboy on 2007-06-30
I have a windows partition that is shown as 'disk'. How can I rename it in ubuntu.

---

### Post by alienexplorers on 2007-06-30
You can rename it and just make sure in your fstab file you also change the name or the partition will not be useable.

---

### Post by newoldboy on 2007-06-30
Sorry, I failed to mention I am very new to linux. I am not familiar with commands. Is there a way to do it with gnome partition manager.

---

### Post by mikewhatever on 2007-06-30
First, can you please post the output of the following command 
> sudo cat /etc/fstab

---

### Post by newoldboy on 2007-06-30
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=154642ce-a217-41c2-9428-a74abc49ff71 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3cb4089e-3043-4d79-993a-7d699750d5e9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by mikewhatever on 2007-06-30
> I have a windows partition that is shown as 'disk'. How can I rename it in ubuntu.
Can you clarify, where is that 'disk' partition? According the your fstab, the Windows partition, assuming it is /dev/hda1, is not auto mounted.

---

### Post by newoldboy on 2007-06-30
My windows partition is on the C drive, which is as far as i know where the ubuntu file are too.

---

### Post by ugm6hr on 2007-06-30
It's a lot easier to rename it in Windows (e.g. as *Windows).*  It will then appear as /media/Windows in Ubuntu (that's what I did).

---

### Post by newoldboy on 2007-06-30
thanks, i will try that

---

### Post by ambush_xx on 2007-06-30
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)

you can edit fstab and add an entry to auto mount your windows partition in a new directory

---

### Post by mikewhatever on 2007-06-30
> **newoldboy said:**
> My windows partition is on the C drive, which is as far as i know where the ubuntu file are too.

Not according to the fstab you posted. You Ubuntu partition is /dev/hda5 and the Windows partition is most probably /dev/hda1, but as you can see, it is not there. In you initial post, you were talking about Windows partition being called 'disk'. One again, let me ask it, where exactly do you see the 'disk' partition.
> It's a lot easier to rename it in Windows (e.g. as Windows). It will then appear as /media/Windows in Ubuntu (that's what I did).
I am almost certain you can not rename the c:\ partition in Windows.

---

### Post by ugm6hr on 2007-06-30
> **mikewhatever said:**
> I am almost certain you can not rename the c:\ partition in Windows.

Sure you can.  Open "My Computer" - Right Click "C:\" and select "Rename" - Type whatever you want ("WINDOWS" in my case) - press return.

Shame I can't do screenshots in Windows.

Having done that, if you want to auto-mount the partition - follow instructions in the psychocats tutorial.

---

### Post by mikewhatever on 2007-06-30
> **ugm6hr said:**
> Sure you can.  Open "My Computer" - Right Click "C:\" and select "Rename" - Type whatever you want ("WINDOWS" in my case) - press return.

Shame I can't do screenshots in Windows

So, in that case, what would it be called, Windows:\? For screenshots, try Alt+Prnt Scr.

---

### Post by ugm6hr on 2007-06-30
> **mikewhatever said:**
> So, in that case, what would it be called, Windows:\? For screenshots, try Alt+Prnt Scr.
I think you have misunderstood.  I realise you can't change the mountpoint (is that what Windows calls it - essentially the drive letter C:\) of the Windows partition in Windows.  

What you can do is rename the Windows partition Volume Name.  This can also be done in Linux, but is a lot easier in Windows (i.e. can be done via GUI).
  
The benefit of this is it is then mounted as media/*VolumeName* in Ubuntu as default.  Same applies for USB FlashDisks (rather than /media/Disk, /media/Disk1 etc.)

I will try the Alt+PrtSc when I next boot into Windows.

PS: this is the psychocats tutorial on auto-mounting: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) (just substitute "/windows" with "/media/*VolumeName*"

---

