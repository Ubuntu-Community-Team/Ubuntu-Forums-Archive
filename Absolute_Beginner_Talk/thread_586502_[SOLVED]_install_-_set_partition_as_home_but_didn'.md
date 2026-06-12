---
title: "[SOLVED] install - set partition as /home but didn't work: has lost+found in it?!"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by snuffy on 2007-10-22
I have just done a fresh install of gutsy. i have a dual boot, but the harddrive with ubuntu on i partitioned to 20GB for the system install, 2GB for the swap, and 160GB for /home. all was good, i thought.

however, now its all installed, i checked my home folder and it is only 5GB, whilst i have the  160GB partition which is mounted as media/disk and only has the folder lost+found in it (this disk also has the padlock symbol on it !).

please tell me what i have done wrong.

thanks.
tim.

---

### Post by realvz on 2007-10-22
can u post ur fstab file here

---

### Post by snuffy on 2007-10-22
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=794d4071-cd12-4d1a-a8cb-319330528d4e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=2C642EDC642EA892 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=4A6C82D46C82B9E9 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=42F0-02BF  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4567142f-63fe-4746-8502-0d4fe2e1c445 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by realvz on 2007-10-22
you have to tell Ubuntu to mount your new home when you boot. Add a line to the &#8220;/etc/fstab&#8221; file that looks like the following:

/dev/hda5 /home ext3 nodev,nosuid 0 2
(Here, change the partition label &#8220;hda5&#8243; to the label of the new partition, and you may have to change &#8220;ext3&#8243; to whatever filesystem you chose for your new &#8220;home&#8221;)

---

### Post by snuffy on 2007-10-22
i formatted the partition as ext3, so thats fine, but silly question maybe.... how do i know what the partition label should be? where do i look?

---

### Post by snuffy on 2007-10-22
and do i need to move all the files that are currently in home to the new /home before i restart?

---

### Post by logos34 on 2007-10-22
> **snuffy said:**
> i formatted the partition as ext3, so thats fine, but silly question maybe.... how do i know what the partition label should be? where do i look?

It's probably /dev/sda3.

check with
[B]
sudo fdisk -l[/B]

> and do i need to move all the files that are currently in home to the new /home before i restart?

Yes.  Use this howto:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by philinux on 2007-10-22
Gutsy wont recognise /dev/xda, it has to be a uuid.

---

### Post by logos34 on 2007-10-22
> **philinux said:**
> Gutsy wont recognise /dev/xda, it has to be a uuid.

Are you sure?  That's the first I've heard of that.

---

### Post by snuffy on 2007-10-22
i tried what you said realvz and logos34, but it didn't work. instead i reinstalled. as far as i can tell i did exactly the same thing, only this time it worked.

thanks guys.

tim

---

### Post by philinux on 2007-10-22
> **logos34 said:**
> Are you sure?  That's the first I've heard of that.

The short version, the rc of gutsy changed my fdisk from hda's to sda's, but I did not know this as it just error on boot said /dev/hda1 not recognised. But the earlier kernel had no problem  at all !

so booted with earlier kernel and edited fstab to have uuids.

---

