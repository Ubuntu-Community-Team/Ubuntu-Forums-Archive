---
title: "Dual Boot"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by blublu on 2007-04-12
[FONT="Century Gothic"]I have Ubuntu and MS XP Pro on my computer. When using Ubuntu I cannot access my Windows folders on the computer. How do I get around this.[/FONT]

---

### Post by KitChy on 2007-04-12
I'm gonna guess that your windows partition is NTFS. So follow this guide to access the files:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by ola on 2007-04-12
Hi! Or if you just want to mount it read only you can check this out: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Good luck!

---

### Post by blublu on 2007-04-12
Thanks but ignoramous dosent know what to do in part with code :
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0
I have succeeded in creating my mount point but do not know what should be written in <your partition>
Thanks again

---

### Post by annda on 2007-04-12
it's right there in the guide: copy and paste this in the terminal (CTR+SHIFT+v or middle-click):

```
sudo fdisk -l | grep NTFS
```

you will see it's something like hda1 or sda2 or something similar.

---

### Post by blublu on 2007-04-12
When I wrote hda1 it said "permission denied"
How do i alter this.

---

### Post by annda on 2007-04-12
do you mean you cannot save the file? in that case, make sure you run this command to modify it:
```

gksu gedit /etc/fstab
```

---

### Post by confused57 on 2007-04-12
Here's an excellent guide for mounting various filesystem types:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

It would be something like:
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf8,umask=0222
```

then you should be able to use nautilus to navigate to your /media/windows folder

---

### Post by blublu on 2007-04-12
Thanks confused57 , not confused anymore.

---

### Post by annda on 2007-04-12
just remember that the drive will not be mounted when you reboot (you will need to issue the sudo mount ...... command manually again). if you want it to be mounted automatically, you still need to edit fstab.

---

