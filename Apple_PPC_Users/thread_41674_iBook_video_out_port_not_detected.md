---
title: "iBook video out port not detected"
date: 2005-06-14
forum: Apple PPC Users
---

### Post by godsunderstudy on 2005-06-14
Brand new iBook G4, 1.2 MHz, 12".
 :???: I have to give a presentation at work. Thought I'd be a guerilla advocate and use the superior Ubuntu instead of the expected Microsoft. Test run today - Gnome won't detect the video out port. 
Any ideas much appreciated.

---

### Post by cow_racer on 2005-06-15
[QUOTE=godsunderstudy]Brand new iBook G4, 1.2 MHz, 12".
 :???: I have to give a presentation at work. Thought I'd be a guerilla advocate and use the superior Ubuntu instead of the expected Microsoft. Test run today - Gnome won't detect the video out port. 
Any ideas much appreciated.[/QUOTE]


Check out m3mirror.
[http://penguinppc.org/~benh/](http://penguinppc.org/~benh/)

Also check out this solution.
[http://lists.debian.org/debian-powerpc/2005/02/msg00364.html](http://lists.debian.org/debian-powerpc/2005/02/msg00364.html)

---

### Post by statico on 2005-06-16
```
m3mirror
``` appears to only work with Ben's modified 2.4 kernels. Am I wrong?

---

### Post by jonatin on 2005-06-18
[QUOTE=statico]```
m3mirror
``` appears to only work with Ben's modified 2.4 kernels. Am I wrong?[/QUOTE]
The m3mirror solution is for Ben's kernels, it's Ben's tool.

Since the new iBooks have radeon cards, you can use various dual monitor hacks.  Search around for combinations of **ibook**, **xinerama**, **mergedfb**, and **xorg.conf**.  You'll have to edit your xorg.conf file and restart the x server... and if it doens't 'take' you might be stuck in text mode... so be prepared for some command line text editing.

I'd give you the specifics, but my poor iBook 500 doesn't have a radeon.   :neutral:   Hopefully this will get you pointed in the right direction.  If so, come back and share your sucess!

---

### Post by statico on 2005-06-19
Ack, I should have just tried the command before badgering. m3mirror correctly turns on video mirroring for my VGA port on my Powerbook G3 (Pismo) with one of the ATI Rage 128 Mobility chips.

---

### Post by jonatin on 2005-06-19
[QUOTE=statico]Ack, I should have just tried the command before badgering. m3mirror correctly turns on video mirroring for my VGA port on my Powerbook G3 (Pismo) with one of the ATI Rage 128 Mobility chips.[/QUOTE]

It's not exactly a 'Brand New' G4 12" but whatever works... :smile:

---

