---
title: "Restore xorg to original"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-06-05
Please help I would like to restore Xorg to original as I could not get my Nvidia  Geforce fx 5700 le to install so now I have downgraded to a Nvidia Riva TNT 64mb in order to get 3d graphics. So here is my problem I need to remove all of the nvidia drivers I installed to get my other gaphics card to work. Any help is greatly appreciated.

---

### Post by Crafty Kisses on 2007-06-05
To recover your Xorg.conf file you type:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

---

### Post by fongs on 2007-06-05
> **Codename said:**
> To recover your Xorg.conf file you type:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

Tanks for help  tryed that and got back 
~$ cp /backupdir/xorg.bak /etc/x11/xorg.conf
cp: cannot stat `/backupdir/xorg.bak': No such file or directory
fongs@fongs-desktop:~$

---

### Post by jfinkels on 2007-06-05
The above suggestion is only a guide if you have previously backed up your /etc/X11/xorg.conf file.

To reconfigure your X server, try the following:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by fongs on 2007-06-05
great configured xorg now what to do next.

---

### Post by jfinkels on 2007-06-05
> **fongs said:**
> great configured xorg now what to do next.

...enjoy?

What do you want to do?

---

### Post by fongs on 2007-06-05
i wish to install the graphic driver maybe you could help me.

---

### Post by kevdog on 2007-06-05
Reboot computer to see the changes!!!!

---

### Post by fongs on 2007-06-05
rebooted now i have  better resolution thank you . but I really would like to see desktop effects work.

---

### Post by jfinkels on 2007-06-05
> **fongs said:**
> rebooted now i have  better resolution thank you . but I really would like to see desktop effects work.

Perhaps you would be better served if you created a new thread, and described your specific problem as detailed and as clearly as possible.

---

### Post by fongs on 2007-06-06
> **jfinkels said:**
> Perhaps you would be better served if you created a new thread, and described your specific problem as detailed and as clearly as possible.

Yes ok thanks for help

---

