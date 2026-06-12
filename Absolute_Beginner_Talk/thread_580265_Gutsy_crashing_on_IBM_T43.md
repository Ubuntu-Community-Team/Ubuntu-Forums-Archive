---
title: "Gutsy crashing on IBM T43"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Wynne G Oldman on 2007-10-18
Hi. I downloaded the 32 bit version of Gutsy today. Every time I try to use Synaptic, it just crashes. The screen either locks up totally, or it locks up and I can move the mouse pointer, but am nothing happens when I click on any controls. The only way out of it seems to be to turn the machine off. I installed Gutsy RC on a T42, and that works fine. Any ideas?

PS It takes an absolute age to boot. It boots much much quicker on the T42 and that's not as high spec. Also, the progress bar and splash screen are not present on boot, just a bank screen. When it finally does boot, 3D effects are enabled and working OK with the standard driver.

---

### Post by Wynne G Oldman on 2007-10-18
One more thing. I can't get Totem to play DVD's, even though I've installed all the CODECS. Gutsy works great on my Intellistation, and on a work T42, it's just not getting on at all with the T43:(

---

### Post by Whiffle on 2007-10-18
I'm doing a fresh install on my t43 right now, ill let you know how i come out.    I had Gutsy working fine, i just wanted to rearrange my hard drive a bit.

---

### Post by durfff on 2008-02-08
Hi there, 

Just thought I'd boot up Ubuntu on my T43 as I've not done it for a while... Why? It kinda kept crashing, not on synaptic but it could be anywhere - I had the feeling it might be to do with compiz, as on crashing I sometimes got blue rectangles on the borders of some windows, but never found out. If I find out anything I'll let you know

Regarding your second problem (ages to boot + no splash screen), I had the same issue and I've sorted it - can't remember how though! I'll take a little time to research it and let you know as well.

---

### Post by durfff on 2008-02-08
try this: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen")

---

### Post by durfff on 2008-02-08
Mmmmh... I just checked /var/log/syslog and found these interesting lines:

```
Feb  8 18:39:12 fred-laptop kernel: [  470.228000] Uhhuh. NMI received for unknown reason a1 on CPU 0.
Feb  8 18:39:12 fred-laptop kernel: [  470.228000] You have some hardware problem, likely on the PCI bus.
Feb  8 18:39:12 fred-laptop kernel: [  470.228000] Dazed and confused, but trying to continue
```

I'm confused myself!!! Anyone heard of that before? Check yours as well, let's see if you find anything...

By the way my lappi has been running various apps for about 2 hours without crashing now - I turned visual effects/compiz off earlier on, that seems to help!

---

### Post by Shanison on 2008-03-06
Same situation happens to me. My IBM T43 will crashes randomly. Sometimes every 3 or 5 minutes. Sometimes i can run smoothly for a few hours. 

For the black screen on boot, u need to edit the usplash.conf to the right screen resolution.

And for the crash, someone suggested me to install fglrx driver for my ATI card, i haven't done so though. Since now it is working fine, and i have just removed' cool and quiet' for BIOS as someone suggested. I wanted to test out what is exactly is the solution, so i need to see if this works or not. If it cann't , i will try to install fglrx driver for my ATI card instead of using the default ATI driver.

---

