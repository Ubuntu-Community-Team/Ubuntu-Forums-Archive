---
title: "Couple of Kubuntu questions"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by mbgb14 on 2007-02-01
Hello! Couple questions :D

1) How do edit which programs load on startup?
2) How do I load new KDM themes?
3) Where is the *regular* KDE control panel? 


Tx alot.

---

### Post by thelocust on 2007-02-01
**To edit what programs start up go to /home/<profile>/.kde/startup applications and make a link to the executables you want to load on start-up, you can also put scripts here. I'm not a hundred percent on the folder name at at work but it's something like that. For KDE Themes and control panel type kdesu kcontrol in to the terminal I if it gives you an error install it in Adept. Good luck and hit me up with anymore questions if you got them.**
[B]
Also check out
[kde-apps]("http://www.kde-apps.org/")
[kde-look]("http://www.kde-look.org/")

If you haven't already.[/B]

---

### Post by mbgb14 on 2007-02-01
Awesome thanks. I figured out the KDM Themes thing. You have to apt-get kdmthemes. Oddly, it isn't installed by default. Then you go into kcontrol. 

:D

And the startup apps list is in ~/.kde/Autostart

---

### Post by %hMa@?b&lt;C on 2007-02-01
if you dont want the programs that were running when you shutdown to run when you re-login, go to system setting>advance>session manager

---

