---
title: "newer kernel freezes mid-boot; Recovery Mode frozen too"
date: 2018-09-27
forum: Apple Hardware Users
---

### Post by bennywas on 2018-09-27
[COLOR=#696969][SIZE=1]MacBook Pro, Mid 2012 | Ubuntu 18.04 partition, installed from USB | Main/original partition is macOS Sierra[/SIZE][/COLOR]

Hi ):P After my first several days with Ubuntu booting normally, I now get indefinitely stuck on the purple logo screen with no white dots loaded ([pic1]("https://i.imgur.com/ny7S1F2.jpg")). This used to load fairly quickly, maybe one orange dot per second.* [COLOR=#808080]*The freeze happens with both the plain old [/COLOR]*[COLOR=#808080][FONT=courier new]Ubuntu[/FONT]* selection from GRUB, as well as with the *[FONT=courier new]Advanced options for Ubuntu -> Ubuntu, with Linux 4.15.0-34-generic[/FONT]*[FONT=arial] selection[/FONT], which I'm pretty sure is the same thing.*[/COLOR]

Advice for similar complaints says to go into [FONT=courier new]recovery mode[FONT=arial] and do stuff[/FONT][/FONT], but my Recovery Mode is frozen too. The Recovery Mode GUI gets displayed ([pic2]("https://i.imgur.com/GXx1pQo.jpg")), but my arrows don't work to navigate it. Neither does Enter. :-| It was navigable for the first couple reboots after this whole problem commenced, and then less and less often, and now it's almost never navigable.
[COLOR=#808080]*Sometimes*--like one time out of every several dozen reboots--Recovery Mode is magically navigable. When this happens, it sometimes freezes after just a few arrow-keystrokes. So for all intents and purposes, I think we should just assume that going into 4.15.0-34's Recovery Mode isn't feasible.*
***Also: on one of these magical occasions when Recovery Mode *was[/COLOR]*[COLOR=#808080] navigable, I got so excited that I left the menu open for a long time while I googled what to do on my phone. After a while, a [FONT=courier new][ TIME ][/FONT] error appeared pasted on top of the screen ([/COLOR][[COLOR=#ff8c00]pic3[/COLOR]]("https://i.imgur.com/ylKqlsa.jpg")[COLOR=#808080])--and then a bunch of other laggy terminal-ish descriptor phrases pasted themselves diagonally all across the screen ([/COLOR][[COLOR=#ff8c00]pic4[/COLOR]]("https://i.imgur.com/rkap4cu.jpg")[COLOR=#808080]). :-? Then when I tried arrowing again, the phrases cleared away. ...No idea what this is about.[/COLOR]*

[FONT=arial black][FONT=arial]However, [/FONT][/FONT]the "older" Linux kernel--listed as [FONT=courier new]4.15.0-29-generic[/FONT]--boots just fine when I select it from [FONT=courier new]Advanced options for Ubuntu[/FONT]. So does the older kernel's Recovery Mode, though I don't know why I'd need it.
Mind you, I know next to nothing about...any of this...so I have no idea how I could've screwed up one kernel version and not the other.[COLOR=#808080]**(Also, I don't rightly understand how you can load two different kernels on your computer yet still see the same files on both...?? guess I don't fully know what a kernel is) *[/COLOR]I thought I could just use this older kernel instead because everything seemed at first to be identical. But the wifi on it was screwed up (Broadcom problems), just like when I first installed Ubuntu *[COLOR=#696969](I eventually fixed it following [/COLOR][[COLOR=#ff8c00]this advice[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2391053&page=2")[COLOR=#696969])[/COLOR]*...so from that being non-identical, I extrapolate that other things are non-identical too.

The last thing I remember doing back when I could boot normally was trying to figure out why VLC's audio only worked occasionally, and researching why YouTube videos were loading so slowly (and learning along the way that my MBP has a "dual graphics card" and that's apparently problematic), and potentially downloading packages or doing other root commands to try to fix those problems, though I can't remember what if any.

Did I explain this clearly?? Did I leave anything out? Can anyone help me diagnose what in the HECK might be going wrong??? [-o< Thxxxx

[SIZE=1][COLOR=#696969]I'm new to Linux, fairly new to the command line, and have little understanding of computer guts. Please phrase your helpful replies closer on the spectrum to ExplainLikeImFive than ExplainLikeIm120.[/COLOR][/SIZE]

---

### Post by deadflowr on 2018-09-27
*Thread moved to** Apple Hardware Users***

---

### Post by bennywas on 2018-09-30
UPDATE: I did a fresh install, which obviously fixed the problem *for now*, though I'll let you know if it comes up again.

---

