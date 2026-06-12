---
title: "Live 5.1 Wireless Question"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by ssn771 on 2005-12-04
Ok I'm having a little trouble getting my wireless card to work.  I'm using a Dell laptop with a Intel 2200BG.  If I use the network configuration tool it shows a wireless connection and it lists the access point I want to connect too in the drop down box.  If I use iwconfig sometimes it'll look like its connected, but I can't ping anything or use firefox.  One thing is I'm not trying to connect to an accesss point.  I'm connecting to another computer that is running windows XP internet connection sharing.  So it needs to run in ad hoc mode I think, but I odn't know how to change it to that setting.  So far ubuntu looks really cool I just need to get the internet part of it working.  Thanks!

---

### Post by mlomker on 2005-12-04
You'll want to look at the help in **man iwconfig**.  The command is **sudo iwconfig wlan0 mode ad-hoc**, assuming that your interface is wlan0.  I'm not sure how to do it from the graphical interface...

---

