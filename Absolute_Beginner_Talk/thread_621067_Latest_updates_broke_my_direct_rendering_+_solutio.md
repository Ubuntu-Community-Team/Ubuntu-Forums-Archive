---
title: "Latest updates broke my direct rendering + solution"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-11-23
Im posting incase anyone else has an ATI radeon mobility x2300 HD and are suddenly having direct rendering probs today, and what i did to fix it.
I downloaded the latest updates last night, I already had ati driver 8.42.3 (the first ATI to use aiglx)
Not sure what the updates did or weather they installed a newer driver, but it set my system back to using indirect rendering. (found out by typing "glxinfo |grep direct")

To fix it i used envy (again) to install the 8.42.3 driver again and rebooted. All was fine, have got direct rendering again. I know Aiglx is working now properly cos i can get compiz and direct.

Is this going to be a regular thing with the updates and was there a new ATI driver released?

---

### Post by derby007 on 2007-11-24
I have an ATI X1300 Pro card. I enabled the restricted drivers, installed fglrx driver, then XserverXGL and I now have all the compiz parafanalia/wizardry. But.......I dont have direct rendering ! 
I think fglrx gets rid of that. Also: if I now do glxgears, the system logs out/crashes and puts me back at the log-in screen !!

---

### Post by dgrafix on 2007-11-24
Have you tried using envy to install the latest driver? Worked wonders both times on mine.

Also, make sure you have not got xserver-xgl installed (try apt-get removing it if you do), Its not needed with the latest driver, Xgl will disable direct rendering altogether if installed (as i understand it)

I have basically the latest driver installed, no XGL and i get direct and compiz at the same time.

---

