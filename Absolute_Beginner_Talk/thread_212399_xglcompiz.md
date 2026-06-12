---
title: "xgl/compiz?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-09
i had followed instructions to download and install the XGL/Compiz thing.

As i was running things in terminal alot of the plug ins and what not failed and then when i logged in as XGL it was very very laggy and unworkable.  Also wheni checked the compiz list i didnt even have all the proper plug ins.

Is there any way to delete all of the XGL/Compiz components and attempt to try it again?

My goal is to have transparent windows.

---

### Post by reacocard on 2006-07-09
what tutorial did you use? also, if you have intergrated/low-end graphics, you may want to use aiglx instead. i have intergrated intel 915 graphics, and XGL was awful. aiglx works perfectly, with all the effects. See "Compiz Eyecandy" in my sig for a bunch of tutorials on installing xgl, aiglx and compiz

---

### Post by IrishGangsta on 2006-07-10
Um, how can i check my graphics.
And i don't feel like looking for the tutorial.
It didn't turn out right though.
Should i follow your compiz eyecandy tutorial?

---

### Post by IrishGangsta on 2006-07-10
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

That is the tutorial i followed.
I was wondering if i can uninstall all of that and just follow your tutorial for aiglx

---

### Post by reacocard on 2006-07-10
yeah, just uninstall the packages with this command:

```
sudo apt-get remove xserver-xgl libglitz-glx1
```

for the config changes you made:

if you used method A, do
```
sudo rm /usr/bin/startxgl.sh
sudo rm /usr/share/xsessions/xgl.desktop
```
to remove that option.

if you used method B, don't worry, you'll be overwriting it anyway.

also be sure to undo whatever you did to enable compiz. don't worry about the packages, they're fine, just remove the script or startup options you added.

now just follow this guide: [http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)
i'd reccommend compiz-vanilla, it seems to be more stable, although it doesn't have as many features.

---

