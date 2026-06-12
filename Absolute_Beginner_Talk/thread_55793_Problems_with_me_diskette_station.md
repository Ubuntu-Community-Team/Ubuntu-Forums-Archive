---
title: "Problems with me diskette station"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by Kenshee on 2005-08-10
hello,
I have a icone that links to my diskstation, but when i try to use it, I get the following error: 'Koppelingsfout: Kan het geselecteerde volumen net aankoppelen' with detail : "mount: I could not determine the filesystem type, and none was specified"
can someone help me with this problem, because I realy need that station...
greetz kenshee

---

### Post by roland on 2005-08-10
[QUOTE=Kenshee]hello,
I have a icone that links to my diskstation, but when i try to use it, I get the following error: 'Koppelingsfout: Kan het geselecteerde volumen net aankoppelen' with detail : "mount: I could not determine the filesystem type, and none was specified"
can someone help me with this problem, because I realy need that station...
greetz kenshee[/QUOTE]

I think you have to check whether the floppy drive is correctly configured in the /etc/fstab file. There should be a line like this:

```

/dev/fd0        /media/floppy   auto    rw,user,noauto  0       0

```

If there is, could you quote it in this thread? If there is not, you could copy/paste it somewhere in the file on a new line, after **backing the file up** and opening it in an editor as root.

Then try in a terminal (in the Applications - System tools menu) the command [font=courier]mount /media/floppy[/font]. Now the floppy should be mounted and readable. Don't forget to unmount it before getting the floppy out of the drive, by typing [font=courier]umount /media/floppy[/font].

If this does not work, the program mount can really not specify the filesystem type. It is most likely it is just fat, called "vfat" in Linux. You could try to mount the floppy in this manner: [font=courier]mount -t vfat /dev/fd0[/font]. Unmounting is [font=courier]umount /dev/fd0[/font].

I hope it works.

---

