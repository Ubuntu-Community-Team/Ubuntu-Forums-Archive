---
title: "Transparency in Kubuntu &quot;plz just help me&quot; :-)"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by kubuntu on 2005-05-16
Hi ive been reading forever on how to enable transparency in kubuntu but i just cant figure it out. I keep on ending up in this situation where i read that theres different ways to do it like with "Xorg" and other things. Im running 5.04 so that has kde 3.4.......and uh yea idk what exactly im doing lol. I know how to use konsol and stuff well so if i just had some nice istructinos that would be extremely great. I would greatly appreciate it if sombody would help me. Thankyou

---

### Post by philipacamaniac on 2005-05-16
"Xorg" is the only way to do it, there are just different ways to go about it. "Xorg" is your graphics server, and it is responsible for display things on the screen.

Anywho, what kind of video card do you have? (ATI, Nvidia, or other)

If ATI, sorry, you're out of luck (I'm with you -- stupid ATI). 

If Nvidia, follow the instructions on this post: [http://www.ubuntuforums.org/showthread.php?t=20769](http://www.ubuntuforums.org/showthread.php?t=20769). Then in KDE, go to the Control Center. In the Control Center, go to Desktop --> Window Settings --> Translucency. Turn it on and you should have some fun.

Remember to log out and log back in whenever you make a change to you Xorg configuration. (CTRL -- ALT -- BACKSPACE is the quick shortcut)

---

### Post by Ironi on 2005-05-16
[QUOTE=philipacamaniac]
Anywho, what kind of video card do you have? (ATI, Nvidia, or other)

If ATI, sorry, you're out of luck (I'm with you -- stupid ATI). 
[/QUOTE]
What about the open source [DRI drivers](http://dri.sourceforge.net/)?

> 
If Nvidia, follow the instructions on this post:

Be aware that enabling composite with GLX (3D accel) can be problematic. In other words, you may experience crashes and other undesirable effects.

---

### Post by philipacamaniac on 2005-05-16
[QUOTE=Ironi]What about the open source [DRI drivers](http://dri.sourceforge.net/)?[/QUOTE]

But I want 3D rendering! We can't have both, can we? If we can, dude, let me know!

---

### Post by Ironi on 2005-05-16
IIRC, the DRI drivers support Radeons up to the 9200 for 3D accel (ATi hasn't given the project specs for newer cards). Some people have taken it upon themselves to write an accelerated [R300 driver](http://r300.sourceforge.net/), but it probably doesn't work too well.

Anyways, I don't recommend trying the DRI drivers unless you know what you're doing. Based on my experiences from last year (with a Radeon 8500), the 3D performance isn't terribly great nor stable either.

---

### Post by philipacamaniac on 2005-05-17
Well, I have a 9700 Pro, so that's no good.

kubuntu, how is that transparency coming along?

---

