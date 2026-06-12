---
title: "Embarrassing: Twofer from retarded rookie"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by jimmj43 on 2007-12-13
I've been test driving a variety of Linux OSs for nearly a year and I always seem to guess wrong when it comes time to select screen resolution. At present I'm using 2 different machines, both with different monitors. I've got Gutsy on this (19" Gateway EV700) and I'm trying to install eLive on the other machine (15"Sampo AlphaScan 511).

1. Is there a tried-and-true rule-of-thumb 'rule' for determining screen resolution, or am I going to have to use a grease pencil and mark it on my monitors?

2. eLive (unstable 1.02)  is looking pretty good, but I'm having some issues, one of which has me just BAFFLED: How to shut down?!?!  I can't find a means of properly shutting it down to save my neck.

---

### Post by Kingsley on 2007-12-13
To shutdown eLive, you can try this command.
```
sudo shutdown -h now
```

---

### Post by JillSwift on 2007-12-13
If they did forget to put something on the desktop for easy shutdown, then you can always type this into a terminal:
[FONT=Times New Roman]*[SIZE=1](Asuming eLive is Debian based and has sudo)[/SIZE]*[/FONT]
```
sudo shutdown -h now
```This shuts the machine off. Using -r instead of -h makes it reboot after a clean shutdown.

**_ edit:_______________________________________**
Oops! Too slow =>.<=

---

### Post by jimmj43 on 2007-12-13
In another thread, a poster said something about having difficulty finding the shut-down icon **at the top right** corner. At the top right of the screen that displays for me there are only alternate desktop boxes. Could it be that I'Ive mis-selected screen resolution to the extent that the shut-down icon isn't visible and resides offscreen?

---

### Post by CouchMaster on 2007-12-13
Don't you just right click (maybe it's left click) the desktop and choose 'shutdown' - or 'logoff'?
I just replaced that version of Elive with the new Mepis the other day and it's just like all the other versions.

---

### Post by Dark_Stang on 2007-12-13
Uhm... can't you just ctrl+alt+f1 to a terminal and use the shutdown command from there? That should work on any linux distro.

Edit:And for your resolutions, if they're standard screens (not widescreen) they're probably 1024 x 800 on the 19", and 800x600 on the 15" (unless it's old, then it might be less). And yeah, I'd write it on them if you can't remember them.

---

### Post by jimmj43 on 2007-12-14
Thanks for the resolution info! :( I may resort to masking tape and a Sharpie instead of a grease pencil.


I find it incongruous that eLive would require that a user has to revert to a terminal to shut down. It just doesn't seem right. Here you've got this sleek XK-E Jag and you have to lift the hood and disconnect the battery to shut it off?!?!

I'm reasonably convinced that I'm missing something.

---

### Post by CouchMaster on 2007-12-17
Yep, I went to visit the grandkids this weekend (I had installed Elive Gem on both their computers) and you left click anywhere on the desktop and choose logoff!

---

