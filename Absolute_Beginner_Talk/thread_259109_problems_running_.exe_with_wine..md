---
title: "problems running .exe with wine."
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2006-09-16
Hi all,
I'm trying to run a game with wine and got the following:

libGL warning: 3D driver claims to not support visual 0x5b
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:ddraw:DirectDrawEnumerateExA no detached secondary devices supported.
fixme:ddraw:DirectDrawEnumerateExA no detached secondary devices supported.
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:ddraw:DirectDrawEnumerateExA no detached secondary devices supported.
fixme:ddraw:DirectDrawEnumerateExA no detached secondary devices supported.

What should I do to fix this?  any help please.

many thanks,
kpham.

---

### Post by Jukey on 2006-09-16
What game is it?

---

### Post by Frak on 2006-09-16
Wine may be missing some "stuff"
Try Wine toolkit

---

### Post by kpham.p on 2006-09-16
The game is Luxor, well...my wife and her mom plays this games all the times in windows, they keeps complain about the popups and slowness, so I install linux (ubuntu) on both of their computers :) lol..... I've never use wine before.  anyways, is that wine toolkit is a package that I can install?

---

### Post by kpham.p on 2006-09-17
any idea what would the error from the first post mean guys?

thanks
kpham

---

### Post by mostwanted on 2006-09-17
It means it doesn't work. WINE hasn't implemented whatever library feature that game uses.

---

### Post by kpham.p on 2006-09-17
aww thanks,  no luck for me than :(......

kpham.p

---

### Post by senn on 2006-09-17
hi kpham.p, i had a look at that game it is in a file format named .Ink. this is used by windows for hand writting recognition software for pocket pc's. as far as i can tell (but please dont hang me out to dry)[-o< it needs an app called activesync to play, microsoft word can also open them up. maybe the good folk at wine HQ are working on this i realy dont know. anyhow hope this helped (but sorry about your game):(

---

### Post by kpham.p on 2006-09-17
I will try to do more research to see if there is any other ways..... if can't play this game in linux, I would have to install xp on both of my wife and her mom machine again.... and I hate to do so. :).

thanks,
kpham

---

### Post by Frak on 2006-09-18
> **kpham.p said:**
> I will try to do more research to see if there is any other ways..... if can't play this game in linux, I would have to install xp on both of my wife and her mom machine again.... and I hate to do so. :).

thanks,
kpham
Try a virtual machine
And unable to create direct draw means that the drivers havent been developed yet for the proccesor for the game (direct draw is info about the processor)

---

### Post by kpham.p on 2006-09-23
Thank you so much guys.

---

### Post by kpham.p on 2006-09-24
Ok, finally the programe is running but, when i start to play the games, the following error shows up:

fixme:msvcrt:MSVCRT__sopen : pmode 0x0190 ignored
fixme:msvcrt:MSVCRT__sopen : pmode 0x270b900 ignored
fixme:msvcrt:MSVCRT__sopen : pmode 0x270b960 ignored
Read failed on temporary file

Not sure what temporary file its trys to read from....

could some one shows me wich places that this temporary file could be and what permission should I set to it so the program could read to run?

thanks.
Khanh

---

