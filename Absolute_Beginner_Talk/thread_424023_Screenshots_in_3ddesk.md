---
title: "Screenshots in 3ddesk"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Skelsgard on 2007-04-26
Well, that's the wuestion asically?
How to take screenshot of 3ddesktop while in "changing mode", as anything seems to die until you select back a desktop.

Cheers

---

### Post by igknighted on 2007-04-26
> **Skelsgard said:**
> Well, that's the wuestion asically?
How to take screenshot of 3ddesktop while in "changing mode", as anything seems to die until you select back a desktop.

Cheers

Try setting the delay to zero and hitting the printscreen button.

---

### Post by Skelsgard on 2007-04-26
Thanks for reading and the fast reply :) 
There's no "delay" option visible in either 3ddesk help or 3ddesktop.conf.
I still tried with a "delay 0" parameter just to check, but no luck. Tried randdelay too, just to make sure.

With and without the funky "delay" option, screenshot are either not taken (the button not pressed fast enough?) or taken before it enters the panels view.
No commands are acknowledge once in this mode.

Any further help, deeply appreciated.

Cheers.

---

### Post by ronmarley1 on 2007-04-26
Open Gimp and then click File -->Acquire -->Screen Shot... and it will let you set a delay to take the screen shot.

---

### Post by Skelsgard on 2007-04-26
Already solved it in the IRC channels, but thanks a lot anyway.
It was easy actually: launch gnome-screenshot from terminal so you can set a delay of a few seconds.
# gnome-screenshot --delay=5
Imagine it works just as the GIMP solution, only it allows me to use keybindings.

Thanks to all the ones that replied,very much appreciated your help :) :)

---

