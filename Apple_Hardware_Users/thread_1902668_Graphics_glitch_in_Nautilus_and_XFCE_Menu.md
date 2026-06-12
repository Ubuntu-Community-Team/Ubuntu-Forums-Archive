---
title: "Graphics glitch in Nautilus and XFCE Menu"
date: 2011-12-31
forum: Apple Hardware Users
---

### Post by Gadgetmo on 2011-12-31
I'm not sure if I gave this a good title, if anyone can think of a better one then please edit it! My menu and file manager icons look like this:

[IMG]http://f.cl.ly/items/3t2A0Y2d1A0G3108113G/2011-12-31-102510_1280x854_scrot.png[/IMG]

They sort of change when you put your mouse over them like this:

[IMG]http://f.cl.ly/items/242M0u0j0A1l041G3h35/2011-12-31-111244_1280x854_scrot.png[/IMG]

It also happens in File Manager:

[IMG]http://f.cl.ly/items/2b1m2j3y0v2M0F0c0g3v/2011-12-31-111639_1280x854_scrot.png[/IMG]

I have Debian XFCE on a Powerbook G4.

I'm running Linux debian 2.6.32-5-powerpc. I have 24-bit colour depth. My screen dimensions are 1280 x 854. My graphics card is VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

---

### Post by 2F4U on 2011-12-31
Well, I don't know much about Debian. However I have an old ThinkPad X31 with ATI Radeon 9600 running the open source ATI drivers and my icons look totally different than yours. It seems as if yours lost most of their colour while mine look mostly like yours when you hover with the mouse over them.

---

### Post by rsavage on 2011-12-31
Yeah, I've seen that before with my radeon card.  It was so long ago now though I can't remember what the problem was.  The solution will be one of the things detailed here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .

---

### Post by Gadgetmo on 2012-01-01
Well, I've given up.

I'm going to install YDL

---

### Post by rsavage on 2012-01-01
If you don't mind me saying that is a silly thing to do.
 
I'm sure the solution is trivial. Just creating an xorg.conf file will probably solve it. Have you tried that?
 
EDIT: Is it possible for you to post your Xorg.0.log file?

---

