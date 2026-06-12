---
title: "NTFS-3G &amp; Locale - Auto Mounting problem"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by m_O_O_m on 2006-12-22
Hi there.

I have  a weird problem with NTFS-3g.

It used to work ok just until now. I have installed and configured some programs so I don't know what caused this problem.

Ubuntu(Gnome) Edgy 6.10 + Scim + ATI (fglrx)

My /etc/fstab is ...
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
/dev/hda1 /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda3
/dev/hda3 /home/moom80nz/storage          ext3    defaults        0       2

# /dev/hdb1
/dev/hdb1 /media/hdb1     ntfs-3g    defaults,nls=cp949,umask=007,gid=46 0       1

# /dev/sda1
/dev/sda1 /media/sda1     ntfs-3g    defaults,nls=cp949,umask=007,gid=46 0       1

# /dev/sda5
/dev/sda5 /media/sda5     ntfs-3g    defaults,nls=cp949,umask=007,gid=46 0       1

# /dev/sdb1
/dev/sdb1 /media/sdb1     ntfs-3g    defaults,nls=cp949,umask=007,gid=46 0       1

# /dev/sdb2
# UUID=09BDE5E866320923 /media/sdb2     ntfs-3g    defaults,nls=cp949,umask=007,gid=46 0       1

# /dev/hda5
/dev/hda5 none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

nls=cp949 is for EUC-KR locale for folders and files with Korean letters. However when gnome starts, all NTFS drives are auto-mounted 
(I don't know how this works though) and appears on the Desktop. When I open the drive by double clicking one of the drive, 
Folders with Korean letters do not show up.

I can solve this by 
sudo umount -a and sudo mount -a to re-mount all partitions & drives with no errors at all. So I think there's some sort of a  
hard drive auto-mounting mechanism by GNOME Desktop which uses different file than the /etc/fstab I wrote above.

It is really annoying. 

Does any one know how to solve this?

Thanks heaps,
Jason

---

### Post by taurus on 2006-12-22
Try to replace the "1" with "0" for the ntfs-3g entries in your /etc/fstab!!!  Then, reboot and see what happens...

Applications -> Accessories -> Terminal
[code[gksudo gedit /etc/fstab[/code]

---

### Post by givré on 2006-12-22
ntfs-3g don't use the nls= option, it use the locale= option instead.
man ntfs-3g for more info.
To get your locale, execute  locale -a in a terminal and pick the one you need.

---

### Post by m_O_O_m on 2006-12-22
> **taurus said:**
> Try to replace the "1" with "0" for the ntfs-3g entries in your /etc/fstab!!!  Then, reboot and see what happens...

Applications -> Accessories -> Terminal
[code[gksudo gedit /etc/fstab[/code]

Nothing happened.

To tell you the truth. I don't know what those numbers at the end are for...
I changed the last 1 to 0 and did a reboot but nothing happened.

---

### Post by m_O_O_m on 2006-12-22
> **givré said:**
> ntfs-3g don't use the nls= option, it use the locale= option instead.
man ntfs-3g for more info.
To get your locale, execute  locale -a in a terminal and pick the one you need.

Wow!!! Your are a legend!!!!!!!!!!!

I have changed my "nls=cp949" setting to 
"locale=ko__KR.utf8" and IT WORKS.!!!!!

Thanks heaps!!!!

---

