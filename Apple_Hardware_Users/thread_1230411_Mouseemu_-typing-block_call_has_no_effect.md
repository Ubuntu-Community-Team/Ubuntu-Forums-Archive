---
title: "Mouseemu -typing-block call has no effect"
date: 2009-08-03
forum: Apple Hardware Users
---

### Post by sha.goyjo on 2009-08-03
Hey, I've been working on getting jaunty working well on my fiancee's ibook g4 1.33 ghz, and I only really have one thing that I just haven't been able to get working right (aside from flash, damn you macromedia!). It's the darn mouseemu. It's probably a lack of understanding on my part that is causing it, but I just don't get why the -typing-block call doesn't seem to have any effect. My mouseemu in /etc/default looked like this after installation
```

#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

```
First off, how is mouseemu doing anything with all of those wrapped in comment code? So, since typing block wasn't having any effect, I did this
```

#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
#TYPING_BLOCK="-typing-block 1000" # block mouse for 1000ms after a keypress

```
Just seeing if a longer delay would make it more apparent. It didn't.
Finally I tried this:
```

#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 1000" # block mouse for 1000ms after a keypress

```
Still no dice. Could someone who understands the ppc ubuntu port better than I (I'm an AMDx86_64 kinda guy) and knows their way around mouseemu lend a hand with this? Is something other than mouseemu controlling the mouse on a default install? Is mouseemu simply not functioning properly? Is there some ridiculously simple and stupid thing I am missing which I need to do to make this work?

Any help is appreciated.

---

### Post by sha.goyjo on 2009-08-05
bump....nobody here interested in the ppc arch?

---

### Post by pmcelwee on 2010-04-01
I am having the same problem (300 milliseconds is not long enough to keep me from constantly fumbling with the touchpad). I have changed what you changed, but it is not increasing the time that the touchpad is disabled.

Have you found a solution?

---

### Post by linuxopjemac on 2010-04-02
You have to remove a #, to make it look like this:

```
MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress
```

This will give you the middle mouse click on F11 and the right mouse button on F12. You can also uncomment the other MID_CLICK/RIGHT_CLICK but you have to comment the ones uncommented out now...I don't know whaat uncommenting the SCROLL does...

PS a # before a line is not interpreted in code, only code without a # is interpreted....

---

