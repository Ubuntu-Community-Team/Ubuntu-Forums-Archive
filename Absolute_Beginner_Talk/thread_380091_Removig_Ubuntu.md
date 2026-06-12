---
title: "Removig Ubuntu"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by IanGB on 2007-03-09
Looked at all the removal advice here, but still have questions.

With Ubuntu taking up all the drive as the only system on a laptop, without a floppy drive, how can I format the drive to install a twin boot system?

Fdisk will not load from a CD because it is not read by Linux.

Ian

---

### Post by PartisanEntity on 2007-03-09
There is a live cd version of gparted. I would recommend using that. You place it in the cdrom drive, boot the laptop from the cd and then you can add/remove/move/resize your partitions as you like. IMO it is better than the gparted that comes with the ubuntu live cd.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by IanGB on 2007-03-09
Thanks for that but I guess I need to get it posted to me or is it a download?

---

### Post by xyz on 2007-03-09
> **IanGB said:**
> Thanks for that but I guess I need to get it posted to me or is it a download?
I think Partisan gave you the download link...

---

### Post by easyease on 2007-03-09
actually you will need to reinstall windows first anyway so you can decide how big a space to give ubuntu then.

---

### Post by nero_86 on 2007-03-09
You can download the iso of gparted live in

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")

---

### Post by easyease on 2007-03-09
theres no need for gparted if you are planning to dual boot windows and ubuntu on a single hd that already is filled with ubuntu........

---

### Post by easyease on 2007-03-09
first you need to install windows, make a partition ntfs to required size then install to it.
secondly any remaining space can be used to create a linux ext3 partition to install ubuntu on.

---

