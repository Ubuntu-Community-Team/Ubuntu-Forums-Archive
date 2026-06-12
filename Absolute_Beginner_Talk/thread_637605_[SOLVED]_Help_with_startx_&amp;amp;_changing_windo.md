---
title: "[SOLVED] Help with startx &amp;amp; changing window manager"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Iceni on 2007-12-11
Hi!

I have a laptop with ubuntu 7.10, but I usually use openbox. I removed GDM and when I type startx it boots into gnome. How can I change this? 


Another question:

Can I disable the NFS service? It hangs on boot, but I don't want to remove it before I know what it does. Is it something like samba, because I already have that running..

Thanks in advance.

---

### Post by gazj on 2007-12-11
edit or create a file in your home directory called .xinitrc

comment out or delete any gnome lines
and add this line

```
exec openbox-session
```

when you type startx it will run what ever is in the file .xinitrc
when all commands in .xinitrc have exited then the x will stop

if .xinitrc does not exsist, startx will refer to a system wide xinitrc usually found somehwere in /etc/X11


NFS is a linux file sharing service, which for linux to linux sharing works better imo, but if you are only sharing files to ms windows machines then you can unistall nfs using the following

```
sudo apt-get remove nfs-common
```

---

### Post by jaybombalous on 2007-12-11
...or use 'slim'

U can check the repository, I use arch linux so I can't, but issue this command and see what happens.
```

sudo apt-get install slim
```

if it installs then u will have to google for how to set it up, its rather easy though and changing themes for it is even easier.

[http://wiki.archlinux.org/index.php/SLIM#Single_Environments](http://wiki.archlinux.org/index.php/SLIM#Single_Environments) <-- yes I know, its not ubuntu, but the exact same procedure will work. U need to edit the .xinitrc file in your home directory.

---

### Post by jaybombalous on 2007-12-11
[http://slim.berlios.de/](http://slim.berlios.de/)

---

### Post by Iceni on 2007-12-11
Thanks a lot, worked like a charm:)

Slim looks nice, I'll try it.

---

