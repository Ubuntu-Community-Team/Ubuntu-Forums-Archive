---
title: "Problems mounting  Floppy"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-01
Hi
When I try to copy a file to my floppy drive, I get the following error message:

Unable to mount the floppy drive. There is probably no floppy in the drive.:
[mntent]: line 3 in /etc/fstab is bad

mount: /dev/fd0 is not a valid block device

Note that there WAS a floppy in the drive.

I have followed the instructions given in this HowTo [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=mounting+floppy](http://www.ubuntuforums.org/showthread.php?t=104259&highlight=mounting+floppy)
but no change. The line recommended for fstab in respect of the floppy is EXACTLY as is written here.

Anybody else experienced this problem and knows how to overcome it?

Thanks
Paul

---

### Post by pistcivet on 2006-08-01
When I'm using a floppy, usually its already formatted for Windows/DOS.

sudo mount -t msdos /dev/fd0 /mnt
mounts the floppy for read/write at /mnt.
"sudo cp /path/to/file /mnt" copies file to floppy.
"ls -al /mnt" lists files on floppy. and so on...

sudo umount /dev/fd0
unmounts the floppy.

sudo mkdosfs /dev/fd0
formats the floppy (for DOS).

This works for me without messing around with fstab or mtab.

---

### Post by PaulFXH on 2006-08-01
Hi pistcivet

Yeah, that works perfectly for me too.
Just wondering why such a simple procedure for such a simple task in not available in the Ubuntu Desktop Guide.
mMybe it's just that nobody uses floppies anymore.

Much thanks
Paul

---

