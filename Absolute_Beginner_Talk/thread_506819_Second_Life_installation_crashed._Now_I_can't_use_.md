---
title: "Second Life installation crashed. Now I can't use apt or synaptic"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-07-22
I was installed Second Life using this package I found on getdeb.net: [http://www.getdeb.net/release.php?id=1057](http://www.getdeb.net/release.php?id=1057)

I ran the .deb and it started the installation. it started to download the second life program, and then something happened, I'm not sure what, maybe my WiFi dropped or something, but the download just stopped, I left it for a while, but nothing happened.

So I tried to exit the installation process, and it just kinda froze up. So I force quit it.

then later when i tried to  sudo apt-get install a program, I got:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

so I ran 
```
dpkg --configure -a
```

and then when I tried to sudo apt-get install again I got

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.


I get the same message when I open synaptic or try and download and install updates.

so I tried to install the Second Life package again, and I get:

> The package may be corrupt or you are not allowed to open the file, please check permissions

I still get this message after re-downloading the package of getdeb

does anyone know how I can fix this?

---

### Post by happy-and-lost on 2007-07-22
Reinstall the .deb using dpkg, not Synaptic.

---

