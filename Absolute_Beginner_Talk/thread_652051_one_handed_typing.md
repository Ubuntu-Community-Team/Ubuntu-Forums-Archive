---
title: "one handed typing?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by akimatsu123 on 2007-12-28
is there any free ways to one handed typing in linux? as in a program that lets me to this, without having to buy a new keyboard. 

the method where u press the spacebar and it maps the keyboard by its midline would be nice. i believe its called half-qwert or sth? im not sure. 

if you know where, places to learn how to type with one hand with the suggested keyboard would also be nice. 

thanks in advance

---

### Post by Dr Small on 2007-12-28
I thought you could type single handedly with dvorak. Maybe not.

---

### Post by PPAAUULL on 2007-12-28
What do you mean typing single handedly can't you just type with one hand on a normal keyboard?

---

### Post by akimatsu123 on 2007-12-28
yeah except its very slow. 

ive discovered the left-handed dvorak method comes with ubuntu. anyone know where i can get a tutorial?

thanks

---

### Post by tgalati4 on 2007-12-28
If you do a search in the forums, you will find techniques for "folding" the keyboard in half using a remapping.  I stumbled on it when trying to reprogram my multimedia keys.

---

### Post by akimatsu123 on 2007-12-28
where would i find that? that should i search? i searched "fold keyboard" "remap keyboard" and a few others without any success

---

### Post by joincamp on 2008-02-07
Bump.

I am also looking into this and have been hitting brick walls everywhere.  Windows has about 14 autohotkey scripts that do this, but every linux way I see is not quite what I want, or is no longer supported.

[Mirrorboard]("http://blag.xkcd.com/2007/08/14/mirrorboard-a-one-handed-keyboard-layout-for-the-lazy/") is by far the easiest to set up that I have seen, but it is not as transparent and nice as the autohotkey implementations.  Although you can change the modifier key to be whatever you want, you cannot use space as both a modifier and spacebar concurrently.  I have found that to be the easiest way, as many others have too.

The xkcd page lead me to [http://repetae.net/computer/hk/](http://repetae.net/computer/hk/) and [http://lists.canonical.org/pipermail/kragen-hacks/2002-July/000351.html](http://lists.canonical.org/pipermail/kragen-hacks/2002-July/000351.html)

The first is console only and has been removed because Matias is trying to uphold their flimsy patent.  The second looks perfect, except I couldn't get it to work.  I had to manually edit the code because it was a different version.  Most of it looked the same, so I thought it would work, but I'm not sure why it didn't.  I think it may have something to do with xkb overriding it.

I am going to spend the day looking into how i can make this work.  I'll let you know if I find anything.

EDIT:  I have made progress on this.  Instead of patching XFree86 in xserver-xorg-core, I had to patch kbd in xserver-xorg-input-kbd.  Once I sort out the bugs (same as on the canonical list) and get it to my liking, I will post the patch and instructions.  If anyone has any ideas for how to fix the bug or add a activate/deactivate setting/combo, please post it.

---

### Post by Mercedes300 on 2008-06-09
Have you got anywhere with this? this is verry interesting to me as well.

---

### Post by joincamp on 2008-06-09
> **Mercedes300 said:**
> Have you got anywhere with this? this is verry interesting to me as well.

I actually completely forgot about this.  Once I get back to the computer I was working on it, I'll see if I can finish it or post my commented code.

---

