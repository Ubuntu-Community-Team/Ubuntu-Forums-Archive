---
title: "can't change permissions on automounted usb drive"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by yellowband on 2007-12-10
hi

i have a usb drive auto-mounted at /media/LACIE when i attach it.  I want to make a sym-link in my web root to access the files on it, but i get forbidden errors because this drive does not have the proper permissions.  I cannot use chmod to change the permissons, it doest seem to have any effect.  my ls output looks like this

drwx------ 6 server root 32768 1969-12-31 17:00 LACIE


how can i change the permissions on this drive?  

note its not in the fstab, its automounted when i plug it in.

---

### Post by geirha on 2007-12-10
If the usb drive has a FAT filesystem, then chmod won't work since FAT doesn't support permissions and ownership. Instead you set these things when you mount it. You will have to make an entry for it in fstab to be able to do this. Adding umask=022 to the options will give all files and folders 755 permission (-rwxr-xr-x), meaning read access for everyone. Read the man page of mount to see what options you can use ```
man mount
```

---

### Post by philinux on 2007-12-10
However you can change the permission for fat32 but you have to specifiy the mount point not the device.

eg

sudo chown -R userxxx /media/diskx

---

