---
title: "RealPlayer 10 plugin error"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by jockjunior on 2005-12-11
Hello,
 I downloaded realplayer10 from real and installed it as per the instructions, It didnt show up on my menu but I sorted that but when I try to use BBC radio player I get helix. not in system path cannot use as embedded player or something like that. What have I done wrong? Also how do I uninstall realplayer as I think I put it in the wrong place ?  Its in my home dir.

thanks

Jock

---

### Post by bluevoodoo1 on 2005-12-11
I followed this guide today for installing realplayer 10 (have to scroll down a bit)

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
and 
[https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods)

and it works fine and it is in my apps > sound/video menu.

here's the code from the 2nd link that I used for the install. After downloading the file from real.com save it to the desktop, then follow the following code...

```

cd ~/Desktop
sudo apt-get install libstdc++5
chmod +x ./RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```

---

### Post by jockjunior on 2005-12-12
Thanks thats what I did , but I will try again


jock

---

