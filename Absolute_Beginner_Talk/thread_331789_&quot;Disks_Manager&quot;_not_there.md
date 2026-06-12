---
title: "&quot;Disks Manager&quot; not there?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Winterkind on 2007-01-05
Hello!

I've just installed Ubuntu 6.10 next to a Windows XP. So this is a newbie question:

The following help page ([https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)) refers to a "disks manager", accessible via System->Administration->Disks.

My problem is: System->Administration does not include any entry called "disks" or "disks manager" or whatever. I've not found any hints so far what I might be doing wrong. The installation seemed to have gone without any issues.

What am I missing here?

Thanks,
Winterkind!

---

### Post by steve.horsley on 2007-01-05
Disk Manager is not included in Edgy. I really don't know why. 

I suggest 2 things (if you are up to it):

1:
Remove the UUID stuff from /etc/fstab (make a backup first). Edgy makes entries like this:
> # /dev/hda5
UUID=bc84a340-83f2-4c86-afd9-a1dbabe5af13 /               ext3    defaults,errors=remount-ro 0       1
At least they're good enought to tell you what device it is in the comment line. Edit the file by copying the stuff after the UUID= to the line above, and then uncomment the /dev lines and comment the UUID= lines instead, so it looke like this:
> /dev/hda5 /               ext3    defaults,errors=remount-ro 0       1
#UUID=bc84a340-83f2-4c86-afd9-a1dbabe5af13 /               ext3    defaults,errors=remount-ro 0       1
Now you have valid lines in both UUID and /dev format, with the /dev ones being the active ones. 

2:
install package **pysdm**. This is an excelent replacement for the old disk manager, but doesn't understand UUID= entries, hence step 1 above. It appears in System->Administration->Storage Device Manager

---

### Post by Winterkind on 2007-01-05
Hi Steve,

thanks for your quick reply! Your input and this document ([https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)) showed me how to change the fstab file.

Works!

---

