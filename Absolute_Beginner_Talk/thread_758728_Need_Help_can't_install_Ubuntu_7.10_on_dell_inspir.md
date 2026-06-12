---
title: "Need Help: can't install Ubuntu 7.10 on dell inspiron 1520"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by TehDuke on 2008-04-18
hey guys,

i'm quite new to linux, and ive been trying to run ubuntu 7.10 on my dell inspiron 1520 laptop with little success. I tried the 64 bit and 32 bit version and in both instances, when i tried to boot from the Live CD, it didnt work. (The screen would turn off after loading the linux kernel)
My aim is to try to install Ubuntu on a USB flash drive so i can play around with it, without affecting my windows partition.

does anybody have any ideas of what i could do to fix this?

thanks in advance...

---

### Post by erlyrisa on 2008-04-18
could be as simple as booting the livecd with a ....

"normal screen resolution"

...ie

when the livecd boots, don't just press enter

theri is an option for starting in screen resolution compatible mode (in the age of widescreens this maybe a necessity for some computer screens)


...once your installed you should be able to fix (or ubuntu itself will find a Res the works) or update a driver.

--worse comes to worse you will have to setup you xorg.conf - inwhich case a little "hardcore" stuff maybe warranted.

---

### Post by zvacet on 2008-04-18
Press F1 ( it is help) and find where is safe grapfic mode.

---

### Post by TehDuke on 2008-04-19
I tried running the Live CD in safe graphics mode, but the same thing happens. Just after loading the linux kernel, the screen turns off, but i can still hear the CD drive reading the disc.

---

### Post by daberger on 2008-04-19
hmmm. if ur aim is to get a pen drive linux id recomend using an difirent system
if u want linux on the laptop u should dual boot with wubi. easiest way ever

---

### Post by zvacet on 2008-04-19
You may try alternate CD.

---

### Post by TehDuke on 2008-04-19
ok i just tried wubi, and it installed ok, and when i restarted I could chose to boot into ubuntu, but then the same thing happened and my screen turned off.

---

### Post by TehDuke on 2008-04-19
I dont know how I did it but i managed to boot into safe graphics mode. After my screen turned off when Ubuntu was loading, i waited a bit, and when nothing happened I mashed the keys on the keyboard hoping it would do something. Somehow it did, and a window opened up telling me that Ubuntu was running in safe graphics mode and it was giving me options to change screen resolution and other stuff. Since then I rebooted and I can't manage to get that window to open again.
Is there some kind of keyboard shortcut that I might have accidentally pressed that would have brought up such a window, and if so what is it?

I'm starting to think there must be a problem with the graphics card drivers.

---

### Post by daberger on 2008-04-20
i have a question for you now.
i tried putting my livecd into a tower and it did weird things with my screen turning it bright colors.
is this what happened with urs?

and srry i dont know the shortcut

---

### Post by TehDuke on 2008-04-20
No my screen just turned off. It wasn't just that the screen went black, it actually turned off but the laptop was still running and I could still hear stuff going on.

---

### Post by daberger on 2008-04-26
darn... ill see what i can do

---

### Post by fabianmejia on 2008-06-06
Hi I Installed the Ubuntu 7.10 on a 1520 machine as soon as that Ubuntu version was available. I only had issues with the soundcard.

I have created a small tutorial, maybe it can be helpful to somebody in the forums:

[http://fabianmejia.blogspot.com/2007/10/ubuntu-710-on-inspiron-1520.html](http://fabianmejia.blogspot.com/2007/10/ubuntu-710-on-inspiron-1520.html)

---

