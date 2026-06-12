---
title: "Problem with Boot Screen"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by L1nux01D on 2007-05-22
Hello,Everyone!!I met a problem on my way.I reinstalled Windows,and when I restart my PC it don't show me the boot screen where I choose my Oeprating System.What's the probelm??I am sure that I have Linux on my PC,but I can't load him.

---

### Post by Sparkster185 on 2007-05-22
My guess is that windows edited your boot loader (grub, maybe?) and only put itself in the list of OS'es.  You probably need to manually edit that grub table.  How, I'm not sure, sorry.

---

### Post by L1nux01D on 2007-05-22
Well......Thanks for that.
But know anyone how to edit this grub table???

---

### Post by matburton on 2007-05-22
What has happened is that windows has overwritten Grub.

Windows doesn't play nice and will do this every time you reinstall it.

Don't worry though, you can reinstall grub using the live CD
Take a look at [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=24113") thread and personally I'd use the second method.

Did you have windows before? If not then you'll have to add a windows entry to the grub menu.

If you need any more help then shout ;)

---

### Post by L1nux01D on 2007-05-22
Sure I had Windows before.Thanks for the link,I'll try to catch up something there.Thanks again!

---

