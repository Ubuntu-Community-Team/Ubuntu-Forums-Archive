---
title: "[SOLVED] Question about booting from XORG"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by jso2897 on 2007-08-16
If one is booting from a live CD and needs to make changes to XORG to boot up, how can you boot directly into X without rebooting completely and losing your changes? i realize this is a really dumb question, but after i have edited and ctl-X to close XORG, i don't know what else to do but reboot. How can i save my chnages and go directly into X?:confused:

---

### Post by ddrichardson on 2007-08-16
CTRL-ALT-Backspace Resarts X or GDM

---

### Post by jso2897 on 2007-08-16
So instead of giving the line command to reboot all I had to do was ctl-alt-bksp. That should have occurred to me - thanks!

---

### Post by mgarces on 2007-08-16
Im not sure, since you are using a liveCD, but you normally accomplish this by changing init levels... In a normal system, you can go to the console, type "init 3" (runlevel 3, no X display), and when you are there, type init 5 (runlevel 5, with X display) and you will get back to X. I don't have a live cd right here with me to test it, but this should work... =)

Also, if you are already in X, and you want to test you new configurations, just do a "CTRL+ALT+BACKSPACE"... this kills xorg, and it restarts automatically.

Let me know if this helped you, if not I will try to get my hands on a liveCD to find you a answer! :)

---

### Post by mgarces on 2007-08-16
I was late :lolflag:

---

### Post by ddrichardson on 2007-08-16
No - I was just too fast ;-)

---

### Post by jso2897 on 2007-08-16
Nope. neither of those things worked. When you are on the command line in safe mode, ctl-alt-bksp does nothing. neither does "init 5". This is driving me nuts - there must be a way to make changes to a live CD install and proceed into X after you have edited XORG.
(Note: what I am doing is trying to get it to recognize my PCI video card - the address in XORG appears to be wrong.)

---

### Post by ddrichardson on 2007-08-16
You didn;t mention you were on the command line. Have you tried good old fashioned startx?

---

### Post by jso2897 on 2007-08-16
DDricharson: Yes. StartX worked. My changes didn't work, but at least now I know how to restart X to chaeck them. Thanks a bunch! Ubuntu forum people are the best!:KS

---

### Post by ddrichardson on 2007-08-16
Glad it helped - don't forget to mark the thread as solved ;-)

---

