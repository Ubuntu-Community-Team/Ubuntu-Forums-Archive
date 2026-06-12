---
title: "Issue with USB Digital Drive"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-11-08
My digital drive worked perfectly in hoary, but after switching to breezy I am unable to write or delete files from it. I get the following error "device is a read only disk". I cannot change the permission settings through the gui interface in the properties section.

How can I get this working again?
Thanks!
-Clay

---

### Post by Mustard on 2005-11-08
Have you tried System>>Administration>>Disks?

---

### Post by Who on 2005-11-08
Just to add to the OPs Q:
I have two compact flas disks that read/write fine on Windows but are declared Read Only by Linux (A fresh hoary install). I checked mtab and it seemed users should have been able to write, and then I tried writing the disk as superuser and it still claimed the disk was readonly...

So..
any ideas?

---

### Post by the_purulent on 2005-11-08
[QUOTE=Mustard]Have you tried System>>Administration>>Disks?[/QUOTE]

I will try this when I get home and let you know.

---

### Post by the_purulent on 2005-11-10
I still cannot write to this disk.

sudo gedit /etc/mtab

```

/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-9-386/volatile tmpfs rw,mode=0755 0 0
/dev/hdb5 /home ext3 rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
/dev/sda1 /media/usbdisk vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```

Any other ideas?

---

### Post by the_purulent on 2005-11-11
No one has any ideas?
This is a failry important function for me as I need to be able to update my files for work.

---

### Post by apjone on 2005-11-11
Ok this may or may not work but
1) $ sudo bash - become root
2) 'cd' to the mount point of your drive
3) 'chmod 777 *' and or 'chown -R username *' 
4) should now have complete access to your drive

---

### Post by the_purulent on 2005-11-11
No Luck.  Still lists as read only and I cannot copy, delete or modify files onto or within the usb disk drive.

---

### Post by apjone on 2005-11-11
change 
/dev/sda1 /media/usbdisk vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
to
/dev/sda1 /media/usbdisk vfat rw 0 0

try that

---

