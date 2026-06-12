---
title: "ubuntu server help!"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by E~dub on 2006-02-23
Yes im a newbie and honestly i just started learning about linux...i just built a linux server using ubuntu 5.10 and i was wondering if i could add the normal ubuntu desktop to the ubuntu server if that makes any sense?

---

### Post by knalle on 2006-02-23
sure, nothing stops you from using the server as a desktop too. professional servers is usually installed "headless" that is without a desktop, but that is to minimize the number of packages and thus potential bugs to patch

---

### Post by Iowan on 2006-02-23
Without splitting hairs, realize that the primary difference between a server and workstation install IS the desktop.  (OK, the default server install doesn't include email, Firefox, or games...)  So not only could you use the server as a desktop, you could install Ubuntu as a workstation and use it as a server.

---

### Post by E~dub on 2006-02-23
but if im running ubuntu server how do i add the desktop to it?reboot and install  desktop from the cd?

---

### Post by lettas on 2006-02-23
If you're willing to use..

gnome: 
sudo apt-get install ubuntu-desktop

KDE:
sudo apt-get install kubuntu-desktop

xfce:

[https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

---

### Post by Eternal Blade on 2006-02-23
On a server it isn't always bad to have a gui.  There are some tools that only work with a graphical interface, plus it is much easier to use at first.  Also, as long as you don't start gnome/kde/etc at boot up there shouldn't be any performance lag.

---

