---
title: "Server with GUI"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by ys_rock on 2005-10-24
Hi All
How do i setup a server installation with a GUI interface?
GNUME / KDE and not GRUB.

Thanks
yoav

---

### Post by nocturn on 2005-10-24
[QUOTE=ys_rock]Hi All
How do i setup a server installation with a GUI interface?
GNUME / KDE and not GRUB.

Thanks
yoav[/QUOTE]

Do the server install and apt-get install the wanted packages (gnome).
Also, you may need to get xorg.

---

### Post by ys_rock on 2005-10-24
I don't know how to do that,
i write: app-get install xorg
and i get command not found
i'm logged in as a root user

---

### Post by Peter76 on 2005-10-24
[QUOTE=ys_rock]I don't know how to do that,
i write: app-get install xorg
and i get command not found
i'm logged in as a root user[/QUOTE]

Hi, after the server install, you firts have to edit /etc/apt/sources.list and uncomment the universe repository.
Then:
sudo apt-get update
sudo apt-get install x-window-system-core gdm icewm 
and continue with anything else you' like to install....
And don't log in as root, use sudo!!!

Good luck

---

### Post by ys_rock on 2005-10-24
Thanks for all the help
Another Q: how do i edit the source.list file?
edit source.list
i got no writing permission
--yoav

---

### Post by Peter76 on 2005-10-24
[QUOTE=ys_rock]Thanks for all the help
Another Q: how do i edit the source.list file?
edit source.list
i got no writing permission
--yoav[/QUOTE]
 
sudo vi /etc/apt/sources.list
You probably don't know vi, so first:
vimtutor
This gives you a good intro to vi. Others use nano a lot, but i don't know it.
Anyway, the only thing you have to do is uncomment the universe repository.
( every line starting with a # is a comment )
 Good luck

---

### Post by Wolki on 2005-10-24
[QUOTE=ys_rock]Hi All
How do i setup a server installation with a GUI interface?
GNUME / KDE and not GRUB.
[/QUOTE]

You can install the full ubuntu/kubuntu. "Server" install installs just the basic system and is thus optimal who want to get a low-resource server (and thus without a GUI), normal install installs those packages and a GUI. If you want a full-featured GUI, i'd rather suggest that instead of installing all the packages by hand.

"sudo apt-get install ubuntu-desktop" or "sudo apt-get install kubuntu-desktop" will install the full desktop package for Gnome/KDE on a server install.

---

