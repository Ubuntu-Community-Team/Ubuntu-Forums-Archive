---
title: "massive screen scroll"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Rick Doll on 2007-12-09
Now that I have my nvidia driver installed I have set my depth at 1024 x 768.

My screen really scrolls far to the top/bottom and left/right though, have to mouse over in those directions to get part of the pages.

This is on desktop or anything.

Is there a work around?

---

### Post by Nano Geek on 2007-12-09
You are running Compiz (a.k.a. Desktop Effects), correct?

---

### Post by Rick Doll on 2007-12-09
Sorry, not sure what that is, just installed linux last night :)

---

### Post by Nano Geek on 2007-12-09
That's OK.

Go to **System=>Preferences=>Appearance=>Visual Effects**, and if it looks like that screenshot I attached, then you are not running [Compiz]("http://en.wikipedia.org/wiki/Compiz") (click on the link for a description of what Compiz can do.)

---

### Post by jordanmthomas on 2007-12-09
How does this have anything to do with compiz?

---

### Post by Rick Doll on 2007-12-09
Hmm, I did a search synaptic package manager and it shows that it is installed but I still have that same screen as the screen shot you posted.

---

### Post by Nano Geek on 2007-12-09
Try hitting **ALT+F2** and typing **metacity --replace** and see if that fixes the problem.

---

### Post by Rick Doll on 2007-12-09
Still stretches, its like it thinks it should be set for one depth but its actually set for another.

So its stretching it as far as it thinks it should go even though the actual screen is only set for 1024x168.

I am just talking out of my rear though as I don't really know :)

---

### Post by Nano Geek on 2007-12-09
Try running this, answering the questions, and rebooting your PC.```
sudo dpkg-reconfigure -phigh xserver-xorg
```This will reset the settings on your display and ask you a few questions such as your screen resolution and depth. 
Hopefully it will solve your problem.

---

