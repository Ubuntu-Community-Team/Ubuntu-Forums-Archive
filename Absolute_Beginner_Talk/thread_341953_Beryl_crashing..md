---
title: "Beryl crashing."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Duppy on 2007-01-19
I uprgaded to Edgy and managed to install beryl, which i was quite pleased about.

When i set beryl as the manager it works for a few seconds then the whole PC freezes.

Anyone know how to sort this out?

I have Nvidia
512mb Ram
3 Ghz Pentium 4
Ubuntu 6.10 Edgy Eft

Remember I am new to linux, so if you could use a bit simpler instructions.

Thanks very much.

---

### Post by mand0 on 2007-01-19
This used to happen to me when I wasn't using the newest Nvidia drivers.  What drivers are you using?

Load beryl through the terminal by typing:

```
beryl-manager
```

Post what the terminal spits back.

---

### Post by Duppy on 2007-01-19
When i load it through the terminal, thats when it crashes, the mouse still moves across the screen though.

[img]http://img347.imageshack.us/img347/633/dsc011522lh7pt7.jpg[/img]

Then it crashes so I have to hard reset the PC.
I cannot open beryl basically or it crashes.

---

### Post by PPAAUULL on 2007-01-19
I have the same problem with an ATI card execpt that mine freezes then it goes back to the login screen.

---

### Post by mand0 on 2007-01-19
type into the terminal:

```
nvidia-settings
```

Look around for what version your drivers are.  Also, try updating your system completely.

---

### Post by Duppy on 2007-01-19
A little configuration panel came up.

Then this was in terminal:
> ERROR: NV-CONTROL extension version 1.10 is too old; the minimimum required
       version is 1.11.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.


Edit: Readin the top line, I think you were right about old drivers.

---

### Post by Peti29 on 2007-01-19
Most likely you have a different problem but you should be aware of: [http://www.ubuntuforums.org/showthread.php?t=341036&page=3](http://www.ubuntuforums.org/showthread.php?t=341036&page=3)

It worth checking your version no. before trying to fix the problem.

---

### Post by mand0 on 2007-01-19
You should delete your nvidia drivers and reinstall them using new repositories.

---

### Post by Duppy on 2007-01-19
Little help please baby? :p

---

### Post by mand0 on 2007-01-19
> **Duppy said:**
> Little help please baby? :p

lol

Try following the directions here carefully:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Edgy_with_nVidia)

---

### Post by Duppy on 2007-01-19
Thanks to everybody who helped!(mainly mand0) I sort of half followed the directions, installed something and then press CTRL ALT + BACKSPACE to restart.

got a serious looking error message saying, X desktop could not be started (or something along those lines) so i reset pc

When I restarted, the NVIDA splash screen was different to the usual one, it was a darker more modern looking one (must have updated)

beryl works now, im on it now and it is stable. (touch wood)

Now all i need is a beryl guide book, telling me all the tricks like how to do the cube thing, then I will be happy. Thanks a lot.

Edit: just found out purely by look that right + left mouse button hold down does the cube. what otehr tricks can i do? like transparent windows and so on.

---

### Post by mand0 on 2007-01-19
Best way to learn what beryl can do is to go into the beryl settings manager and just play around with it! Congrats on getting it to work!

If you type in the terminal:

```
nvidia-settings
```

What do you see now?

---

### Post by Duppy on 2007-01-19
A Lot more advanced configuration box with lots of options and loads of information about my PC. :D
\\:D/ 
Thank you buddy, I know it was 50% my luck and just messing around in terminal, but you truly have helped me. I would kiss you if I could.

.. Only on the cheek mind..

---

### Post by mand0 on 2007-01-19
You're most welcome :p 

Look here for the beryl default keys:

[http://wiki.beryl-project.org/wiki/Tips/Default_Commands](http://wiki.beryl-project.org/wiki/Tips/Default_Commands)

If some of those keys don't work you may need to enable something in the settings.

---

