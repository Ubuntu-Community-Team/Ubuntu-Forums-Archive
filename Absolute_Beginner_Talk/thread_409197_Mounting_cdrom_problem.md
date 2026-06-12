---
title: "Mounting cdrom problem"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by ssharish on 2007-04-14
Hi,

I been trying this for quit a few hours but no success. I tried mounting the Cdrom drive thought this command

```

mount /dev/cdrom /mnt

```

It would do something and after few min its just says media not found and sends a error message like "Cdrom error code no 32". I dont really understand. Why does this happens, what is the solution for this. How do i read a data Cd on Kubuntu.

The interesting part here is when i try to play a song from a auto CD it plays fine but when i try to read a file, no success.

I even tried unmounting it no success either.

Can any one help me please

Thanks you

ssharish

---

### Post by Malta paul on 2007-04-14
Check out [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) 
This should help you, Have fun :D

---

### Post by ssharish on 2007-04-14
Thank Paul for the reply, but the documentation doesn't say anything about problem mounting in Cdrom drive.

Have anybody faced this problem before?/

ssharish

---

### Post by zvacet on 2007-04-14
```
mount /media/cdrom0
```

---

### Post by ssharish on 2007-04-14
sorry zvacet nothing happened. It just give me a message "No media found". But the CD  is already in the drive.

this is my fstat entries, does this help u

```

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=e820a50d-9a55-4692-8f36-24b3e96770b2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda2
UUID=6acdfb12-db02-40f5-a326-f4f4a7351622 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda3
UUID=befc9dc8-625e-46f2-b5b8-80ed88550019 none swap sw 0 0
/dev/hdc /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0

```

ssharish

---

