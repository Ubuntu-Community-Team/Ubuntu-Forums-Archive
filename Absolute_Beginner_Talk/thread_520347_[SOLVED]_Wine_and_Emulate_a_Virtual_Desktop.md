---
title: "[SOLVED] Wine and Emulate a Virtual Desktop"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by El_Matthews on 2007-08-08
Gents

Maybe this is a stupid question but I still will ask it;
what's the difference in wine when you check the option "Emulate a virtual desktop"? What does it do differently?

I know that I have a window and that my games aren't crashing. As soon as I remove this my pc freezes when I try to play fifa 07. If I put the option I can't play full screen or am I wrong ?

Maybe this is even a better question, can I play in full screen with the option "Emulate a Virtual Desktop" ?


Greetings

Matthieu
Ubuntu 7.04 with wine 09.33

---

### Post by 3rdalbum on 2007-08-08
I can't answer your "even better question", but Wine's default behaviour is to spawn new windows with your ordinary window manager, just like Windows XP itself would do. The "Emulate a Virtual Desktop" is more like what an emulation or virtualisation program would do - WIne only opens one X window, and displays all the Windows windows within that space.

As you have noticed, the "Emulate a Virtual Desktop" does get some programs working. But the trade-off is that, to my knowledge, full-screen programs will still only appear within the X window and not full-screen on your monitor. But there may be a way to change that.

---

### Post by Hospadar on 2007-08-08
Well when you are emulating a desktop, any programs running within that desktop are going to think that that window is the entire screen, so you won't really be able to full-screen them like that.

you could get darn close to fullscreen by just making the virtual desktop the same size as your screen(minus the width of the panels and title bar)

Also have you poked around the wine appdb or google in general to see if there are some guides to making your game work right? often changing a config file or adding a command line option can make a world of difference.

Furthermore, if you are running beryl or compiz, try disabling them while running the game

---

### Post by El_Matthews on 2007-08-09
Hello, thank you both to take the time answer.  The game I want to play is Fifa 07. If I check the wine DB and other sites they just mention it works, nothing more.

For the moment I am playing it with minimized gnome-panels etc. but I would like to run it in fullscreen to integrate it later in my mythtv with mythgame.

Once this is working I will be a very happy penguin ;)

Greetings

Matthieu

---

### Post by El_Matthews on 2007-08-10
Anybody ?

---

### Post by El_Matthews on 2007-11-23
installed fifa 08 without any problems. thread closed

---

