---
title: "[SOLVED] New Monitor and Resolution?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Niedzwiedz on 2007-12-14
Well, I finally found a good deal on a LCD Flat Screen. It an HP W19B and man this look good. \\:D/
I may not need glasses anymore. :lolflag:
OK, in my screen resolution settings, my high choice is 1024x768 with a refresh rate of 75 Hz.
It have it set to 1024x768 @ 60 Hz.
This Monitor does support this and it really does look good. But, I downloaded the manual and it say it best @ 1440x900 @ 60 Hz (75 Hz is OK too). I not have this choice in my Screen Resolution (The 1440x900). Graphics card supports more or less.

Should I leave well enough alone (If it works, don't fix it), or should I try; 
sudo dpkg-reconfigure xserver-xorg
And see whatever I can do to optimize the Monitor's capability? :confused:

In Screens and Graphics it show the Monitor as Plug-n-Play.

---

### Post by siciliancasanova on 2007-12-14
First of all you want to fix this.  Or I would.  If only just for practice.  I am very glad I learned how to configure .xorg in my brain because there have been times when I've brought my machine to someone else's house to watch a movie and sure enough it doesn't auto pick up on the monitor.  So I just busted into the command line and a few seconds later poof the monitor was working.

Do you want this screen resolution? 1440x900?

Follow any of the xorg guides out there, you will only need to reconfigure if you screw it up.

But right now you're just going to be in /etc/X11/xorg.conf making changes to the monitor and refresh rates.

---

### Post by Niedzwiedz on 2007-12-14
> **siciliancasanova said:**
> First of all you want to fix this.  Or I would.  If only just for practice.  I am very glad I learned how to configure .xorg in my brain because there have been times when I've brought my machine to someone else's house to watch a movie and sure enough it doesn't auto pick up on the monitor.  So I just busted into the command line and a few seconds later poof the monitor was working.

Do you want this screen resolution? 1440x900?

Follow any of the xorg guides out there, you will only need to reconfigure if you screw it up.

But right now you're just going to be in /etc/X11/xorg.conf making changes to the monitor and refresh rates.

OK, I had an idea this was coming. :rolleyes:
This how I been learning, by doing. I will give it a whirl and hope to learn. May need to help someone else someday. Taking it "as is" not teach me. Thanks. :mrgreen:

So, yes, I want to try the 1440x900 and see if it get better.

---

### Post by siciliancasanova on 2007-12-14
Yeah and depending on the quality of your eyes it should look smoother when you fix that refresh rate also.

I know hardly any commands in Linux by memory.  But all it took is one time with me screwing up .xorg and not being able to get back to the internet and not having the commands written down, for me to teach myself those commands.

---

### Post by Niedzwiedz on 2007-12-14
Yesssss! I think it looking good. Another learned step, I was afraid to take. 
You buy the Beer and I bring the Popcorn :popcorn: Thanks!

---

