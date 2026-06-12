---
title: "apple Keyboard"
date: 2006-12-17
forum: Apple PPC Users
---

### Post by aunzim on 2006-12-17
I have a Pc with kubuntu instaled and a new apple keyboard with a european portuguese layout. 

- Kubuntu configures this keyboard as a pc-104. After a lit bt of googling I manage to change it in xorg to "macintosh" but all the acentuation keys are misplaced 

- then i tried to make kcontrol to remap it. So I choose the macintosh keyboard and the basic variant, but no "alfa" keys work except for the ~\´ª_ and the numeric keys that work fine.

- so tried the nodeadkeys variant. It goes find (in kde, not in fluxbox), but guest what, now I have "no dead keys" :)

- The only way I can do the @ simbol is by 

Xmodmap -e keycode 113 = Mode_switch 

I tried to change the pt file in /usr/X11R6/lib/X11/xkb/symbols/ and /usr/X11R6/lib/X11/xkb/symbols/macintosh_vndr

with no good results... any idea??

thanks !!

---

