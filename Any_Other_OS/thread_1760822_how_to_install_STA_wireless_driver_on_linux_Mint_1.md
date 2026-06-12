---
title: "how to install STA wireless driver on linux Mint 10 KDE"
date: 2011-05-17
forum: Any Other OS
---

### Post by ZomZilla on 2011-05-17
i recently downloaded linux mint 10 KDE  because i have always loved mint and i quite like kde. i had problems installing this driver before but i recently found a .deb that does it easily in ubuntu.

when i try it in Mint however: there is a huge long list of dependencies that need to be satisfied (i never have to do this in ubuntu: just add dkms) and it says error downloading (well obviously: i have no internet connection)


does anyone know how to sort this? i could try and locate a .deb for each of the 100+ dependencies but i'm positive there is a way to do it offline.

just to stress: i KNOW i need the sta driver
                       i have no way of connecting to the internet except through wireless in ubuntu
                       i am on a 64 bit OS


thanks in advance as this is driving me round the bend

---

### Post by Perfect Storm on 2011-05-18
Moved to Other OS/Distro Talk.

---

### Post by manzdagratiano on 2011-05-19
I use the broadcom sta driver too, and on my Slackware install, the only option is to compile the official package. But that is a very easy process, and the README file is extremely well written. Can you try doing that, and report if it works (just google "broadcom sta" and download the 64-bit package)? The wireless is my main source of internet as well.

I believe all you need to make that package is to have the linux-sources installed in /lib/modules.

---

### Post by ZomZilla on 2011-05-21
thank you sir!

i tried again and it worked so all is well :)

---

### Post by manzdagratiano on 2011-05-23
> **ZomZilla said:**
> thank you sir!

i tried again and it worked so all is well :)

Ah! Glad to be of any assistance! :) I know the feeling when the wireless does not work, and when you get it to work!

---

