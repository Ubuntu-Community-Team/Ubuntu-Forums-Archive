---
title: "Compiz  versus Beryl performance"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-23
I had Beryl on Feisty -- now I have Compiz on Gutsy.
Seems Beryl was faster.

Anyone note this?

Carl

---

### Post by jualin on 2007-10-23
I noticed something similar in the beginning, however after using the compiz-config-settings manager and tweaking the speed, it seems to me that it is the same. But I still feel that the rotary cube was running a little bit faster in Beryl than in Compiz Fusion. Maybe is just my imagination, :lolflag:

---

### Post by cwmoser on 2007-10-23
Do you have any tweaking hints for Compiz that you would like to share?

I would like to improve the performance.

Thanks,

Carl

---

### Post by Vadi on 2007-10-23
Click here: [apt:compizconfig-settings-manager]("apt:compizconfig-settings-manager").

After that, head to System - Preferences - Advanced Deskop Effects Settings, and have a blast.

The option that'll help is general settings - display settings, and texture filter. Also, keep in mind that transparency is pricey, so see if you can eliminate that if it's not needed.

---

### Post by rundee_f on 2007-10-23
i'm currently installed beryl and after that i also installed copiz-fusion... first time i use beryl, im hsving no problem at all and heaving some good times with it, but i dunno since when, when i use beryl, i open a new window (e.g Home Folder) it show up behind other window(s). I never experienced this before with beryl or when i didnt use any desktop effects (Beryl and Compiz deactevated).

i had problem with my compiz fusion,, when i run "compiz  --replace", my window lost its border and title bar... it disturbed me so i end its process and session but they still wont come back,, so i restarted my laptop.. :((

hhhh.... help please...

---

### Post by vertexoflife on 2007-10-23
This is caused by Window-Decorator.

Under compizconfig-settings-manager go down to the Workarounds Part, enter that and uncheck Legacy Fullscreen Support.

---

### Post by rundee_f on 2007-10-24
nope.. nothing's change... is it possible that this problem caused by my instalation process? i did the re-installation for almost 3 times, but they still the same.. please read my other post [http://ubuntuforums.org/showthread.php?p=3616166#post3616166](http://ubuntuforums.org/showthread.php?p=3616166#post3616166)

---

### Post by Sef on 2007-10-24
> Compiz versus Beryl

CompizFusion is what you should use.  Beryl is no longer being maintained.

---

### Post by rundee_f on 2007-10-24
yup sef... now i've been uninstalled my beryl.. and install compizfusion under the help from [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) but i find it didnt work on my feisty... no desktop cube, no rotating desktop, wobbly effects and completely nothing.. and strangely i found my window bar missing after i did ALt-Tab > "compiz --replace"...

---

### Post by rundee_f on 2007-10-24
i solved my cases at [http://forlong.blogage.de/#blogentry_451](http://forlong.blogage.de/#blogentry_451)

thank you so much... it works!! Love my Ubuntu more than before! :D

---

### Post by Sturmeh on 2007-10-24
FOR DRAMATIC IMPROVEMENTS ON COMPIZ...

Disable Transparency where possible. ( On the cube, this brings my FPS above the 80 mark. )

---

