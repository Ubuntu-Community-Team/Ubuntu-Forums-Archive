---
title: "No Suspend (to ram or to disk)"
date: 2012-10-24
forum: Apple Hardware Users
---

### Post by Farinet on 2012-10-24
After upgrading/installing from scratch to lubuntu 12.10ppc i realise there isn't anymore Standby or Hibernate.  The only thing is the screen is shut down, but the fan(s) are still running.

I'm on a PB G4 17" (2003) with a Radeon 9600.

Two remarks: 

1) I had the same (or similar) problem on a Samsung 535u3c (2xamd) laptop. There i could resolve the problem installing (from ppa) samsung-tools and the proprietarian fglrx video driver (from the repositories).

2) Before the release (and even in the final release) of 12.10 there were all kind of video issues. The desktop installer - often - needs a special boot line (in my case the installation was possible only from the alternate installer).

Now, i'd suspect the suspend issues might have to do with some video driver issue (unfortunately the fglrx does not exist for ppc - or am i wrong?). Someone out here has an idea how to tweak the built-in video driver so suspend may turn back? I'm clueless . . .

TIA!

---

### Post by 2F4U on 2012-10-24
FGLRX is not available for your graphics card,  because the card is too old. I would also assume that it is an issue with the graphics card. You may wish to look into /var/log/pm-suspend.log, which is a log file that lists in more detail the steps which happen when your machine suspends.
Since you have an ATI card, you could try adding nomodeset to the Grub kernel parameters. Sometimes it solves problems with older cards.

---

### Post by Farinet on 2012-10-24
> **2F4U said:**
> FGLRX is not available for your graphics card,  because the card is too old. I would also assume that it is an issue with the graphics card. You may wish to look into /var/log/pm-suspend.log, which is a log file that lists in more detail the steps which happen when your machine suspends.
Since you have an ATI card, you could try adding nomodeset to the Grub kernel parameters. Sometimes it solves problems with older cards.

Thanks a lot for the quick reply: 

It's not grub, it's yaboot, but that does not change so much, i presume ;-)

I'll try that this evening when i'll be back to the PB. Meanwhile just another question regarding the grub preferences. To get started ubiquity (with 12.10 that wasn't the case before) many of those who tried out the 12.10ppc dailies, had to set the following boot parameter:
live video=radeonfb:1024x768-32@60 (or whatelse your screen default resolution was).

Now, radeonfb points to framebuffers, right? Would there be some tweaking possible/useful as well? And is there a way to try out the bootparameters "on the fly"? Modprobing?

TIA

---

### Post by Maxim Feoktistov on 2012-11-12
I have the same problem with Samsung 535u3c.  To fix it, I disable "radion"  driver.  (Add the line:  ```

blacklist radeon

```
to  /etc/modprobe.d/blacklist.conf)  
With default VBE video driver suspend and wikeup work fine.

---

### Post by Farinet on 2012-11-12
> **Maxim Feoktistov said:**
> I have the same problem with Samsung 535u3c.  To fix it, I disable "radion"  driver.  (Add the line:  ```

blacklist radeon

```to  /etc/modprobe.d/blacklist.conf)  
With default VBE video driver suspend and wikeup work fine.

Great! That's interesting. I own the same identical machine and i've the same problems with it. I also tried fglrx but that's not a good option, imho.

The VBE video driver is built-in or shall i've to install it from somewhere?

Right now i checked my '/etc/modprobe.d' directory. There is no blacklist.conf but:
-  alsa-base-blacklist.conf
-  alsa-base.conf
-  fbdev-blacklist.conf ("# This file blacklists the framebuffer drivers.")
-  radeon-kms.conf (empty!?!?)

In the fbdev-blacklist.conf there is, among others, the radeonfb blacklisted. Any idea in regard?

TIA

---

