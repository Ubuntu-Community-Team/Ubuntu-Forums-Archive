---
title: "ESS audiodrive ES1868F"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Penguinw on 2006-08-27
I have got ubuntu today, i have manneged to seteverything elce up but...
i have a ESS audiodrive ES1868F but i can not get it to reconise it, i think it has not got the right driver or summithing.
please help

---

### Post by Penguinw on 2006-08-28
anybody?

---

### Post by u04f061 on 2006-08-28
i also have problem with my sound card and i am using ES1978
i could not find its driver anywhere even for windows and now my pc is soundless. but i think you will not feel any problem because i found the name of your drive in following link of drivers . may it be helpful to you.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix")

---

### Post by Penguinw on 2006-08-29
in the end i have just endedup getting a new sound card :p

---

### Post by az on 2006-08-29
> **Penguinw said:**
> I have got ubuntu today, i have manneged to seteverything elce up but...
i have a ESS audiodrive ES1868F but i can not get it to reconise it, i think it has not got the right driver or summithing.
please help


That card is on the ISA bus and the kernel can not safely scan it.

 You need to load the module by hand, just like in windows, you would often need to tell it that the hardware is there.

[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)



sudo modprobe snd-es18xx

---

