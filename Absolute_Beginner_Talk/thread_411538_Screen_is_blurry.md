---
title: "Screen is blurry"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by owerio on 2007-04-17
Hello. There is  blurriness  on screen  while I surf the internet with firefox. Even I changed the fonts and tried other zoom options I coudnt solved the screen problem. Is it a general problem or have I done some wrong during install?

 Thanks in advance.

---

### Post by lunarmelody on 2007-04-17
Did you install the correct drivers for your video card?  I had a similar problem at first with firefox when I first started, and that was the problem.

---

### Post by owerio on 2007-04-17
> **lunarmelody said:**
> Did you install the correct drivers for your video card?  I had a similar problem at first with firefox when I first started, and that was the problem.
Hello. Yes already did. Somewhere , I have read to change the monitor Hz to solve this. But I dont know how to change Hz of monitor. Could someone help,please?

---

### Post by lunarmelody on 2007-04-17
Go to System -> Preferences -> Screen Resolution.  There's an option in that box called "Refresh Rate" that is measured in Hz.  I think this is what you want.

---

### Post by t1m on 2007-04-29
> **lunarmelody said:**
> Go to System -> Preferences -> Screen Resolution.  There's an option in that box called "Refresh Rate" that is measured in Hz.  I think this is what you want.

Hmm, I tried that, but there's only one option (85hz). :-k

---

### Post by TheFourElements on 2007-04-29
Maybe it's your glasses. Did you try cleaning them?

---

### Post by lunarmelody on 2007-05-01
Check out this thread:  [http://ubuntuforums.org/showthread.php?t=344430&highlight=changing+screen+refresh+rate](http://ubuntuforums.org/showthread.php?t=344430&highlight=changing+screen+refresh+rate).  There seem to be some ideas here.

---

### Post by t1m on 2007-05-06
I tried [this]("http://ubuntuforums.org/showthread.php?t=270245") and it worked!

Open Terminal (or Konsole) and type this:
```
sudo gedit /etc/X11/xorg.conf
```
(you can use kate instead of gedit)

There is a section that looks similar to this:
 ```
 Section "Screen"
 Identifier "Internal Screen"
 Device "Internal Device"
 Monitor "Internal Monitor"
 DefaultDepth [COLOR="Red"]**16**[/COLOR]
 SubSection "Display"
 Depth [COLOR="Red"]**16**[/COLOR]
 Modes "1280x768"
 EndSubSection 
 EndSection
``` 
(it may have more stuff in it)

Try changing the 16 (in red; do the first and last if there are more than one 'sections') to  24. Save the file and restart the X server (press CTR + ALT + Backspace).
Does that help?

---

