---
title: "various large fonts"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by thomseddon on 2008-01-30
ok 2 problems here:

1. When i am  logging in, the font is so large i cannot make out the letters, now i can deal with this as i can obv. manage to type my name/password with out seeing but this i would like to correct this issue please!

2. My window font jumps around from huge to massive, sometimes i will turn on and it will be so big it takes half the screen, so i reduce it to 1, and it is normal size, then that may work for a bit, but on another boot the font will be so small it cannot be read? so i whack it up to 10 again, this has no real implications except for inconvenience, (also when i was trying so show my, naive and narrow minded sister the bright alternative to windows, i had to change the font size and this just gave her reason to think linux is for geeks who have to tweak it all the time!!!! (i realise it is nothing to change but to her.....well she just wants it to work.......why use windows i hear you shout lol!! but its what you get use to, is it normal to adopt personal crusades to open peoples eyes to the world of alternative OS's primarily open source!)  << wow tangent, sorry....but yeh how can i stop this?

cheers

---

### Post by n00rt on 2008-01-31
bump to this thread as i'm having the same problem with ubuntu studio gutsy gibbon - splash screen login fonts are massive and in ardour the font used to show cursor position on the time line takes up half the screen!

any ideas on how to solve this?

---

### Post by n00rt on 2008-02-01
found another thread on this forum eventually (had to search google tho) that offers a solution - havent tried it yet myself but thought it might be useful - i'll post back if it gives me grief! 

Re: Huge Fonts on login screen
Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me.

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now

---

### Post by thomseddon on 2008-02-03
worked for the login font size, but what about the erratic window title size?

cheers

---

### Post by khai_huynh on 2008-05-04
hi, 
I have the same problem but worse than that, Not only my Login font is very big, but also in my KDE 4, the font is very big so i can see and adjust anything. However, my Gnome is working well. I don't know if i can fix that problem in GNOME? 

Can anyone help me with that problem ? 

thanks 
Khai HUYNH

---

### Post by williamlweaver on 2008-05-09
Thanks @n00rt!

Your -dpi 96 fix corrected large font login and large Window title fonts on HH 8.04.

Awesome!

-wlw  :)

---

### Post by reaganf2 on 2008-05-22
fixed my large login font trouble... thanx...

---

### Post by oldmuttonhead on 2008-06-05
That fixed a whole host of font issues I was having.  Thanks!!

---

### Post by /usr/bin/hacked? on 2008-06-11
Thank you so very much for this fix!

---

