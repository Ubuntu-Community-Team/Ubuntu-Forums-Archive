---
title: "VNC how to (Not start new seasson)"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-06
Ok so I've got a xubuntu that I want to access and a xubuntu machine that I want to access from. How ever I would like access from windows as well.

I want to VNC to the xubuntu machine but I don't want it to start a new seassion. I want to see and control what you would if you where there locally.

I know you could do it with kubuntu but I don't want to install any KDE app's if I don't have to and I dont even know if it will work.

Also not that I will be looking into putting myth TV onto that box and that will be mainly what i want to controll remotely so if there is away to do that that might have to do. but what i really want is to VNC it.

Also i would like if possible if the machine is not loged it. still be able to VNC it and see the login screen.

Any help will be awesome.

---

### Post by snakyjake on 2006-10-07
Nomachine's FreeNX might be an option for you.  VNC has required me to be logged in first, plus there's no security or compression with VNC.

[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

---

### Post by cwaldbieser on 2006-10-07
> **guysmiley25 said:**
> Ok so I've got a xubuntu that I want to access and a xubuntu machine that I want to access from. How ever I would like access from windows as well.

I want to VNC to the xubuntu machine but I don't want it to start a new seassion. I want to see and control what you would if you where there locally.

I know you could do it with kubuntu but I don't want to install any KDE app's if I don't have to and I dont even know if it will work.

Also not that I will be looking into putting myth TV onto that box and that will be mainly what i want to controll remotely so if there is away to do that that might have to do. but what i really want is to VNC it.

Also i would like if possible if the machine is not loged it. still be able to VNC it and see the login screen.

Any help will be awesome.

Try the x11vnc package.  Running it should export your current session.  You may want to configure the server to lister to localhost and then use ssh to forward the ports from your client (using PuTTY or a similar program) if you are concerned about snooping.

---

### Post by guysmiley25 on 2006-10-10
Chears I got x11vnc working perfectly. I also got it starting on boot. But does anyone know how to get it to start on boot with a password cause at the momnet it does not. Even thow its only avaible on the LAN i would still like a password.

---

### Post by krunge on 2006-12-12
See the -rfbauth and -usepw options here:

[http://www.karlrunge.com/x11vnc/#faq-passwd]("http://www.karlrunge.com/x11vnc/#faq-passwd")

---

### Post by guysmiley25 on 2006-12-30
Ok so I used to have x11vnc starting on boot, but now i've done a reinstall and can not remember how I did so. I think I used xinet but I don't really know how that works.

Can anyone help me out?

---

### Post by guysmiley25 on 2007-04-19
Ping on that

---

