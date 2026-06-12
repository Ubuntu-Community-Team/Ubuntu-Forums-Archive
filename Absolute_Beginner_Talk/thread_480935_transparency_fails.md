---
title: "transparency fails"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-06-21
why is it that transparency for me in ubuntu is false. it doesnt actually make things transparent but rather loads the background, so when i more the transparent window (terminal) you cant see anything beneath except wallpaper and it lags. also i installed screenlets and everything thats supposed to be transparent is black. happens with all transparent apps. in xp, i always had transparency, so its not that my hardware isnt capable. how can i fix this? i rather like eyecandy =]

---

### Post by Hobo Joe on 2007-06-21
Paste the ouput of:
```

glxinfo

```

Are you trying to use Beryl?

---

### Post by supersonicdarky on 2007-06-21
thnx for crashing x >_> (the same thing happened as when you press **ctrl+alt+bksp**)

and no, i am not trying to use beryl

---

### Post by zodmaner on 2007-06-21
You ***must ***have compositing window manager like Compiz or Beryl enable in order to have true transparency. 

Ubuntu already come preinstalled with Compiz. Try enable the Desktop Effects (which is Compiz) in **System >> Preferences** and check if transparency works.

If it still didn't work, then try install Beryl via **Applications >> Add/Remove** and see if it's work. Beryl is in System Tools categories. Install ***both*** the Beryl Manager and Beryl Settings Manager, or else Beryl won't work.

Also, it would help us a lot if you tell us what graphic card you are using, and keep us posted on how you're doing.

---

### Post by supersonicdarky on 2007-06-21
- i dont have the desktop effects thing in the menu because i thought it caused gnome to be faulty [[More Info](http://ubuntuforums.org/showthread.php?t=438469)]
- i had beryl installed before, but removed it because it crashed x or i got a white screen of death [[More Info](http://ubuntuforums.org/showthread.php?t=429050)]
- gpu: SiSM760GX [[Source](http://reviews.cnet.com/laptops/acer-aspire-5000/4507-3121_7-31394073.html)]

---

### Post by supersonicdarky on 2007-06-22
bump...

---

### Post by diatribe on 2007-06-22
go to xfce settings select window manager settings and click compositing i think

---

### Post by supersonicdarky on 2007-06-22
where are the xfce settings located?

---

