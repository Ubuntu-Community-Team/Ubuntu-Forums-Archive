---
title: "Open Source Radeon drivers on Saphire X800GTO"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by cinnix on 2007-01-26
Hey, I just wanted to know if it was possible to use the opensource radeon drivers working on my card. My ultimate goal is to get Beryl up and running on my rig, but to my understanding Beryl does not function on fglrx drivers.

Now I've only had Ubuntu on my rig for just over a week now. When I first attempted to install I had trouble booting the Live CD, X gave me some sort of error. I solved this problem by editing my xorg.conf to run "vesa" drivers, then installed fglrx once the Ubuntu was fully installed.

When I try to set my driver to either "ati" or "radeon", Ubuntu boots up until the end of the splash screen, then the screen flickers and I get a green and a blue dotted lines across my display, whilst the Ubuntu logo is still there. Obviously X is having trouble rendering my login screen, or perhaps Gnome or something.

So please, is there a way to get the opensource drivers working on Edgy? I am really out of solutions.

Thank You in Adance.

---

### Post by r4ik on 2007-01-26
Try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by cinnix on 2007-01-26
> will download right version of the [COLOR="Red"]proprietary[/COLOR] driver for your ATI or Nvidia card from ATI or Nvidia's websites

Isn't that the fglrx driver? I already have beryl on my startup session, and to my understanding Beryl will not work as a Window Manager without direct rendering, which ironically is not supported with the proprietary driver?

I could be wrong, could someone please clarify.

[EDIT]

I've ran envy, Beryl now hangs. Tyring to identify problem. - Solved

[Edit 2]

Same boat as before, do I need Open Source drivers? Or is it possible to run with fglrx? Beryl automatically changes my window manager back to gnome instantly.

---

### Post by r4ik on 2007-01-26
Dont know i have got an Nvidia but my guess is yes.

---

### Post by sloggerkhan on 2007-01-26
I have an x700 mobility, which should be same generation as your card. Don't know if stuff is the same or not for yours.

On my card, I can use the open source ati/radeon drivers to run beryl with AIGLX  

OR

I can use the fglrx driver to run beryl with XGL.

I think it is easier to run with AIGLX, all you have to do is makes sure your card works decent with glxgears, add a repo, and hit OK. (Or at least that's all I remember doing.)

I'd run a search on ATI AIGLX BERYL

---

### Post by sloggerkhan on 2007-01-26
[http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7)
[https://help.ubuntu.com/community/RadeonDriver#head-a0bf0ca17168200ea3dd810ae505419bdc7f2e6d](https://help.ubuntu.com/community/RadeonDriver#head-a0bf0ca17168200ea3dd810ae505419bdc7f2e6d)

---

### Post by cinnix on 2007-01-26
OOOOOO, i just got it working correctly with fglrx and XGL, which should be fine for now. Envy seemed to have done the trick, fglrxinfo did not return anything involing mesa, which opened doors to an alternate route to get Beryl working. 

Im loving Linux, you start to wonder why you used Windows for so long once you start to understand how Linux works. 
Thanks

---

### Post by r4ik on 2007-01-26
Glad it works !

---

### Post by CowzRule on 2007-01-26
You can't do this now, but if you ever have to reinstall and want to try AiGLX and Beryl, take a look at the info I provided in the following thread:
[http://www.ubuntuforums.org/showpost.php?p=2058699&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=2058699&postcount=2")

---

