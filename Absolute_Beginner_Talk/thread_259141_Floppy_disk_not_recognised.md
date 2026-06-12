---
title: "Floppy disk not recognised?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-09-16
Hi All

I followed the earlier post: [http://www.ubuntuforums.org/showthread.php?t=257376&highlight=floppy+disk](http://www.ubuntuforums.org/showthread.php?t=257376&highlight=floppy+disk)

to get my Ubuntu 6.06 floppy device recognied.

Unfortuantly I got: 
root@Server1:/home/michael# mount -t vfat /dev/fdo /mnt/floppy
mount: special device /dev/fdo does not exist

Any ideas?

Thanks

---

### Post by alienexplorers on 2006-09-17
It should be mount -t vfat /dev/fd0 /media/floppy.  The fd part is followed by a zero not a small o.  I personally use /media/floppy instead of /mnt/floppy.

---

### Post by Calculator on 2006-09-17
Thanks 

Alas, I get another problem:

root@Server1:/home/michael# mount -t vfat /dev/fd0 /media/floppy
mount: /dev/fd0 is not a valid block device

But the strange this is I found if I use Gnome and go to Places > Floppy0 I find that I can read the floppy disk bu tI am unable to write to it.

I have checked the Write Protect on the disk

Any solutions?

---

### Post by blent07 on 2006-09-20
I'm having the same problem. It automatically mounts, but I can't write anything to it. And I can't change the permissions either, saying it's a read-only filesystem. 

does that fact that it mounts with the floppy icon, but it's called: Untitled 
have anything to do with it?

---

### Post by Demio on 2006-09-20
Maybe the floppy is locked? :P

---

### Post by tatimmer on 2006-09-21
here is an entry for /etc/fstab that works.
the rw is for read/write.

/dev/fd0  /media/floppy   msdos   rw,user   0       0

---

### Post by Calculator on 2006-09-24
> **tatimmer said:**
> here is an entry for /etc/fstab that works.
the rw is for read/write.

/dev/fd0  /media/floppy   msdos   rw,user   0       0

Thanks tatimmer

I get that following with that command:
root@Server1:/home/Calculator# /dev/fd0 /media/floppy msdos rw,user 0 0
bash: /dev/fd0: Permission denied

I have reformated the floppy disk via a PC running XP ([http://ubuntuforums.org/images/smilies/icon_redface.gif)](http://ubuntuforums.org/images/smilies/icon_redface.gif)), so it is not write protected.

I can read the disk in the Ubuntu floppy drive but cannot write to it?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

It looks like a permission issue?  I have administrator access ... what else should I do?

Thanks

---

