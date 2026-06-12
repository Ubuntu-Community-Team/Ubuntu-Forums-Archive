---
title: "problems with editing fstab"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by mwk2916 on 2006-11-24
[SIZE="2"]/dev/sda1       /media/sda1     ext3 rw,auto,user,exec      0       2
/dev/sda2       /media/sda2     vfat rw,auto,user,exec      0       2

Can somebody please tell me what I have to add to these two lines in fstab to give me read and write access to the partitions mounted at /media/sda1 and /media/sda2? I've been trying to follow the tutorial on editing fstab but I must be missing something.

Thanx for your help![/SIZE]

---

### Post by Bachstelze on 2006-11-24
For the ext3 partition, you don't need any parameter, just modify your line like this :

```
/dev/sda1 /media/sda1 ext3 defaults 0 2
```

and then you can tweak the permissions with CHMOD like you do for any other file/directory.

For the FAT, you need do to this :

```
/dev/sda2 /media/sda2 vfat rw,iocharset=utf8,uid=YOUR_UID_HERE,umask=022 0 0
```

(You can change the umask to your needs and also specify a GID if you want)

---

### Post by mwk2916 on 2006-11-24
[SIZE="2"]How do I go about finding the UUID # for that partition?[/SIZE]

---

### Post by taurus on 2006-11-24
You don't have to use UUI; you can still use the old fashion way, /dev/sda1 thing in your /etc/fstab...

---

### Post by Bachstelze on 2006-11-24
By the way, could anyone explain me why on earth Edgy use UUIDs ?

---

### Post by mwk2916 on 2006-11-24
[SIZE="2"]Ok but what about the vfat partition at /media/sda2? I tried it without the uuid "/dev/sda2 /media/sda2 vfat rw,iocharset=utf8,umask=022 0 0" and that doesn't give me write access either.[/SIZE]

---

### Post by taurus on 2006-11-24
```

/dev/sda2  /media/sda2  vfat  iocharset=utf8,umask=000  0  0

```

---

### Post by mwk2916 on 2006-11-24
[SIZE="2"]That got it! Excellent help guys! Thanks so much![/SIZE]

---

### Post by CatKiller on 2006-11-24
> **HymnToLife said:**
> By the way, could anyone explain me why on earth Edgy use UUIDs ?

I think [this]("https://wiki.ubuntu.com/LibAtaForAtaDisks") is why.

---

### Post by confused57 on 2006-11-24
Herman's explanation of the new Edgy fstab & mounting:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by bodhi.zazen on 2006-11-24
> **mwk2916 said:**
> [SIZE="2"]How do I go about finding the UUID # for that partition?[/SIZE]

To list your partitions by UUID:

First connect the usb devices:```
ls /dev/disk/by-UUID -alh
```

---

