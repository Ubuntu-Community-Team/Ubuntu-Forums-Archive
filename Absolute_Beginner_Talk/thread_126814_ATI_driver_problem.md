---
title: "ATI driver problem"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2006-02-07
Ok I followed the ati HOW TO: [http://www.ubuntuforums.org/showthread.php?t=75378]("http://www.ubuntuforums.org/showthread.php?t=75378")
and now I have a problem. 

I installed this driver and it works on the computer at work (were I installed it) but upon taking it home, after 5 seconds at the usplash login screen, it goes blank then I get a message that says [PHP]Input signal out of range[/PHP] Then the screen goes blank. How do I correct this?

Also what the heck is this driver so darn interested in my mouse and keyboard? the questions on those two topics were 5:1 about the graphics.

---

### Post by Micro Rotors on 2006-02-08
Hmmm,, Know one knows how to correct this?

---

### Post by Dizaster on 2006-02-08
Are you outputting to a tv or anything else throught the ATI card?

I had a very similar problem a couple of weeks ago (working in windows). I got the same error message as you. It turns out that the card was sending a signal to bothe the monitor and the tv and the two were getting conflicted.

I disconnected the TV and everything worked from there (just had to change a few settings, cant remember which though)

Dont know if this helps or not!

---

### Post by Micro Rotors on 2006-02-08
Hello Dizaster

No I do not have it connected to anything but the monitor.

---

### Post by David Corrales on 2006-02-08
It probably has to do with the vertical/horizontal ranges in Hz. Check the monitor manual or the backpanel info for these ranges, then edit the file **/etc/X11/xorg.conf** and make sure the values there match the ones from your monitor.

---

### Post by Micro Rotors on 2006-02-09
ok guys, that worked! ;)

---

### Post by David Corrales on 2006-02-09
woot! :mrgreen:

---

