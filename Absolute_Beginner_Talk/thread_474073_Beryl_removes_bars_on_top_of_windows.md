---
title: "Beryl removes bars on top of windows"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-14
hey!

I'm having lots of fun with Beryl, but every time I launch it, applications (like the firefox I'm typing into) loose there "bar" at the top. The bar that says the program's name, and also contains the minimize, maximize, and close buttons.

It's just.... gone. :P

Can someone help?

---

### Post by overdrank on 2007-06-14
> **alecwh said:**
> hey!

I'm having lots of fun with Beryl, but every time I launch it, applications (like the firefox I'm typing into) loose there "bar" at the top. The bar that says the program's name, and also contains the minimize, maximize, and close buttons.

It's just.... gone. :P

Can someone help?

Hi you can try and reload the theme manager. Right click on the red diamond select reload widow decorator. Hope it works! :KS

---

### Post by alecwh on 2007-06-14
Nope, I've tried that.

---

### Post by tahuya_rat on 2007-06-14
> **alecwh said:**
> Nope, I've tried that.

Well, I only played with Beryl for a couple days (a couple weeks ago) so I'm no expert, but as I recall, I just hit the "Show Desktop" button in the lower-left corner before I started Beryl, and that seemed to keep that problem from happening.

If that doesn't do it, I think that starting the Beryl manager with no open windows will keep it from happening.

A pain in the butt, to be sure, but all that eye candy is pretty fun to play with when it's all cooperating!

-tahuya_rat

---

### Post by Zalbor on 2007-06-14
It's probably a line missing in the /etc/X11/xorg.conf file. It's an option that needs to be turned on in order for beryl to display window borders (which is what you're missing).
Open that file as root (try this command: gksudo gedit /etc/X11/xorg.conf ), go to where it says: Section "Screen" and just before the next "endsection" add this line:
Option			"AddARGBGLXVisuals" "True"
Log out, press ctrl+alt+backspace to restart X, and it should be OK.

---

### Post by old_geekster on 2007-06-14
I have this happen periodically.  I simply go to the Red Gem, right click and check that "Beryl" is selected in "Select Window Manager".  If it is, then I usually will change to one of the other managers and then click again on Beryl.  This usually corrects the problem.

---

### Post by alecwh on 2007-06-14
That worked poerfectly!

Thanks for the awesome tip, man, I love Ubuntu. Best thing I've ever switched to in my life.

---

### Post by tahuya_rat on 2007-06-14
> **Zalbor said:**
> It's probably a line missing in the /etc/X11/xorg.conf file. It's an option that needs to be turned on in order for beryl to display window borders (which is what you're missing).
Open that file as root (try this command: gksudo gedit /etc/X11/xorg.conf ), go to where it says: Section "Screen" and just before the next "endsection" add this line:
Option			"AddARGBGLXVisuals" "True"
Log out, press ctrl+alt+backspace to restart X, and it should be OK.

Dang, man, this should be added to the howto!  I re-installed Beryl (just did a nuke job on the box about a week ago, ya know), and tried this,  and Beryl is completely smooth.  None of the wierdness (including the title-bar disappearance issue) that I had before.

Thanks for the great tip!

-tahuya_rat

---

### Post by MattyGabe on 2007-08-14
Zalbor, you hit the nail on the head.  I too had this problem and the Option "AddARGBGLXVisuals" "True" was not in the xorg.conf file.  Good work!

---

### Post by clrumivier4life on 2007-08-16
THANK YOU THANK YOU THANK YOU!!! I've been messing around with this for hours trying all sorts of things and this one simple line fixed all my problems.

---

