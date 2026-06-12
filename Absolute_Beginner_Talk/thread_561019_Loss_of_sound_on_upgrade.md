---
title: "Loss of sound on upgrade"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by billio on 2007-09-27
I have just started using Ubuntu as a laptop operating system on a Lenovo C3000 N100 laptop.
I am impressed, it works nicely, but a little tedious to make the sound work. Good instructions from the Ubuntu forums make it a relatively simple problem to solve.

However, yesterday an upgrade came along that completely zapped my sound drivers without warning. This is a bug in Ubuntu - you can't do this to users, especially simple novice users like myself. There should at least be some warning that allows the user to decline this type of upgrade.

Anyway, does anyone know how to go back to working sound ?. Do I just have to repeat the process I used to make sound work in the first place ?.

Bill

---

### Post by maryjanua on 2007-09-27
i had the same problem and had to manually recompile alsa if thats any help

---

### Post by zatumate on 2007-09-27
a couple of updates have muted(turned off) my onboard sound
alsamixer turns it on again hope this helps:)

---

### Post by mali2297 on 2007-09-27
> **billio said:**
> I have just started using Ubuntu as a laptop operating system on a Lenovo C3000 N100 laptop.
I am impressed, it works nicely, but a little tedious to make the sound work. Good instructions from the Ubuntu forums make it a relatively simple problem to solve.

However, yesterday an upgrade came along that completely zapped my sound drivers without warning. This is a bug in Ubuntu - you can't do this to users, especially simple novice users like myself. There should at least be some warning that allows the user to decline this type of upgrade.


It is the kernel updates that can cause these problems. Their purpose is to fill security holes but I would say that they're not necessary for the common user. You can choose to ignore kernel updates (involving packages like *linux-image*) and save yourself potential problems.

> 
Anyway, does anyone know how to go back to working sound ?. Do I just have to repeat the process I used to make sound work in the first place ?.

You will probably not have to repeat every step, but it might be easiest.

Did you compile from source last time? Then you have to recompile, but you can use the same source.

---

