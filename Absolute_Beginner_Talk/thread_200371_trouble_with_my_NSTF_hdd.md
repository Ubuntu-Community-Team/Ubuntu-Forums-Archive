---
title: "trouble with my NSTF hdd"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2006-06-20
I have 2 x 120 gig hdds in my pc.  On the weekend I decided it was time to make the jump to Ubuntu from Windows.  All is going relatively smoothly, but i am having small problems with my second hdd.  The first one /dev/hda, has ubuntu on it.  The second hdd, /dev/hdb is still NTSF, which I could access but not wirte to.  On the Desktop I went to System->Administration->Disks, diabled the hdd and formatted it as ext3.  Now I can't enable it and it still lists it as NTS.  What do I need to do to get this in a format that Ubuntu will read and write and have it enabled.  If you can't tell, I'm a dirty Linux noob, but I'm learning fast and am totally smitten by Ubuntu.  One Distro to rule them all......

Oh and while I'm posting, I keep getting an error with the latest system update about a broken package:

E: /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.0ubuntu1_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0

Honestly, it might as well be written in Japanese.

---

### Post by anaconda on 2006-06-20
you have to edit your fstab file, and change the ntfs to ext3 from the line that refers to your ex ntfs hard-disk..

If you post the contents of your fstab file here I am sure someone will tell you exactly what you have to change...

Oh.. it is located hete:  /etc/fstab

---

### Post by xboxbman on 2006-06-20
[QUOTE=anaconda]you have to edit your fstab file, and change the ntfs to ext3 from the line that refers to your ex ntfs hard-disk..

If you post the contents of your fstab file here I am sure someone will tell you exactly what you have to change...

Oh.. it is located hete:  /etc/fstab[/QUOTE]

Thank you for the quick reply.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/ntfs_storage     ntfs auto,gid=1001,umask=0002   0 0

---

### Post by xboxbman on 2006-06-20
bizump

---

### Post by raptros-v76 on 2006-06-20
do fdisk -l, tell us what that gives

---

### Post by caldaar on 2006-06-20
I believe the following line would be what needs to change

dev/hdb1 /media/ntfs_storage ntfs auto,gid=1001,umask=0002 0 0

I would comment it out using # and try:

# dev/hdb1 /media/ntfs_storage ntfs auto,gid=1001,umask=0002 0 0
dev/hdb1 /media/ntfs_storage ext3 defaults 0 1


It will still be mounted to the "/media/ntfs_storage" but should be accessible.

---

### Post by xboxbman on 2006-06-20
[QUOTE=raptros-v76]do fdisk -l, tell us what that gives[/QUOTE]
thanx...here's fdisk report:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14759   118551636   83  Linux
/dev/hda2           14760       14946     1502077+   5  Extended
/dev/hda5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+  83  Linux

---

### Post by xboxbman on 2006-06-20
[QUOTE=caldaar]I believe the following line would be what needs to change

dev/hdb1 /media/ntfs_storage ntfs auto,gid=1001,umask=0002 0 0

I would comment it out using # and try:

# dev/hdb1 /media/ntfs_storage ntfs auto,gid=1001,umask=0002 0 0
dev/hdb1 /media/ntfs_storage ext3 defaults 0 1


It will still be mounted to the "/media/ntfs_storage" but should be accessible.[/QUOTE]
You are awsome!!  It works now.  I'll say it once, I'll say it again, this forum is top notch!

---

