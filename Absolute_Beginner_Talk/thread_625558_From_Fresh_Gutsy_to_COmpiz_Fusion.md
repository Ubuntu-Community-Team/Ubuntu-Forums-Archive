---
title: "From Fresh Gutsy to COmpiz Fusion"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by osmdian on 2007-11-28
Hey Guys,

sorry, i know there are a lot of posts about compiz dusion, but none go into the Detail that I need. I am a total noob:
My first question: I have installed ubuntu right now. Is Gnomes good for running Compiz Fusion or should i install kubuntu? I have a hpnx6325 laptop with tl52 1.6ghz amd64 processor, 1g ram and 100g harddrive.

2condly: I have just installed a fresh copy of ubuntu 7.10
No tutorial for installing compiz really starts at the beginning. I understood that i may have to install video card drivers, xgl, aixgl, xorl and than the compiz fusion desktop manager.

It would be great if someone could help me out. Also another small thing: My mousepad does not work as good as under windows, are there tools to change mouse properties other than the standard?

thanks


PROBLEM IS RESOLVED, THANKS!!! JUST HAD TO CHANGE COMPOSITE FROM 0 TO 1

---

### Post by Sef on 2007-11-28
Once you install Ubuntu, it will let you know if you can install Compiz-Fusion.

---

### Post by osmdian on 2007-11-28
sorry, but how will it let me know? remember that i know very little of linux. 

by the way: where are you supposed to put in the stuff like sudo.... in the terminal?

Cheers

---

### Post by osmdian on 2007-11-28
plz help!!

---

### Post by Sef on 2007-11-28
> sorry, but how will it let me know? remember that i know very little of linux. 

There was a notice that I could install Compiz-Fusion.   If you can't install it, it will not pop up.

> by the way: where are you supposed to put in the stuff like sudo.... in the terminal?

Applications > Accessories > Terminal

Check out this command which tells you your partitions:

```
sudo fdisk -l
```

sudo just goes at the begining.   It is not required for all commands; just the ones that need root access.  Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

> plz help!!

Have patience.  We are all volunteers here, so your question may or may not get answered fast.   Do not bump your thread unless a day has gone by.   Earlier bumping can result in a warning or infraction.

---

