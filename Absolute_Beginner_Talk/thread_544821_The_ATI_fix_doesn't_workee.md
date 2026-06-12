---
title: "The ATI fix doesn't workee"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by hamhoks on 2007-09-06
Hey there.

I have an ATI Radeon X850 XT Platinum Edition and seems like it just won't work.

I've installed the OS and run this fix ([Installing Ubuntu 7.04: ATI X**** Cards ]("http://ubuntuforums.org/showthread.php?t=414194")) and whenever I restart the rig, I get not the [COLOR="Blue"]**BLUE**[/COLOR] but instead the **BLACK **screen of death meaning, monitor appears to shut down :)

I've reinstalled the OS from scratch and again applied the [FIX]("http://ubuntuforums.org/showthread.php?t=414194") and still, monitor shuts down.

If it helps, I chose the 3 default resolutions so that my max was 1024 x 768.

How do I go about making sure I have the latest ATI drivers installed?  I ask because I reall have no clue regards where the [FIX]("http://ubuntuforums.org/showthread.php?t=414194") gets them or if they are the latest drivers.

And thanks for looking!

---

### Post by SOULRiDER on 2007-09-06
Can you boot into recovery mode or do you have issues there too?

---

### Post by hamhoks on 2007-09-07
Thank you for the reply!

I had to boot into the recovery console to apply the [fix]("http://ubuntuforums.org/showthread.php?t=414194") so, as far as I can tell, the recovery console is OK - minus graphics of course :)

---

### Post by hamhoks on 2007-09-10
bump di bump di bump di bump di bump !

---

### Post by Brightbelt on 2007-09-10
The program 'Envy' worked for me when nothing else would. It works for installing ATI drivers as well as Nvidia.

Go here [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

Good Luck, Frank B.

---

### Post by asmoore82 on 2007-09-10
worth a shot ...

Xorg has a new confg-less automagic configuration;
I highly doubt that it will load the fglrx driver for you,
BUT it may at least get you some working graphics to
copy and paste some config files on the forums :) ...

from your recovery console, rename the Xorgconfig file ...
```
(rootprompt)# mv /etc/X11/xorg.conf "/etc/X11/xorg.conf_$(date)"
```

We are intentionally _not_ putting a config file in its place to force Xorg
to do its automagic stuff; so now simply reboot.
```
(rootprompt)# reboot
```

If you get a GUI, post the contents of that xorg.conf backup file ...
```
~$ cat /etc/X11/xorg.conf_*
```

---

