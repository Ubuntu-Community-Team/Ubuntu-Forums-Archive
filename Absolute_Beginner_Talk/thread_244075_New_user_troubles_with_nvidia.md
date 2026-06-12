---
title: "New user troubles with nvidia"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Jarnz on 2006-08-25
Hello all

I'm new to Ubuntu and Linux, so please be gentle.

I'm trying to install nvidia drivers downloaded from their site, but the installer keeps complaining that X is still running.

I've tried 3 things so far that I have picked up from other forums:
<Ctrl><Alt><Backspace>
init 3
/etc/init.d/gdm stop

Nothing seams to work. I'm using Ubuntu 6.06 (Dapper I believe), all standard install with a couple installs for building and compiling.

Thank you.

---

### Post by Bachstelze on 2006-08-25
Hi and welcome to Ubuntu :)

For pretty much everything, there's an "Ubuntu" way to do stuff, which is significantly easier than the "normal" way. For nVidia drivers, see [here](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia).

---

### Post by Jarnz on 2006-08-25
Thank you. I followed that link. Drivers already installed. The computer Ubuntu is on is my media/gaming PC. needs to have a high res in widescreen with 3D acceleration which the default drivers cant do, that I'm aware of.

---

### Post by Dar on 2006-08-25
I'd recommend [http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)
Bookmark that page! I have a fast PC but it would lag doing something as simple as dragging a large selection box over a blank desktop. It seems a virgin Ubuntu install isn't very strong graphically.

 I updated my nvidia card drivers as per that threads instructions, as well as updating my kernel to the athlon-specific one, and now my computer renders a selection box smoothly.

Edit: I would not know how to optimise for wide-screen yet, sorry, and my link would not help you with that I'd bet. But it did help my computer run Ubuntu faster, which is desirable by pretty much anyone's standards.

---

### Post by Jarnz on 2006-08-25
Thank you SOOOO much. got the nvidia logo of bliss so its installed. its still giving me a max res of 1024x768, if I want to go higher, do I have to put it into the x.conf file or will that stuff things up?

---

### Post by infoseeker on 2006-08-26
I think the resolution depends on your monitor. I use a LG Studioworks 710 and I can get 1280x1024, from the default setup, no tweaking.

---

