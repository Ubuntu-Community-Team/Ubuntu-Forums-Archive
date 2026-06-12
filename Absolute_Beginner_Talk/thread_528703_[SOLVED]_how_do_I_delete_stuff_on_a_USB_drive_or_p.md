---
title: "[SOLVED] how do I delete stuff on a USB drive or portable hard disk"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-08-18
I can't delete stuff from portable hard drives and USB drives - it says the stuff is read-only. How do I delete it?

---

### Post by agds on 2007-08-18
This is a common problem.  It has to do with the permissions with which the filesystem gets mounted.  This article is a decent reference: [How to edit and understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html").  In particular, look at the rw option.

---

### Post by tdrusk on 2007-08-18
Right click the drive.
Click properties.
Click Permissions (third tab over)
Change all of the "access" boxes to "Read And Write".

---

### Post by kleo skywalker on 2007-08-18
> **fuzzyhair said:**
> Right click the drive.
Click properties.
Click Permissions (third tab over)
Change all of the "access" boxes to "Read And Write".

The owner is root, so I can't change permissions. What do I do?

---

### Post by agds on 2007-08-18
> **kleo skywalker said:**
> The owner is root, so I can't change permissions. What do I do?

Please type ```
mount
``` into a terminal window and post the result.  This should show us how the drive is being mounted at the moment.

---

### Post by tdrusk on 2007-08-18
Darn. I'm not sure. Check out what agds posted.

---

### Post by mikeyphi on 2007-08-18
> **kleo skywalker said:**
> I can't delete stuff from portable hard drives and USB drives - it says the stuff is read-only. How do I delete it?

Sounds as though you need to change the Permissions for those drives:
When the drive is connected  - open a terminal and have a look at /media to see the name given to the drive:
enter: ls -al

then:
sudo chmod a+w drivename
where drivename is the name you previously found.

Hope that works!

All that's assuming the individual files on the drives are not locked!

---

### Post by agds on 2007-08-18
This is similar to what I'm going to suggest: [unable to chown or chmod on USB drive]("http://ubuntuforums.org/showthread.php?t=175256").  Of course, I can give more specific instructions once I've seen your list of mounted devices.

---

### Post by kleo skywalker on 2007-08-18
> **agds said:**
> Please type ```
mount
``` into a terminal window and post the result.  This should show us how the drive is being mounted at the moment.

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sdb4 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sdb2 on /media/disk-2 type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sdb3 on /media/disk-3 type ntfs (rw,nosuid,nodev,umask=222,utf8)



The portable hard drive has four partitions, I only need to delete stuff on one - /dev/sdb1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8).

---

### Post by kleo skywalker on 2007-08-18
> **mikeyphi said:**
> Sounds as though you need to change the Permissions for those drives:
When the drive is connected  - open a terminal and have a look at /media to see the name given to the drive:
enter: ls -al

then:
sudo chmod a+w drivename
where drivename is the name you previously found.

Hope that works!

All that's assuming the individual files on the drives are not locked!

The ls -al thing gives a really long response that I can't make head or tail of. I'm new.

---

### Post by por100pre1 on 2007-08-18
You can try using Nautilus as root:

```
gksudo nautilus
```

and then delete the undesired file(s). Be careful with this! Be sure to close Nautilus after that.

---

### Post by agds on 2007-08-18
> **kleo skywalker said:**
> The portable hard drive has four partitions, I only need to delete stuff on one - /dev/sdb1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8).

Ah, it's NTFS.  Okay, check this out:

[MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

That's the semi-official story.  Googling *ntfs rw ubuntu* will get you a ton more info, but first see if the above link gets you anywhere.

---

### Post by kleo skywalker on 2007-08-18
> **por100pre1 said:**
> You can try using Nautilus as root:

```
gksudo nautilus
```

and then delete the undesired file(s). Be careful with this! Be sure to close Nautilus after that.

I get the following response when I run that command:

(nautilus:12107): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

And even though nautilus does open in the root account, stuff on this portable hard drive doesn't get deleted saying it is a read-only disk. Says the same thing when I try to change the permissions.

What next?

---

### Post by kleo skywalker on 2007-08-18
> **agds said:**
> Ah, it's NTFS.  Okay, check this out:

[MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

That's the semi-official story.  Googling *ntfs rw ubuntu* will get you a ton more info, but first see if the above link gets you anywhere.

I did what it says on that link, rebooted and then ran gksudo nautilus. This time root had permissions to create and delete files, so I deleted what I needed to.
Except, when I right-click on the drives (on desktop) and click eject, it says > Can't eject volume
If I remember correctly, the same thing had happened the only other time I'd used this portable hard drive on my computer. How do I eject it?

---

### Post by agds on 2007-08-18
You may need to change the entry in /etc/fstab, but in the meantime you can probably unmount it as superuser.  You could try ```
sudo umount /media/disk
``` and see if that does it.

---

### Post by kleo skywalker on 2007-08-18
> **agds said:**
> You may need to change the entry in /etc/fstab, but in the meantime you can probably unmount it as superuser.  You could try ```
sudo umount /media/disk
``` and see if that does it.

Yes I was in the middle of posting that I did > sudo umount /media/devicename and it worked. I had to do it four times though, for each of the disks.

---

### Post by agds on 2007-08-18
To save you that hassle in the future, you can edit your file system table.  Back it up first, though.  I use vi in the command below, but you can use gedit or whichever text editor you prefer.  ```
sudo cp /etc/fstab /etc/fstab.bak
sudo vi /etc/fstab
```  Then find the lines corresponding to those NTFS disks and add "user" to the comma-separated list of options.  ```
/dev/sdb1 /media/disk ntfs rw,nosuid,nodev,umask=222,utf8,[COLOR="Red"]user[/COLOR] 0 0
```  Save the file and mount the disks again.  ```
sudo mount -a
```  Now try ejecting them as you normally would.  If that still doesn't work, you may need to change umask from 222 to 000.

---

