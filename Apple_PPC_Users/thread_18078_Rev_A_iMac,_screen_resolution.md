---
title: "Rev A iMac, screen resolution"
date: 2005-03-04
forum: Apple PPC Users
---

### Post by mcnelson on 2005-03-04
Hey ho,
I'm so very wet behind the ears so bear with me - not only do I not know Ubuntu very well, I know nothing about Macs either, so I need a little help.

I used to run Mandrake 9.0 on  spare PC so Linux isn't a total mystery - anyway, I recently BOUGHT an old school, Rev A iMac JUST so I could chuck Ubuntu on it. I upgraded the 32MB Ram with an extra 128MB so I could actually install it and make it work now. It only has 2MB vid ram though.

The problem is the screen resolution is a ridiculous 512x384 @75hz. According to documentation I should be able to get 800x600 @95hz with 2MB vid ram. Gnome won't budge though, the only resolution selectable is 512x384. The Xconfig file shows a default of 800x600 though, so what's the deal? I had a quick play with xvidtune but that seemed to make minor adjustments only - if anyone can talk a newbie through this I'd be most appreciative!
 :-D

---

### Post by farruinn on 2005-03-04
You might try running 'sudo dpkg-reconfigure xserver-xfree86' and selecting medium when it gets to the monitor configuration part.  I would try it at lower frequencies - 95 sounds awful high...  BTW, 2MB video ram should be fine - the beige G3's get thousands of colors at 1152X768 with that.

---

### Post by mcnelson on 2005-03-04
Well, running that looked good - went through the keyboard and mouse crap, selected the 'medium' setting for monitor and put in the max size as 800x600 (just to be safe)....but then it crapped out with this message:

**/usr/sbin/laptop-detect: line 1: dmidecode: command not found**

...which I am obviously clueless about. Anyone cast some light on this? Am I doing something wrong?
 :-s

---

### Post by daniels on 2005-03-04
This one should be fixed in Hoary.

---

### Post by mcnelson on 2005-03-05
Cool, so it's not me that boned it! Thanks for all your help guys!

edit:
I thought I'd give editing my xconfig file another go, and removed every reference to 640x480 and just left 800x600 in. One quick reboot later and everthing looks peachy, and now Gnome shows a resolution of 1024x768? Obviously this pleases me, and although the end result is more than satisfactory, I remain unsure as to how I have effected such a transformation.

Once again, thanks for all your help chaps.

---

