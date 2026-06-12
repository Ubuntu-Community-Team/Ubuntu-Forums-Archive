---
title: "Why isn't my volume automounting?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Fallom on 2006-06-16
/dev/hda5 is an ext3 partition that I added after I installed Ubuntu. It mounts fine, but I have to do it manually. I thought setting the 'defaults' option made it automatic?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ext3    defaults,umask=777      0       0
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0   $/dev/hdb6       none            swap    sw              0       0

---

### Post by aysiu on 2006-06-16
If it's in the /etc/fstab file, it should be mounted automatically.

I don't know if the umask parameter works with Ext3. Maybe that's what's futzing with the automount?

Do you get any error messages during boot-up?

---

### Post by Fallom on 2006-06-16
Looks like taking out the umask parameter fixed it. I'm not exactly sure why I put it there in the first place.

Thanks!

---

