---
title: "help guys..i wacked it..!!!"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Balvinder25 on 2007-06-18
hi all,
          i am a newby to ubuntu and was just fidling with the services list and unticked an options for some system configuration and now i can get the damn thing up but everything else is working ok..please help as i use this start /stop by bue tooth device..:(

thanks in advance..

---

### Post by shearn89 on 2007-06-18
can you give details of where loading fails: is it at boot up, or is it when loading GNOME?

---

### Post by Crafty Kisses on 2007-06-18
> **Balvinder25 said:**
> hi all,
          i am a newby to ubuntu and was just fidling with the services list and unticked an options for some system configuration and now i can get the damn thing up but everything else is working ok..please help as i use this start /stop by bue tooth device..:(

thanks in advance..

If it's booting up at a black screen, you should try reconfiguring your X server file, and then backing it up.

---

### Post by Balvinder25 on 2007-06-18
hi all,
         thanks for the quick response guys ..i managed to fix it up..phew..:p..i read it in the forum list ...and run the following with the sudo rights,,aptitude reinstall dbus and it worked great...

thanks all for your concern..

---

