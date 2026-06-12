---
title: "Could'nt find my video drivers.."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by dungeonmas124421 on 2008-03-17
Its been a couple of days I started with Kubuntu 7.10.Everything is going smoothly right from handlin dependecies problem to downloadin correct packages via Adept.

But my screen flickers a lot (screen res. 1024X768 and freq 85 hz) and the vlc player couldnt properly render the video, as if proper video drivers are not installed.
I m using MSI K8MM-V (VIA K8M800-CE + VT8237R Chipset) with AMD Athlon 64 bit 2800+ processor and LG700E CRT Monitor.

Please suggest proper drivers or any solution to the above problem..:confused:

---

### Post by Ub1476 on 2008-03-17
Post the output of:

```
lspci | grep VGA
```

---

### Post by forrestcupp on 2008-03-17
It sounds like you are have an ATI video card and are using the proprietary drivers while running Compiz, or video effects.  Is that right?  If so, look [here](http://ubuntuforums.org/showpost.php?p=4532372&postcount=10) for a fix on video flickering.  

If not, that possibly may help anyway, but we need more info to fix the problem.

If my speculations are right, you can fix video flickering, but not flickering in opengl stuff.

---

### Post by dungeonmas124421 on 2008-03-17
dungeon@dungeons-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA A                                                              dapter (rev 01)

---

### Post by Ub1476 on 2008-03-17
Make sure VIA is selected as the driver in xorg.conf. There should be a GUI to do this (in Ubuntu it's System>Administration>Screens & Graphics). Remember to "test" the driver before you apply it!

If this is not the issue, see [here]("http://ubuntuforums.org/archive/index.php/t-636368.html").

---

