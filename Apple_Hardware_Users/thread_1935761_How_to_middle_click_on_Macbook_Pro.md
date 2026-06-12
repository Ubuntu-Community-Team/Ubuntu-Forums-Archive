---
title: "How to middle click on Macbook Pro?"
date: 2012-03-04
forum: Apple Hardware Users
---

### Post by daehenoc on 2012-03-04
Hi all,

I used the Ubuntu+mac ISO to install Ubuntu 11.10 on this Macbook Pro and it's great :)  Even figured out that a two-finger tap on the touchpad does a right click, cool :)

I don't know how to do a middle click (i.e. to paste highlighted text) - does anyone know if there is a default setting for this with the +mac version of the ISO, or do I have to configure something else to get a middle click working?

Thanks!

---

### Post by MisterGaribaldi on 2012-03-05
At a guess (and it's nothing more than a guess) you might need to set this up as like a three-finger click (1 = left, 2 = right, 3 = middle). Can't help you specifically because I don't run Linux on my MBP, but this is just an off-handed guess.

---

### Post by markbl on 2012-03-05
I installed BTT (Better Touch Tool) in OS X to give me middle click for pasting in Ubuntu. I run Ubuntu 11.10 in VirtualBox and it works very well.

---

### Post by terryeden on 2012-03-26
It looks like the only way to get this working is to remove Unity.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/933355](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/933355)

Unless anyone knows any differently?

---

### Post by papibe on 2012-03-26
Hi daehenoc.

If you are using the synaptics driver (highly likely). You may use this:
```
tap on the upper right corner of the touchpad
```
That is what has been working for me (not on Mac though).
Regards.

---

### Post by jonny on 2012-03-27
> **papibe said:**
> Hi daehenoc.

If you are using the synaptics driver (highly likely). You may use this:
```
tap on the upper right corner of the touchpad
```
That is what has been working for me (not on Mac though).
Regards.
That works for me on a MacBook Air 4,2.  The alternative is to tap and hold with two fingers, and then to use a third finger to click.

---

### Post by mcamilo on 2012-08-28
Make sure xkbset is installed.  Then run the following to bind the right hand command key to middle click:

xmodmap -e "keycode 134 = Pointer_Button2"; xkbset m

For more info go to [http://superuser.com/questions/73612/alternative-to-middle-click-for-linux-in-parallels-on-a-macbook](http://superuser.com/questions/73612/alternative-to-middle-click-for-linux-in-parallels-on-a-macbook)

---

