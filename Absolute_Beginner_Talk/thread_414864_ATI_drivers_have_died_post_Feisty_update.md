---
title: "ATI drivers have died post Feisty update"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by showty on 2007-04-20
I have a 9600XT, and after I updated from Edgy to Feisty (I had direct rendering support before) it came up with an xorg error. So I reset my xorg config and set it back to ATI (rather than the flsomething drivers).

Rebooted, back to GUI, albeit without direct rendering. Then that new administration function (Restricted Drivers Control) comes up, telling me to enable my ATI graphics card drivers. So I do. Then it reboots, and whala, another xorg error. I reset the config, and back to Mesa we go!

I checked in synaptic, I have the driver package, just like I did in Edgy, up to date, but if its put into my xorg config it wont load.. what should I do? Really want to keep playing Deus Ex! :D

---

### Post by showty on 2007-04-20
Bump because its slipped off the front page..

---

### Post by thesphine on 2007-04-20
I think your card is on the no-longer supported list by the fglrx driver - you'll have to either switch to the OSS driver or buy a different card.

Cheers,

Steve

---

### Post by showty on 2007-04-20
Hmm, can't I just use the version I was using before?!

If not, how can I install the OSS driver? Will I suffer a performance drop?

---

### Post by showty on 2007-04-20
bump to the first page again..

---

### Post by wyth on 2007-04-20
The oss driver for ATI is ati, whereas the proprietary ATI driver is fglrx.  Funny how they chose the names.

But to get the oss driver, you'll need to do this at the command line:
```
sudo-dpkg xserver-xorg
```When you get the option for the driver, choose ati.  Follow the rest as normal, and at the end run
```
sudo shutdown -r now
```to restart.  That should get you the oss ATI drivers.

I'm using an older ATI Radeon R250, and these drivers *work*, but my fan is sprinting all day long, the card is running hot, and anything a little gfx-intensive gets me lines across my screen (like watching a video).  I can't get any good info on fixing this, and I've become a constant lurker on the threads hoping for an answer.  This is disappointing, because I never really had these problems with fglrx in the past, but fglrx isn't playing nice with Xorg 7.2.  We either need better oss drivers, or fglrx needs some pressure.  I'd swap out my card, but it's a laptop.

---

### Post by kittyhawk63 on 2007-04-20
I was going to say, since Feisty is LTS, I would seriously consider buying a video card that Feisty supports. However, if it is too hard, near impossible, to upgrade a laptop yourself, that option may be out. Put up one point for desktop, among other things, esp. price differences versus system features. Put up one point for laptops for their wonderful portability.
kh

---

### Post by wyth on 2007-04-20
Y'know, I may look into changing out my video card.  I have no problem tearing down my laptop; I've done it more times than I care to remember.  I've never tried to replace a video card in it, and never thought too because I always understood they were pretty tightly integrated.  But if it's possible, I'd say it's worth it.  

The question is which is the best card to run Ubuntu on a laptop?  I believe Nvidia is the way to go, but not quite sure, and just not sure which one will give the best performance.

---

### Post by kittyhawk63 on 2007-04-20
> **wyth said:**
> Y'know, I may look into changing out my video card.  I have no problem tearing down my laptop; I've done it more times than I care to remember.  I've never tried to replace a video card in it, and never thought too because I always understood they were pretty tightly integrated.  But if it's possible, I'd say it's worth it.  
The question is which is the best card to run Ubuntu on a laptop?  I know Nvidia is the way to go, just not sure which one will give the best performance.
 I would start a new thread and post a "Poll". See what others say. I've read more and more use Nvidia because Linux supports Nvidia.

---

### Post by showty on 2007-04-20
Guys - I'm not getting direct rendering with the 'ati' drivers.

---

### Post by freebird54 on 2007-04-20
There may be some 'leftovers' in your xorg from having the fglrx drivers before.  If you post it I can take a look.  What version of fglrx did you run before? (if you can remember!)

---

### Post by wyth on 2007-04-20
What does ```
glxinfo | grep "glx vendor string"
``` and ```
glxinfo | grep "direct rendering"
``` show?

---

