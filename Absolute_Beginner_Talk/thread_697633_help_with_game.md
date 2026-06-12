---
title: "help with game"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-02-15
i want to play the old doom95 on ubuntu, but when i go to launch the doom95.exe file with wine, it tells me that it's unable to locate the wad file for doom, and that i should put it in the same directory where doom95 resides. well, i know the wad file is there. is there something i'm missing?

---

### Post by pytheas22 on 2008-02-15
I don't know if this will work, but you could try playing it in dosbox instead of wine, if it was a DOS program.  I think there is a dosbox .deb in one of the standard repositories, or if not search for it on the Internet.  I've had good luck in the past with dosbox for old games that wouldn't run in wine.

---

### Post by Sinkingships7 on 2008-02-16
i just recently tried that, but (in dosbox) it told me that the file i was trying to run was a windows nt executable.

---

### Post by pytheas22 on 2008-02-16
Yeah, I guess dosbox wouldn't be able to run an NT executable.

I don't know anything about it, but apparently there are native Linux ports of doom?  Did you try that?  Take a look at these threads [http://www.linuxquestions.org/questions/linux-games-33/doom-95-on-ubuntu-i-dont-want-prboom-579775/](http://www.linuxquestions.org/questions/linux-games-33/doom-95-on-ubuntu-i-dont-want-prboom-579775/) and [http://www.linuxquestions.org/questions/linux-software-2/how-to-run-doom-on-ubuntu-using-wine-579835/](http://www.linuxquestions.org/questions/linux-software-2/how-to-run-doom-on-ubuntu-using-wine-579835/)

Otherwise, you could always try a virtual machine.  It might be tricky depending on how much hardware acceleration the game requires, but vmware has beta support for direct 3d now, and Virtual Box can do direct draw, at least.  I got VB to run Age of Kings and Cossacks easily, so I'm thinking that an even older game would probably work fine as well.

---

### Post by knattlhuber on 2008-02-16
> **Sinkingships7 said:**
> i want to play the old doom95 on ubuntu, but when i go to launch the doom95.exe file with wine, it tells me that it's unable to locate the wad file for doom, and that i should put it in the same directory where doom95 resides. well, i know the wad file is there. is there something i'm missing?

I had the same problem. For some reason, the doom95.exe file doesn't work.
I tried the GZDoom port instead, which worked fine. You can download it here:
[http://grafzahl.drdteam.org/index.php?page=topic&id=230]("http://grafzahl.drdteam.org/index.php?page=topic&id=230")

Remember to switch of the Advanced Desktop Effects before running Doom.

---

### Post by Sinkingships7 on 2008-02-17
> **knattlhuber said:**
> I had the same problem. For some reason, the doom95.exe file doesn't work.
I tried the GZDoom port instead, which worked fine. You can download it here:
[http://grafzahl.drdteam.org/index.php?page=topic&id=230]("http://grafzahl.drdteam.org/index.php?page=topic&id=230")

Remember to switch of the Advanced Desktop Effects before running Doom.

oh my god man, thank you so much. i've been trying to get that to work since 2007. :)

now if only you or someone else knew how to get doom 3 working, or at least could tell me how to start installing off of an iso...

---

### Post by RomeReactor on 2008-02-17
Hi. Try the [instructions here]("http://zerowing.idsoftware.com/linux/doom") (ISO related instructions [here]("http://ubuntuforums.org/showthread.php?t=695295")). If you have issues with audio or graphics in Doom 3, try searching and/or posting in the [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93") section.

---

### Post by AnRa on 2008-02-17
I think that the problem is that you are executing wine from a directory other than the Doom's one. You may try this in a terminal:
```

cd /path/to/doom
wine doom95.exe

```

---

### Post by orangey on 2008-02-23
THANK YOU!  Wine+gzdoom works wonderfully.  No need to deal with compiling skulltag or lxdoom or prboom or freedoom.  Lol.

---

