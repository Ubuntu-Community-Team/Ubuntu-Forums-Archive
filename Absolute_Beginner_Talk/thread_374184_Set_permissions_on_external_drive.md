---
title: "Set permissions on external drive"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Wardazo on 2007-03-02
Hi

I'm trying to set my external hard drive to occasionally be able to use it with apache.

However, I cannot changes the permissions on the drive - it has to be publiclly readable.

If I use the file browser the menus always flip back to the original (700). If I use chmod it gets ignored.

Any help would be very appreciated.

Thanks

Ward

---

### Post by Archmage on 2007-03-02
I would suggest to enter the harddrive in fstab with the nessacary rights.

---

### Post by Wardazo on 2007-03-02
Hi

Do you mean something like this?

/dev/sda  	/media/LACIE  	auto  	rw,auto,user,sync  	0 0

But where are the permissions?

Thanks for the previous reply.

Ward

---

### Post by xyz on 2007-03-02
an example, my 3 partition external HD:
> /dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)

/dev/sda2 on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)

/dev/sda3 on /media/USBDISK-0 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)

rw

---

### Post by Wardazo on 2007-03-02
Hi

I edited my fstab as folows:

/dev/sda1       /var/www/disk   vfat    rw,auto,umask=0644      0       0

... but the drive does not auto mount.

There is a disk folder that I created under sudo.

Thanks

Ward

---

