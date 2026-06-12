---
title: "How to install GUI"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by tracek1 on 2006-04-14
Hi!

Due the unsufficient amount of space on my HDD I had to install Ubuntu 5.10 with 'server' option. I have downloaded and installed from repositories xserver-xorg with xserver-xorg-driver-ati (i got Radeon 9000 Mobile) and xfce4 environment. Now my question is: how to make it working??

When I type:
"startxfce4" I get:
*starting X server*
*X: cannot stat /etc/X11/X (No such file or directory), aborting*
*Connection refuse (errno 111): unable to connect to X server*
*No such process (errno 3): Server error*

if I type "startx" :
*xauth: creating new authority file /root/.serverauth.6813*
*X: cannot stat /etc/X11/X (No such file or directory), aborting*
*xinit: Server error*

Posts which I found on this forum related to this topic were saying somthing about 'xorg.conf' file. Well, I don't even have this file :).
What should I do? Please, don't say "sudo apt-get install ubuntu-desktop"!
Please help! 
...and sorry for my english, I'm really doing my best :)

---

### Post by malavar on 2006-04-14
try apt-get install xserver-xfree86 (i think)
and if you dont have xfonts 
apt-get install xfont-face

this is what i did recently on anold laptop that had like a1.7gb hdd

---

### Post by Monster_user on 2006-04-14
[QUOTE=malavar]try apt-get install xserver-xfree86[/QUOTE]
Xfree86 is a little old. It has since been surpassed by Xorg. I'm not sure if that is Xfree86, or if it is just an upgrade package, that installs Xorg.

apt-get install xserver
or
apt-get install xserver-xorg

---

### Post by az on 2006-04-14
sudo apt-get install x-window-system-core xterm

If you want to boot into a GUI. install gdm, too.

---

### Post by tracek1 on 2006-04-14
It worked!
I made a mistake by installing only certain packages from xserver insteed of installing them all. After that nice configurator appeared and sorted out everything. 

Thank you very much for your help!

---

