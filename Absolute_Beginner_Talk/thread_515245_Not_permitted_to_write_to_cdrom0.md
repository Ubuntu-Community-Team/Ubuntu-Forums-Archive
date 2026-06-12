---
title: "Not permitted to write to cdrom0"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by wink on 2007-08-01
My first attempt to copy a ,jpg file to a CD-RW resulted in an error message: "You don't have permission to write to this folder." If I understand correctly - not likely for a newbie - I would need to edit fstab in order to gain permission, except I don't know what to change. Here's the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=50d074da-d085-4804-a7f6-f31336d78ae3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=686af392-5bff-4794-bef9-9f4cd27f339f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0   

What do I need to put in place of "udf,iso9660 user,noauto     0       0" so I can write to cdrom0 (which is my burner). 

Thanks in advance for your help with  my continuing Ubuntu education.

wink

---

### Post by apswartz on 2007-08-01
Are you just dropping the file on the cdrom folder?

Did you try a program like k3b?

---

### Post by wink on 2007-08-01
> Are you just dropping the file on the cdrom folder?

Did you try a program like k3b? 

Tried dropping on the folder, tried to cp from the terminal but never thought of using K3b. duh!

K3b did the trick. Thank you very much.

wink

---

