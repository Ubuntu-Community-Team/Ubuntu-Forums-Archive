---
title: "Can't start live CD or install"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by icon on 2007-05-29
Hello, I'm completely new to ubuntu and linux. 
I'm using the 64-bit version of Ubuntu.

Before trying to install Ubuntu on my current machine, I tried it on my old one before I upgraded it. It worked perfectly. The only differences after the upgrade is that the motherboard is now a Asus Crossfire, and I'm using a AMD X2 6000+. When I pop in the disk and boot from it, I choose Start or Install Ubuntu and all I get is:

kernel is alive
kernel direct mapping tables up to 100000000 @ 8000-d000

Followed by a freeze and that's it. I've tried every option on the CD such as boot with safe grafics, check cd health, etc.. and each one gives me the same error message. Could anyone please direct me into where I can find information on how to fix this, or could anyone tell me what to do to get Ubuntu started. Thank you very much.

---

### Post by AAM on 2007-05-29
you may be suffering the scourge of Linux - new hardware. I found that I had to put irqpoll after the boot sequence to get things working, but the problem may be more basic. Is the mobo supported in linux?

---

### Post by jsc315 on 2007-05-29
yea i'm having the same problem.  i'm trying to install it on a AMD 3200+ I have been searching for help but with no luck. i'm going to try the 32 bit version  later to see if that works. If anyone can help that would be greatly appreciated.

---

### Post by rsambuca on 2007-05-29
> **icon said:**
> Hello, I'm completely new to ubuntu and linux. 
I'm using the 64-bit version of Ubuntu.

Before trying to install Ubuntu on my current machine, I tried it on my old one before I upgraded it. It worked perfectly. The only differences after the upgrade is that the motherboard is now a Asus Crossfire, and I'm using a AMD X2 6000+. When I pop in the disk and boot from it, I choose Start or Install Ubuntu and all I get is:

kernel is alive
kernel direct mapping tables up to 100000000 @ 8000-d000

Followed by a freeze and that's it. I've tried every option on the CD such as boot with safe grafics, check cd health, etc.. and each one gives me the same error message. Could anyone please direct me into where I can find information on how to fix this, or could anyone tell me what to do to get Ubuntu started. Thank you very much.

With that chipset I think you will have to add the boot option "ide=nodma".  Press F6 at the main menu to enter the boot options, and then enter ide=nodma before the -- at the end, and leave a space before the dashes.  Then see if that boots.

If it does, you will want to turn dma back on after it boots into the liveCD before installing or it will take forever.

---

### Post by icon on 2007-05-29
Thanks, I'll try this. If it does work, how do I turn dma back on and install without getting the message? Like jsc I'll try the 32 bit version if the nodma dosn't work.

---

### Post by rsambuca on 2007-05-29
> **icon said:**
> Thanks, I'll try this. If it does work, how do I turn dma back on and install without getting the message? Like jsc I'll try the 32 bit version if the nodma dosn't work.

There is a bug with certain chipsets that won't boot easily from ide CD/DVD drives with certain boot parameters.  I do not have your motherboard, but I have the same northbridge chipset, and I had to enter the ide=nodma parameter in order to boot up.

After it has booted up (if it works:)), you just need to open a terminal while in the live CD (Applications -> Accessories -> Terminal), and then enter the following command for each ide drive:```
sudo hdparm -d1 /dev/hda
```You will have to do this for each ide drive ie. /dev/hda, then repeat for /dev/hdb, etc.

Then run the installer after you have turned dma back on.

Good luck.  

And by the way, if the ide=nodma option doesn't work, let me know and there are a bunch more you can quickly try.  I don't have them handy, but I can find them for you if this doesn't work.

---

