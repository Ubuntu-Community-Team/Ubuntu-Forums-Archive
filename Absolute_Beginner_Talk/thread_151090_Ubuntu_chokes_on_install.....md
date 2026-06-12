---
title: "Ubuntu chokes on install...."
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by charriso on 2006-03-27
Hello,

Totally new to Linux, I chose Ubuntu for my first approach. I have a Mac G4 with two hard drives of which one is empty and 150G, and should be a perfect landing pad! It is mostly "unformatted", which I am told is what has to happen for a Linux install... (note, all assertions can be taken as questions...)

I have tried the LiveCD and it works fine. The install CD however won't play ball, and every time I try to launch it, it crashes differently (?!).

I have managed to get as far as selecting the country in which I reside in the initial setup process, but then the interface freezes. I have to force a restart.

I've tried about five or six times now, and now the process is ending in a Kernel panic, the details of which I do not recall, but the last few lines are of the style "Oops, tried to access a bad sector"; "Not syncing", etc. Autoreboots after 180sec, but then we fall back into the same problem. 

Rebooting into Mac OS X is not a problem, and everything seems to work fine.

I have tried launching with different options (expert, video= ofonly) etc. Same problem every time (more or less: as I say, the crashes are not always identical).

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

Both of my hard drives are installed in the tower, and I recently noticed that my OS (Mac OS X) is on device1, while device0 is the one I would be installing Linux on, if it would work for me. I have no idea if this is a problem (does the installer assume that there's an OS on device 0? I dunno. I'm shooting in the dark.)

Any advice gratefully received, and sorry if there's already a thread answering this (I didn't see it...)

Cheers,

Colin.

---

### Post by charriso on 2006-03-27
Sorry, forgot to add: trying to install Ubunutu Breezy (5.10)

Colin.

---

### Post by KingBahamut on 2006-03-27
Is that a burned image CD or one provided by Canonical?

---

### Post by meborc on 2006-03-27
it seems like a cd problem... try to burn the image with a low speed... 

if it is a hardware problem (which it is not) you might get help from [mac/ppc subforum]("http://www.ubuntuforums.org/forumdisplay.php?f=95")

but i am quite sure it is a cd problem... so... try again with a new cd and report here ;)

---

### Post by charriso on 2006-03-27
No, it's a Canonical disk...

bad disk perhaps?

Colin

---

### Post by charriso on 2006-03-27
Whoa whoa, no the problem is my CD reader...
LiveCD works in my laptop (also a G4), but not in my desktop... Hmmm. Same kind of kernel panic nastiness....

That's a drag...

I'll try something different and get back to you. Thanks for the replies.

Colin.

---

### Post by meborc on 2006-03-27
have you ever thought of cleaning your cd-rom? :mrgreen: you wouldn't believe what i found in there once... the best way is to use special CD's with little brushes... pretty cheap... get yours from your local pc-store;)

---

### Post by taurus on 2006-03-27
Maybe you want to download the iso file and burn it to a CD with a slow speed like 4x.  It's real important to burn it at slow speed so Ubuntu won't choke on itself when you try to install it...

---

### Post by charriso on 2006-03-27
[QUOTE=meborc]it seems like a cd problem... try to burn the image with a low speed... 

if it is a hardware problem (which it is not) you might get help from [mac/ppc subforum]("http://www.ubuntuforums.org/forumdisplay.php?f=95")

but i am quite sure it is a cd problem... so... try again with a new cd and report here ;)[/QUOTE]

Right disc drive problem... I'll have to deal with that later. I managed to install to my second HD from my laptop.

BUT, the installer failed to install yaboot. It nevertheless let me continue the installation process...

Not having yaboot seems like its going to be a problem to me... No?

I have'nt tried to launch Ubuntu yet (this is real time stuff here...)

Colin

---

