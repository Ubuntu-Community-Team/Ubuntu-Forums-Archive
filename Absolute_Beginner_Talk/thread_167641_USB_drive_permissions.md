---
title: "USB drive permissions"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-28
I have an external USB drive that shows up under Ubuntu as SCSI0_VOL1.  Although I can see it and read it,  I cannot write to it.  Any ideas how I can get Ubuntu to give me permission to write to it?

Also, can I set this drive up as "shared" so I can back up files to it from my notebook (wireless).

Thank you.

---

### Post by Qrk on 2006-04-28
Find the row of /etc/fstab that corresponds to your external harddrive. 

```
sudo gedit /etc/fstab
```

Change whatever is under <options> in that row to "defaults"

---

### Post by landsg on 2006-04-28
Here is the contents of my fstab file after editing.  Still cannot get write permission to it.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    defaults             0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Qrk on 2006-04-28
Its hdb1, right. 

Have you done 

```
sudo mount -a
```

---

### Post by landsg on 2006-04-28
Yes, I tried "sudo mount -a".  Doesn't allow write privelages.  Here is the updated fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3	defaults

/dev/hdb5       none            swap    defaults             0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Qrk on 2006-04-29
hmm. Try browsing with nautilus run in root mode. Use this command to get root privileges:

```
gksudo nautilus
```

But to your problem. Are you sure it is /dev/hdb1? Most external hard drives come formated as fat32, unless you manually changed this. But hdb1 seems to be mounted as ext3.

---

### Post by landsg on 2006-04-29
No, I'm not sure if its hdb1.  In Nautiluss, it's listed as SCSI0_VOL1.  Does that translate to a different name in Fstab?

---

### Post by Qrk on 2006-04-29
fstab doesn't use the /media/ naming used by nautilus.

 It probably isn't hdb1, then. If its an external drive, it might be sda or sdb. If it is removable and discovered by hotplugging, than fstab won't have it listed.

Try looking in System->Adminstration->Disks for more information. This may even fix your problem. 

If, however, the drive is formated as ntfs, you won't be able to write to it with Linux.

---

### Post by landsg on 2006-04-30
If Linux won't read NTFS, then can I reformat it using Linux?  I would like to use this as my data backup drive, even as a shared drive on my network.

---

### Post by Randomskk on 2006-04-30
I'm not sure if it's installed by default, but install gparted. That's a tool for formatting drives, so you could use it to format your USB drive.
Choose filesystem type "ext3", which is what linux generally uses.

---

### Post by landsg on 2006-04-30
OK, I also checked in System-Admin-Disks; it's not listed.  Therefore, I believe you are right, it is most likely formatted in NTFS.

My next step is to reformat it.  Your suggestions are welcome.  Thanks for your expertise.

---

### Post by landsg on 2006-05-06
Hi:

I installed "gparted", and created a new disklabel, then tried to create the new partition, but get an error message.  Any idea on what may be causing that?  I am using an 80MB Seagate USB drive.

---

### Post by landsg on 2006-05-06
OK, got it formatted in ext3.  However, Ubuntu is still telling me I don't have permission to write to it.  I am the only user and do admin tasks.  How do I get write privelages to the USB drive?

---

