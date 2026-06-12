---
title: "Ive been trying to get my sound working for weeks please help?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by roostercogburn on 2005-12-04
I think I have tried everything and i dont know what else to do?:confused: :confused: :confused: :confused:

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=roostercogburn]I think I have tried everything and i dont know what else to do?:confused: :confused: :confused: :confused:[/QUOTE]
What type of card do you have?

Normally, this is what I check:

1) Does /dev/dsp exist? 
```
$ ls -l /dev/dsp
```
2) Is the hardware detected (for PCI cards)
```
$ lspci
```
3) Are the sound drivers loaded? 
```
$ lsmod | grep snd
```

If you can narrow down what is wrong, there will be a better chance someone can help you.

---

### Post by adduds on 2005-12-04
This fix helped me I had sound and it showed up, and videos played and cds but just no sound came out so this is what i did:

First download the latest alsa-drivers:

[here]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.10.tar.bz2")

Then try this:

[http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH4]("http://ubuntuforums.org/showthread.php?t=87849&highlight=ICH4")

---

