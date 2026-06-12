---
title: "Blank fstab"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Jugney on 2008-01-14
Hi Ubuntuians,

I just created a new partition and am planning to move over my /home directory to it. The problem is, I open up handy dandy etc/fstab and it's blank, whether I open it in gedit or nano. Could someone help with this? My computer seems to run fine, but I'm concerned if my fstab is blank.

Any ideas?

Jugney

---

### Post by thelatinist on 2008-01-14
> **Jugney said:**
> Hi Ubuntuians,

I just created a new partition and am planning to move over my /home directory to it. The problem is, I open up handy dandy etc/fstab and it's blank, whether I open it in gedit or nano. Could someone help with this? My computer seems to run fine, but I'm concerned if my fstab is blank.

Any ideas?

Jugney

The file is located at /etc/fstab.  Since you are probably in your home directory, if you leave off the ititial / it thinks you want to edit /home/username/etc/fstab.  

Do the following:

```
cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```

The first command backs up your fstab (always back up system files before editing them).

---

### Post by Jugney on 2008-01-14
Thank you. I love it when the fix is easy!

---

### Post by thelatinist on 2008-01-14
Glad I could help.  Don't forget to mark this thread [Solved] using the thread tools!

---

### Post by Jugney on 2008-01-14
Now I'm wondering...I saw directions on how to indicate a partition to contain the /home folder, but it seems they were written pre-UUID.

Below is my fstab. When adding an entry for the new partition, sda3 (which is not currently listed) how do I know its UUID?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fa54c7c3-676e-434b-aaf1-df88eab4ebbc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=509f9dd4-b4c8-44bc-93d2-f93b33dbef0a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by thelatinist on 2008-01-14
> **Jugney said:**
> Now I'm wondering...I saw directions on how to indicate a partition to contain the /home folder, but it seems they were written pre-UUID.

Below is my fstab. When adding an entry for the new partition, sda3 (which is not currently listed) how do I know its UUID?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fa54c7c3-676e-434b-aaf1-df88eab4ebbc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=509f9dd4-b4c8-44bc-93d2-f93b33dbef0a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Don't bother with UUID. Just use the following line:

```
/dev/sda3    /home/    ext3    defaults,errors=remount-ro    0   1
```

---

### Post by Jugney on 2008-01-14
No '#' in front?

---

### Post by thelatinist on 2008-01-14
The # is put in front of lines that contain comments so that the system won't read them.  If you wan't the system actually to mount the partition, then no, no #. ;-)

---

