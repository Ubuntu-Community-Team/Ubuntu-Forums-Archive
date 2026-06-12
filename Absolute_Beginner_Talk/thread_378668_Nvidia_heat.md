---
title: "Nvidia heat"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by xadloki on 2007-03-07
Hello, I've got the newest drivers from nvidia and I'm running ubuntu edgy 386, I've noticed in the nvidia control panel that the heat of the card is way too high to what it usually i in windows, currently showing 55 celsius, and in windows I usually see it around 38-45 celsius, now I don't know if in linux it gives a more true measure than in windows or not but the I do hear that the fan is constantly running at high speed.
There's no wierd glitches or anything and everything works fine, I'm just concerned that linux might be using it more than it needs to be used. In linux I don't run any special software that might need 3D acceleration, just basic web browsing/email/IM and so on.

---

### Post by rajeev1204 on 2007-03-07
Hi

i have nvidia 7600gt and it shows around 50 degrees in both windows and linux.

i guess ur temp is normal range. (safe)

which card model u have?

---

### Post by xadloki on 2007-03-07
I have the 6600 LE 
55 is safe but still I was expecting it to be lower since linux is supposed to use less resources.
It's not a big deal I was just wondering why does my pc make more noise running ubuntu than windows :)... or maybe I'm just imagining since I haven't used windows for a few weeks now.

---

### Post by Bachstelze on 2007-03-07
You guys can use the *nvclock* utility to underclock your card if you don't use 3D stuff, I guess it will hel lower the heat.

BTW, I've noticed that nvclock reports a much lower temperature than nvidia-settings :

```
mfb@ana:~$ nvidia-settings -q gpucoretemp

  Attribute 'GPUCoreTemp' (ana:0.0): 63.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

mfb@ana:~$ nvclock -T
nVidia Geforce Go 7600
=> GPU temperature: 52C

```

---

### Post by xadloki on 2007-03-07
thanks for the info, oddly enough when I typed nvclock --info the temperature showed 66 C while nvidia control panel shows 52 C 0.o

---

