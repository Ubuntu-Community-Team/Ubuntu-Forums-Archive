---
title: "Mounting linkstation NAS"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by GrantShoe on 2007-03-07
I've been having some troubles mounting my network attached storage drive... I got it to the point where it's on my desktop! but it says unmounted.

in this thread i posted some of my laments: [http://ubuntuforums.org/showthread.php?t=377760](http://ubuntuforums.org/showthread.php?t=377760)

i installed smbfs
i tried to mount it on the spot in the terminal and that wasn't happening so i edited the /etc/fstab with:```
//NAS-250	/media/NAS-250	smbfs	guest,uid=1000,iocharset=utf8,codepage=unicode,unicode	0	0
```

so my situation now is that i have this:

[[IMG]http://img178.imageshack.us/img178/6537/snapshot4cp2.th.png[/IMG]](http://img178.imageshack.us/my.php?image=snapshot4cp2.png)

it seems to be great except it says unmounted so the folder is completely empty.

there's an option in the properties to mount the drive "mounting" - generic mount options.  I tried to edit this with my settings because right now the options say that the mountpoint is /media/ and i changed that to /media/NAS-250 and checked the mount automatically chkbox but that just froze my computer to the point where i couldn't ctrl-alt-del or anything and had to col reboot.

so does anyone have any idea about how to mount this drive?

---

### Post by GrantShoe on 2007-03-08
bump - does anyone know how to help me?

---

