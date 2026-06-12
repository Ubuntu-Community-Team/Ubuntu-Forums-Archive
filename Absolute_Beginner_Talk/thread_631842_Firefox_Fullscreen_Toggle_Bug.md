---
title: "Firefox Fullscreen Toggle Bug"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by rossdub on 2007-12-04
I'm a complete newbie, so I'm not sure if I'm even posting this in the right place, but I'm getting some weird effects when I toggle Firefox to fullscreen (F11).  

I'm running gutsy with compiz fusion, and when I toggle to full screen and right click a link to open in new tab, the entire screen goes black (momentarily) except for the secondary right click menu.  

Also, when typing in text boxes the screen sometimes flashes between black screen and the web page where I'm typing.  

Anyone seen anything like this?  Is it a firefox issue or a compiz issue or neither?  Any help or direction in finding a solution would be appreciated.  Thanks

---

### Post by raul_ on 2007-12-04
Did you try disabling compiz and do the same steps to see if you get the error?

Sound like a graphics card issue to me

---

### Post by rossdub on 2007-12-04
Ok, I killed compiz, and that didn't fix the problem.  Then I killed compiz.real, which did get rid of the issue, but I lost all sorts of other functionality (my cursor focus was stuck in the terminal I had open).  Is this a configuration issue or is it my hardware as you mentioned in your earlier post?  Thanks.

---

### Post by discoade on 2007-12-04
I think this may be a fire fox problem! mine does the same thing but not if im using opera!

---

### Post by fishyf on 2007-12-16
> **rossdub said:**
> 
I'm running gutsy with compiz fusion, and when I toggle to full screen and right click a link to open in new tab, the entire screen goes black (momentarily) except for the secondary right click menu.  


I had this too and tried a tip from BoardDWorld
"Actually the black screen flicker is "very" easy to resolve. Just go to the System ---- Preferences ---- Advance Desktop Effects menu. Select General Options then Display Settings untick Detect Refresh Rate and manually set the refresh rate to 60Hz. Restart your system, done!"

Worked for me.

---

### Post by rossdub on 2007-12-16
Thanks for the tip...tried it and it didn't work for me.  Thanks though.

---

### Post by fishyf on 2007-12-17
Turns out it hadn't actually worked for me either. Something fixed it temporarily and I thought that it was this. Sorry.
Let us know if you find a solution.

---

### Post by ekuber on 2008-01-10
Go to "Advanced Desktop Effect settings" , uncheck "Unredirect fullscreen windows" in "General Options". That gets it working correctly. :)
In case you too have problems with full screen Flash videos displaying in a small window check "Support legacy fullscreen" in the plugin "Workaround".
Beware that the latter WILL get Firefox to keep a bug from a previous RC that makes changing tabs or selecting text not as responsive as it should... I recommend keeping it off unless you are lazy and watch a lot of online videos a day...

---

### Post by rossdub on 2008-01-10
Awesome!  Worked perfectly.  Thanks for the response.

---

### Post by explicitly ambiguous on 2008-03-09
Great -- this has been bugging me for ages!  Good to see there is a work around.  Does anyone know if there is a bug filled against this, as it should be easy to fix for everyone?

---

### Post by brewstah on 2008-04-26
This is not a Firefox issue.  It's a Compiz issue.  It happens here using other apps that have a fullscreen mode, like EOG and Epiphany.

There are several open, apparently related, bug reports at Launchpad regarding this.  In fact I just posted a detailed comment in one describing the 'uncheck Unredirect Fullscreen Windows' fix (workaround?). 

I actually went about disabling and re-enabling each active Compiz plugin, to see if that had any effect.  I had one false alarm.  But that didn't help.  So then I went into General Settings and there was the suspicious Unredirect Fullscreen Windows...so I unchecked it, and as others have seen, it worked.  Yay!

Now, if I had been better with my search terms in the first place either google or the forum search would have led me to thisi thread and helped save me a bit of time. d'oh :D

---

