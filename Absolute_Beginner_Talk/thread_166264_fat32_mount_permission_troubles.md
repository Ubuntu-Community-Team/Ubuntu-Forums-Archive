---
title: "fat32 mount permission troubles"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by OrganicPanda on 2006-04-26
hey all,

i got my fat32 partition mounted fine but only some of the directories are writable, like 50/50, some of them are full read-write-execute but some are just read-execute, my entry to fstab looks like:

```

/dev/sda2 /home/panda/files vfat iocharset=utf8,umask=000 0 0

```

and ive sudo umounted / mount -a / rebooted more times than i care to recall , it doesent appear to like me, i guess sudo chmodding could work but id rather know whats actually wrong, any help would be much appriciated
cheers,
panda

---

### Post by joshrobinson on 2006-04-26
[QUOTE=OrganicPanda]hey all,

i got my fat32 partition mounted fine but only some of the directories are writable, like 50/50, some of them are full read-write-execute but some are just read-execute, my entry to fstab looks like:

```

/dev/sda2 /home/panda/files vfat iocharset=utf8,umask=000 0 0

```

and ive sudo umounted / mount -a / rebooted more times than i care to recall , it doesent appear to like me, i guess sudo chmodding could work but id rather know whats actually wrong, any help would be much appriciated
cheers,
panda[/QUOTE]

try

```
/dev/sda2 /home/panda/files   vfat    umask=0000    0 0
```

then do sudo umount /dev/sda2
then sudo mount /dev/sda2

---

### Post by manicka on 2006-04-26
I've always used something like 

```
/dev/sda2 /home/panda/files   vfat   defaults,rw,umask=000        0       0
```

---

### Post by hizaguchi on 2006-08-30
Guess I'm replying to this kinda late, but what has worked for me is to add the option "uid=username" to the fstab options, which makes the mounted drive owned by whoever you put for "username", and then go in an manually mark the folders writable.

---

### Post by Omnios on 2006-08-30
Hi hi I had a lot of problems with my document drive which is vfat32 with permitions etc and came up with this fstab entry which I have now been using for over a year.
```
/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0
```

  Anyways found it to work a lot better than the guide entrys

---

