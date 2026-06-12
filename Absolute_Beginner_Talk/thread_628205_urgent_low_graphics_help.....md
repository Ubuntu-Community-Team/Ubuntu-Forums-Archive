---
title: "urgent low graphics help...."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-12-01
i dont know what the hell happend... i was running ubuntu nicely on a second screen cause the screen of my laptop is ****** up.. still fixing it..*the piece arrives on 1 week* but something werid happend when i opened screen and graphics from administration.. it is running on low graphics mode.. and i dont know how to fix it

---

### Post by Ronjr on 2007-12-01
I just posted about this problem. I was trying to fix my mouse to use the back button and this happened to me.

I eventually found out how to fix it by going to system - Admin - Screens and Graphics. 

Click Graphics card and then just select your graphics card. I have onboard and I just selected the make and the closest model since it didn't have mine. Then it allowed me to change the resolution. I may have ctrl + alt + backspace I cant remember now. Just try it and see what happens. 

Hope it helps.

---

### Post by patchido on 2007-12-01
ok.... i runned the live cd so i could see what were the graphics it had.. tried to put them and wont let me.. >S what can i do?

---

### Post by Ronjr on 2007-12-01
I cant really help much I just installed ubuntu 2 days ago for the first time. I just happened to have the same problem but from a different angle about an hour ago.

---

### Post by patchido on 2007-12-01
anyone???? plz

---

### Post by Gone fishing on 2007-12-01
I had a similar problem I enabled  the second screen using Screens and graphics Manager , it enabled the second screen and made both screens 640x 480 which is useless. However, I had a back up of /etc/X11/xorg.conf file and simply deleted the new one and renamed the backup xorg.conf that took me back to where I was :)

I then enabled the second screen using gksu nvidia-settings (I'm using an nvidia card) and everything was great.

---

