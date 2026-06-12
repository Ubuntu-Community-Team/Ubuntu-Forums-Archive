---
title: "Adding a new cd to source.list"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by martinmanzana on 2006-08-20
I installed an ubuntu server on a laptop that has no connection to internet. I need the packages to get x-window-system running with a light windows manager like fluxbox. In the server cd I used to install ubuntu, the packages are not available. But I got an ubuntu desktop cd that has all needed packages to install x-window-system. ¿What line do I need to input into the sources.list file, so that aptitude looks for the packages in the desktop cd?

Thanks

---

### Post by meng on 2006-08-20
sudo apt-cdrom add

---

### Post by martinmanzana on 2006-08-20
Now that I have the packages added. Which ones should I install to get x-window-system running with fluxbox. Or do I need a connection to internet. Can I get the .deb files for xserver-xorg, xterm, and fluxbox from somewhere? Thanks

---

