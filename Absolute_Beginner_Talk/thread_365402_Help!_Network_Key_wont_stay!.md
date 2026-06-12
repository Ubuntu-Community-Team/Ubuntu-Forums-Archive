---
title: "Help! Network Key wont stay!"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Halonut1 on 2007-02-19
Ok i (finally) figure out how to set up my linksys card and router decently, and it works fine on the windows part of my dual boot but it wont keep the network key in it when i reboot! it justs erases it and i have to enter it again to use it. is this a bug or is there a way it cant be helped? i dont know how to change my routers network key so if i can just get a fix for it that would be great, anyone have this problem?
Sorry, forgot to put i am running ubuntu 6.06 with a linksys G router and a B wifi card. also linksys.

---

### Post by mctk on 2007-03-12
Do you have the gnome-keyring program(I would assume it's installed by default)?  In a terminal try running ```
gnome-keyring-manager
```

  If you have it, you might try deleting the info about your current wireless network and setting it up again.  See if the keyring will grab the password.

If you don't have it, install it with your package manager, delete your wireless network's info and set it up again.  

You should be able to access your routers control panel by pointing your browser to:

192.168.0.1

---

