---
title: "Beryl or compiz"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by krishnavamshi24 on 2007-01-06
Im having 845 graphics chipset and im on Dapper,Can i Install beryl or compiz...infact i have had it installed but the window borders dissappear .Can anyone help (compiz or Beryl) anyone will do......](*,)

---

### Post by zgornel on 2007-01-06
You can use both beryl or compiz, personally I prefer compiz, I found it more stable than beryl. It's up to you.

---

### Post by Sasa_Ivanovic on 2007-01-06
Don't use any of them, it will just screw up your xorg.conf. And you will have to reinstall Ubuntu like i did. They just bring trouble!!!

---

### Post by zgornel on 2007-01-06
> **Sasa_Ivanovic said:**
> Don't use any of them, it will just screw up your xorg.conf. And you will have to reinstall Ubuntu like i did. They just bring trouble!!!
You should have backedup ;) .

---

### Post by Sasa_Ivanovic on 2007-01-06
I did, but it modified some other files which i couldn't keep track off. In the end Beryl worked with aiglx rendering. direct rendering of glx was disabled and i couldn't load any 3d games.

So i was pissed off, and reinstalled the whole system...

---

### Post by kinematic on 2007-01-06
if you card supports xgl or aiglx i'd say just try it.
be sure to make a backup of your xorg.conf just in case something goes wrong,
personally i prefer aiglx.....why install another x server when xorg has composite capabilities build in from version 7.0 and upwards.
so my advice is go ahead ;)

---

### Post by macogw on 2007-01-06
try 
sudo apt-get install emerald-themes
Then you can click on the beryl manager in your notification area and click "select window decorator > Emerald" (if its not chosen) and you can go to the Emerald editor up there too.  That might get your window borders back.

---

