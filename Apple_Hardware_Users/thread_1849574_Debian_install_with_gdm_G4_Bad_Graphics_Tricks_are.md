---
title: "Debian install with gdm G4 Bad Graphics Tricks aren't working!"
date: 2011-09-24
forum: Apple Hardware Users
---

### Post by ronnielsen1 on 2011-09-24
I did a dual boot install On a G4 with Tiger on one boot and Debian net install of xfce4. It was actually the only cd I could get it to boot from. It installed beautifully and gives me a choice on boot of macosx, linux or cd. The graphics are messed up and I need to go to vesa drivers. I have no way to get to terminal. Control-alt-backspace or any other key combos don't work! Short of reinstalling debian without gdm, does anyone know a simple fix to this?

[CENTER]](*,)
[/CENTER]

---

### Post by rsavage on 2011-09-25
Yeah, you just boot into single user mode.  In ubuntu at the second yaboot prompt one would type this:
 
Linux single
 
In debian I think you can also do it by typing
 
Linux 1
 
This post explains how to setup graphics [http://ubuntuforums.org/showthread.php?t=1798792](http://ubuntuforums.org/showthread.php?t=1798792)

---

### Post by ronnielsen1 on 2011-09-27
Thank you very much. I got sidetracked for a minute. I had a live cd of gnustep actually work on it

---

