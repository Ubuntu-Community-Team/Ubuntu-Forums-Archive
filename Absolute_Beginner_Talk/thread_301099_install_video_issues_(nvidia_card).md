---
title: "install video issues (nvidia card)"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by jadedcritic on 2006-11-16
Hey all, seeking some advice.

Long story short, my primary PC is having some install trouble, I'll get to the "start or install" prompt on ubuntu and the screen will just literally black out, presumably as the video drivers load;  In my own wacky experiments, I've tried multiple monitors, and multiple PC's - I can honestly say the only other issue I've noticed is a quirky flickering on the LCD screen on my laptop.  (But the install went fine).   In any case, my other PC's are taking to Ubuntu fairly readily. I can only assume the video card is the issue (Geforce 6800GS).

I've been kinda lurking the forums where I can, looking for others that may have had similar issues;  I did see several people recommend the "install from graphics safe mode" option, but I tried that as well, and had no luck 

Any advice? :confused:

---

### Post by tzulberti on 2006-11-16
You could use "sudo dpkg-reconfigure xserver-xorg" and then "sudo /etc/init.d/gdm restart"

---

### Post by jadedcritic on 2006-11-17
Can't type anything - can't see anything at all on the screen; literally;  Granted, I can touch type, but I'm not sure I want to go there yet though.   Surfing the forums though, I did get an idea.  Someone pointed out there's an install CD for 64 bit Athlon processors.   I completely forgot I was using a 64 bit machine.   Not quite sure how that would cause video issues, but I thought I could give it a try, beats giving up.

---

