---
title: "LiveCD &amp; Blank screen"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-09-23
Using the 7.04 LiveCD from Shipit, I choose install Ubuntu & computer grinds away but stops with a blank screen and responds to nothing (no terminal).  Strangely, I already have Feisty installed on this laptop (Dell 6400) and was going to use LiveCD to create separate /home partition (following [Psychocats tutorial]("http://www.psychocats.net/ubuntu/separatehome"))

I can't remember if I had this problem when first installing Feisty or how to get around this!  Anyone know what the issue might be & how to fix?
Thanks.

---

### Post by n3tfury on 2007-09-23
use this instead, sir

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by flyingsolo on 2007-09-23
Thanks n3tfury.  I have a gparted cd already so, yes that would work to redo the partitions but part 2 of what I'm doing is to reinstall the Feisty OS or Gutsy in attempt to get wireless working but the install hangs on blank screen.

---

### Post by n3tfury on 2007-09-23
oh, sorry, i didn't know about part two :)  i'm sure someone will be along to help that issue.

---

### Post by flyingsolo on 2007-09-24
OK--I've solved my own problem but thought I should post in case others come this way.  The problem is related to the ATI graphics card I have and so runs into xorg problems.  The fix was:
1. Load Live CD & choose F4 (VGA) --> select 1024x768x16; eventually, you'll get a command line (enter 'no' to choice to try and fix xorg screen)
2.  At command line use;
   sudo -s
   apt-get install xorg-driver-fglrx
   aticonfig --initial
   startx
Since this requires internet connection, use a wired connection b/c wireless on laptop often won't be working from liveCD (depending on your wireless card)
This should deliver you to a visible Ubuntu desktop provided via the liveCD.
(credit to thayerw on a post from april 20th/07 but i've lost the link!)
Cheers.

---

