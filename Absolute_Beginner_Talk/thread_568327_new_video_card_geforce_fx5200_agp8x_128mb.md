---
title: "new video card geforce fx5200 agp8x 128mb"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-10-05
hey folks 
after my problems with my ati card (radoen x1550 512mb- no 3d) a friend has kindly donated an nvidia geforce fx5200. will this card work better? has anyone had any problems with this card?
and lastly i have also accquired 2x 512mb ddr400 to replace my 2x 256 ddr400, will this just autodetect like windos or do i have to do anything?:):)
thanks in advance
mj :guitar:

---

### Post by skymera on 2007-10-05
i have nVidia and works wonders :)

i used Envy script to do all the work, voila!

---

### Post by maryjanua on 2007-10-05
excellent!!

but what about when i plug the nvidia card in and ubuntu loads the ati driver to use it 
will it work?

---

### Post by Jeroen Vernooij on 2007-10-05
In 7.04: no
in 7.10: yes, thanks to bulletproof-x

You should boot into recovery mode, and run
```
sudo dpkg-reconfigure xserver-xorg
```
if you are running 7.04.

---

### Post by louieb on 2007-10-05
Maybe then again maybe not won't know till you try. 

if doesn't then boot to recovery mode and run
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Paul820 on 2007-10-05
I have that card on my desktop, it works perfectly in feisty and gutsy. Not like this crappy ATI card in my laptop.

---

### Post by maryjanua on 2007-10-05
thanx guys i'm running 7.04 and 7.10 on different hdds

whats puppy and how r u using it?:):):)

---

