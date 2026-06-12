---
title: "Installing Ubuntu 7.04: ATI X**** Cards"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by meegs on 2007-05-20
I was having trouble with installing and then now loading ubuntu....and I have an ATI card

so I figured that I should follow this sticky [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
 and try to sort it out...

I have installed Ubuntu 7.04 using the alternate cd....this seems to have gone fine

I then could not boot into ubuntu it would stall in the normal mode (orange bar would not fully load) and in the recovery mode it would stall on the "loading drivers required for boot" and would print out an error of some sorts...ending with the line

agpgart: AGP aperture is 128M@0x0000000

So, I got some advice from an earlier thread
[http://ubuntuforums.org/showthread.php?p=2687411#post2687411](http://ubuntuforums.org/showthread.php?p=2687411#post2687411)

What I ended up doing was taking my ATI Radeon9250 Graphics card out and using the onboard Intel graphics card, boot into ubuntu.

This did work...but X wouldn't work because it still didn't like my graphics card, anyway, I did boot in, but only into the command line...

So in there I typed in everything as instructed in the sticky, and it seemed to all work....things were updated and upgraded and it looked like the aticonfig file thing worked and stuff....

So then I shut down, put my ATI Radeon Graphics card back in and tried to boot into Ubuntu....but once again....it just stalled in exactly the same way it did before I applied the sticky.

So that's my story...I really have no idea what to try next.....

any suggestions...

My puter specs are:
HPd220 Intel Pentium4  2.4GHz
512MB of RAM
 ATI Radeon 9250 graphics card

---

### Post by AlexenderReez on 2007-05-20
if i were you....i will reconfigure xserver .... andset its base is ati....and beside that...just same....


> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by meegs on 2007-05-20
Well, ok, I'm a bit of a noob and y'know....some more details would be most appreciated...

also, having done some more reading...my card is NOT an X**** card, so maybe I was doing the wrong thing anyway....

does anyone know how to get this thing working?

---

