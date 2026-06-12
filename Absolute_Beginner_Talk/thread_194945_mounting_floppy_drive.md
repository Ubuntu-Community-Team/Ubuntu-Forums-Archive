---
title: "mounting floppy drive"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by bpt on 2006-06-12
I have just loaded ubuntu onto an old P350 to explore the os. I wanted to install a program from a floppy disk and don't know how to access the floppy. The drive is there so what do I do? When I tried to mount the floppy drive I got a message asking me about the file system so I'm a bit lost. Basic assistance please.

---

### Post by cotcot on 2006-06-12
Supposing you have created a mount point /media/floppy you can add the filesystem with the -t option of mount :

```
sudo mount -t vfat /dev/fd0 /media/floppy
```

---

### Post by The Grum on 2006-06-12
bpt - What happens if you double-click on the floppy icon in Places->Computer?

---

### Post by Sef on 2006-06-12
This is from another post of mine.   There is a small bug in Dapper for the floppy, but here is an easy work around.

> 
1) Open Terminal (Konsole in KDE)

2) sudo gedit (Kate in KDE) /etc/fstab

3a) Go to the floppy module (on the bottom in gedit)

Code:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


3b) Change auto to vfat

Code:

/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

4) To open the floppy, go to Places > Computer > click on the floppy (Not sure what it is called in KDE.)

5) Click on the floppy pic

6a) Floppy drive will mount

6b) You can read your floppy documents

6b) To unmount, right click on the floppy and highlight unmount

---

### Post by bpt on 2006-06-13
Done that but now I get the error message: given UDi is not a mountable volume.

---

### Post by mlind on 2006-06-13
I don't know what Ubuntu version you're running, but you may need to
modprobe 'floppy' and 'vfat' modules. And create necessary mount points.
```

sudo modprobe vfat floppy
sudo mkdir -p /media/floppy0
sudo ln -sf /media/floppy0 /media/floppy

```

Then, like others already pointed out,  /etc/fstab should contain line
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

then try 
```

sudo mount /media/floppy

```

---

### Post by bpt on 2006-06-17
I'm using Ubuntu 5.10 and I can't sudo modprobe vfat floppy.

---

### Post by bpt on 2006-06-17
Done it using sudo pmount -d /dev/fd0. Will it be mountable form now on or do I have to repeat this procedure each time I boot up?

---

