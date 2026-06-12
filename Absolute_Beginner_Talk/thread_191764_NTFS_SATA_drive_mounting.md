---
title: "NTFS SATA drive mounting"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by jkopp on 2006-06-07
I have already mounted my SATA NTFS windows partion.  I had a Draper 6.06 installed previously and had to re-load due to some graphics cards issues.  

In the previous install I was able to edit the fstab so that the NTFS partition would be dispalyed on my user desktop and appeared with drive icon.  Currently it only appears as a folder.  I would like the drive to appear with a drive icon on both my user accounts Desktops.

Does anyone know the fstab entry that I am referring to from my previous installation?

Thanks,
Justin

---

### Post by nanotube on 2006-06-08
[QUOTE=jkopp]I have already mounted my SATA NTFS windows partion.  I had a Draper 6.06 installed previously and had to re-load due to some graphics cards issues.  

In the previous install I was able to edit the fstab so that the NTFS partition would be dispalyed on my user desktop and appeared with drive icon.  Currently it only appears as a folder.  I would like the drive to appear with a drive icon on both my user accounts Desktops.

Does anyone know the fstab entry that I am referring to from my previous installation?

Thanks,
Justin[/QUOTE]
hi,
things only appear as a drive icon if you mount them into the /media/ folder. if you mount the drive to some other location in the filesystem, it will not make the magical drive icon.
so just edit your fstab so that the mount location is in /media, and it will work. (don't forget to create the folder in /media before you attempt to mount to it.)

---

