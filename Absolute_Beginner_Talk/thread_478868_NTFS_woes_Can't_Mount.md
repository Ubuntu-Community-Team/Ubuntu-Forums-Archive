---
title: "NTFS woes Can't Mount"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by nothinghead on 2007-06-19
I was getting this error when I tried to open my external HD.

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
Boot Windows and shutdown it cleanly, or if you have a removable
device then click the 'Safely Remove Hardware' icon in the Windows
taskbar notification area before disconnecting it.
Or
Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
the 'force' option read-write, or with the 'ro' option read-only.
Or
Mount the NTFS volume with the 'ro' option in read-only mode.

I ran ntfsfix and now it tells me
> Volume is scheduled for check. Please boot into Windows TWICE, or use the 'force' mount option. For example type on the command line:  mount -t ntfs-3g /dev/sdb1 /media/Media -o force.  Or add the option to the relevant row in the /etc/fstab file:  /dev/sdb1 /media/Media ntfs-3g defaults.force 0 0

The first option gives me this:
> WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: failed to access mountpoint /media/Media: No such file or directory
FUSE mount point creation failed
Unmounting  /dev/sdb1 (Media)

With the latter, it won't let me save changes to fstab.

Sorry to bother you with this, but I've just installed Ubuntu today and all of my files are stuck on that external drive that I can't access.

EDIT: No, I do not have Windows installed anymore.

---

### Post by raja on 2007-06-19
You have to create the mount point before you can mount it. So when you force mount it, use an existing mount point or else make the mount point first. 
```
mkdir /media/Media
mount -t ntfs-3g /dev/sdb1 /media/Media -o force
```

For the other option, if you open fstab with sudo, you can save changes to it.

---

### Post by nothinghead on 2007-06-19
Thank you so much.

I've discovered appending "sudo" to the front of commands gives me "root" to allow installation of software/running commands etc.

However, how do I use sudo in the context you said?  I mean, how would I use sudo to open fstab?  I assume there's a command line for opening files that I don't know yet seeing as I've been using Ubuntu for all of 4 hours?

---

### Post by raja on 2007-06-19
```
sudo gedit /etc/fstab
```
Or any other editor you prefer...

---

### Post by drivel on 2007-06-19
Try NTFS-3g,maybe it works

---

