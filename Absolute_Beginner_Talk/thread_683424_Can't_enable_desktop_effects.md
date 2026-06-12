---
title: "Can't enable desktop effects"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-01-31
Hi,

i recently tried to install another graphic driver, my screen went blamk and I had to reset the graphic driver with

sudo dpkg-reconfigure -phigh xserver-xorg 

So, now the display is OK, but in Appearances I can't enable anything but NO visual effects. I had compiz fusion running before, AWN all that doesn't work now.

I tried running 'compiz' and such in the Terminal but that won't have any efffect.

What can I do to set Viesual Effects again to custom?

Thanks

Andreas

---

### Post by seventhc on 2008-01-31
try this,
right click on desktop>change desktop background>visual effect> set it to custom.
maybe it got reset to none

---

### Post by Djalmahal on 2008-01-31
No,

that trick didn't work.
I looked up some thread, does xserver-xgl play into the whole thing, i wasn't installed right now, i installed it now, how do I start it.

I repeat, everything worked this morning, the resetting of the graphic driver started this problem

Andreas

---

### Post by Bluestick on 2008-01-31
Do you have correct Video drivers installed?
 i had that hapend to me while changing the video drivers, then after restart no visual effects nothing, so i re-insalled the whole UBUNTU, and i did not mess with the drivers..

---

### Post by Djalmahal on 2008-01-31
Well,

i know that the video driver that runs now again (intel -experimental modesetting driver) is the one that works, it ran before with the whole compiz and it runs now, whateer else i tried to intall messed the display up badly. There are certain issues with it, like that when I run a video and do the cube turning, the videoscreen just shows blue, not the actual video (that's rather minor), also Google Earth has problems with having a window above the main Google Earth window, it blinks a lot.

But basically the driver works and everything else doensn't. 

Do you mean you reinstalled the whole Ubuntu, I'd rather not do it at this point.

Andreas

---

### Post by oedha on 2008-01-31
what if only sudo dpkg-reconfigure xserver-xorg
no need xserver-xgl since you said it is intel

~E~

---

### Post by Djalmahal on 2008-01-31
Ok, i ran that line, gave al the answers,restart but nothing changes.

Further ideas

Andreas

---

### Post by jan quark on 2008-01-31
try to change the session to xclient script during login

and try to enable the effects once more

---

### Post by Djalmahal on 2008-01-31
NO, again, this doesn't change anything, i can't enable desktop effects other than none.

Now, the tricky thing is I it worked, before I tried to improve my graphic card driver it all worked nicely.

Andreas

---

