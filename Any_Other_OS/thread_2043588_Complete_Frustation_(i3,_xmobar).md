---
title: "Complete Frustation (i3, xmobar)"
date: 2012-08-16
forum: Any Other OS
---

### Post by 0xicl33n on 2012-08-16
Hello~! this is my first post, but definetly not my first experience with linux. Ive been using ubuntu on and off for a long time now. Never have gotten into it as much as now because i have had NO IDEA HOW TO.

Im using Kubuntu 10.4 (Backtrack 5). Normally i would post on the backtrack forum, but it WONT log me in ! (ie, type in username and pass, "hello blah , thank you for logging in, then it takes me back to the same page, and im not logged in at all, tried on two computers, maybe bt forums are broke?). So i decided to post here because ubuntu is ubuntu. So my problem is:

Im using i3 as my window manager. i have i3status and all the proper perl dependencies. ( i added the debian repo to apt, and a few more) 

I have my xmobar sit on top of the screen, okay, thats fine. BUT

Any terminal i create goes fullscreen, again, thats normal for i3.

The problem is, the top menu bar on i3 covers xmobar. I cannot get it to NOT cover xomar

dzen2 is broken, and a known debian bug.  (in 10.4)

Im usingxmobar .11  
and i3 version 3.e

I spent about an hour on google trying to figure out what to do. I found out it has something to do with xmobar NOT setting its window class for xprop to handle. The only way to fix that is to update.. i can try using the sid package but thats extremely experimental and i dont even know if it would hlep

xmobar crashes every time i load it with its config file ~/.xmobarrc without it, it loads perfectly fine. So i cant change the settings in xmobar EITHER!

Also i could possibly rebuild i3 from source and tell it that 50pixels down is where it should start with terminals

There is 0 documentation on stuff like this, it really annoys me.

Is there anyone using i3? Or xmobar? And have had similiar problems?

Anything would help would be REALLY appreciated,  might even post this on the BT forum as well

---

### Post by 0xicl33n on 2012-08-20
bump v_v

---

### Post by oldos2er on 2012-08-20
Moved to Other OS/Distro Talk.

---

### Post by 0xicl33n on 2012-08-21
Solved

New laptop, new OS. Originally had BT5 R1 and updated to BT5 R3 via apt

(cant post pix yet)
[http://i72.photobucket.com/albums/i188/xxSlainxx/2012-08-20-231935_1368x768_scrot.png](http://i72.photobucket.com/albums/i188/xxSlainxx/2012-08-20-231935_1368x768_scrot.png)

fresh install with BT5 R3 64 bit

back to using dzen2
this is in my ~/.i3/config
```
exec i3status | dzen2 -fg white -bg black -y 750 -x 500
```decided to place it at the bottom, works instead of at the top, much easier on my part

---

