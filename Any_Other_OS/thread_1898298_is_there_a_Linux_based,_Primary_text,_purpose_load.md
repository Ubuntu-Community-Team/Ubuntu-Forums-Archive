---
title: "is there a Linux based, Primary text, purpose loading OS"
date: 2011-12-21
forum: Any Other OS
---

### Post by Fenderian_Mayhew on 2011-12-21
when i say **"Purpose loading"** I mean if you want to run a high graphics game it loads only what that program needs to run (window manager, wine, etc.) than returns to a shell prompt when the program is exited. It loads only the pieces needed to run what is on each individual Terminal

I want to make a live game OS which can deticate** all** the resources of a system to running a single game. essentially turning that PC into a temporary game console.

---

### Post by tartalo on 2011-12-21
Not sure that I understood your objective correctly, but if you are looking for better performance I believe that making the game native and getting rid of Wine would be probably the first step.

---

### Post by jjex22 on 2011-12-21
Pretty much any distro can be configured to boot to the cli, from there you could write a script to start x and the program you want, though if you were running them underwine I'm not sure how you'd get wine to launch a specific program, but then I barely use wine so not the bestto ask.

Personally I'd just set up a custom system using gentoo and use a simple window manager like openbox - linux isn't really designed to be jumping in and out of X all the time - starting games from CLI was more of a DOS era thing. If you use gentoo, you can make sure you install only the things you need to play your games, this can of course e achieved via any distro that lets you do a minimal install to the cli - from there you'd build your system from source, not binary packages, choosing the variables you want at each package.... though this is much easier in gentoo as the system is designed to work in this way. 

hope it helps

---

### Post by mips on 2011-12-22
It's kinda pointless not running X11 and say Openbox as each time you start a game you will at least have to load X11 so you might as well just start up with X11 running as you are going to need it anyway. You can just use X11 without Openbox as well but Openbox is so small you will hardly notice it, at least it provides you with a desktop menu.

---

