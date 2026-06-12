---
title: "Ububtu Desktop as Server"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by skewh on 2006-10-13
Hey all,
I want to run LAMP along with FTP server, and a GUI like Ubuntu Desktop. Will Ubuntu Desktop do fine for what I want to do, or do I have to use Ubuntu Server? Thanks!

---

### Post by IYY on 2006-10-13
It's perfectly fine. Of course, you might want to turn off the GUI when you are not using the computer so that more CPU cycles, memory and bandwidth is left for the server functions (of course, this is just a suggestion. It'll work fine with the GUI on.)

---

### Post by PriceChild on 2006-10-13
Ubuntu Desktop install is just the same as the ubuntu server install but with the ubuntu-desktop metapackage.

This installs various gui apps such as the xserver and other graphical apps.

To stop the x server to save on resources, ctrl+alt+F1 log in and then ```
sudo /etc/init.d/gdm stop
```

---

### Post by KingBahamut on 2006-10-13
Honestly , if you could actually get used to it, Id recommend using fluxbox or xfce as your desktop UI for a server. Both are extremely lightweight and have very little or no overhead. 

to get xfce 
sudo apt-get install xubuntu-desktop

to get fluxbox 
sudo apt-get install fluxbox fluxconf

---

