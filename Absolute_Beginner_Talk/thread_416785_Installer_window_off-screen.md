---
title: "Installer window off-screen"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ahh_Jebubs on 2007-04-21
Hey, there's probably a really simple solution to this but I can't seem to find any. 

I'm doing a clean install of Feisty from the live-dvd, and have gotten as far as running the installer. Problem is, the installer window runs off the bottom of the screen so I can't see any of the options I'm selecting at the bottom, it's all cut off. I've tried changing resolution but can only get either 640*480 and 800*600 (defaults to 800*600). Resizing the window wont work, moving/dragging it up only moves it until the title bar hits the top of the screen, leaving it still cut off. Maximising the window doesn't help either.

So yeah, daft question, but how the hell do I get it so I can actually see the install window properly? :( 

I'm using a 17" monitor btw.

Thanks.

---

### Post by IgnacioMiller on 2007-04-21
Hey ahh_Jebubs,

This is a rather unconventional fix, but did you try moving the image from the control panel on the bottom of your physical monitor? On mine you can bring up a menu that has an option for moving the image vertically and horizontally.

You could also try editing your xorg.conf file in with the right resolution and refresh rate, then restart X on the live cd with shift+backspace. If you have questions on how to edit your xorg.conf, hopefully someone can help (I am horrible at it for whatever reason)

Hope you get your question answered!

---

### Post by ahh_Jebubs on 2007-04-21
Hey Ignacio, cheers for the suggestion. 

I had tried messing with the monitor settings but if I moved the image up it would just leave a black bar at the bottom and not actually show anymore of the desktop. Same thing if I scaled vertically using the monitor settings.

I have just finished getting it installed through text mode though, so I'm happy :). I still don't have hardware acceleration for the graphics (stuck at 800*600 @ 60hz) but I'll play around with the xorg.conf and see what I can do.

Thanks for the help.

---

