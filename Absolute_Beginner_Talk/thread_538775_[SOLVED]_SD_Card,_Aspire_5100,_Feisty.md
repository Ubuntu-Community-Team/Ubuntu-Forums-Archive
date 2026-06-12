---
title: "[SOLVED] SD Card, Aspire 5100, Feisty"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by moocow1452 on 2007-08-30
Hi, I have a bit of a problem with an internal SD card reader with my laptop. I have got it ages ago, but I only recently realized that the SD slot wont work on it. After some googling, I have found nothing helpful except I'm supposed to run this command that lets you see your hardware, 'lipci' or something. Here's what I got...

```
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

```

Since I found nothing on google, I'm wondering if there is even a fix for this. Suggestions?

---

### Post by ThrobbingBrain66 on 2007-08-30
Give this thread a shot:
[http://ubuntuforums.org/showthread.php?t=420721](http://ubuntuforums.org/showthread.php?t=420721)

It's more for Texas Instrument readers, but it might work for you.

EDIT: I did some more searching, and right now it seems the only fix involves manually patching the sdhci driver
[http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html](http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html)

---

### Post by moocow1452 on 2007-08-30
> **ThrobbingBrain66 said:**
> Give this thread a shot:
[http://ubuntuforums.org/showthread.php?t=420721](http://ubuntuforums.org/showthread.php?t=420721)

It's more for Texas Instrument readers, but it might work for you.

EDIT: I did some more searching, and right now it seems the only fix involves manually patching the sdhci driver
[http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html](http://list.drzeus.cx/pipermail/sdhci-devel/2007-May/001735.html)
Thanks. but what do I do with it? The code does squat in the terminal.

---

### Post by ThrobbingBrain66 on 2007-08-30
Patching kernel modules can be difficult and messy.  In all honesty, you're probably better off waiting until Gutsy.  The patch should be a part of the module by then.

If you're feeling adventurous however, you can check out the following link:
[http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/](http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/)

I've only patched one package in my 1.5 years of linux experience and it was pretty involved.  Basically, you have to save the code from the link i gave in my previous post to a file called 'patch'.  Then the link I gave in this post gives the command to apply the patch.

Just be warned, I haven't tested applying the patch or the patch itself.  Good luck!

---

### Post by moocow1452 on 2007-08-30
> **ThrobbingBrain66 said:**
> Patching kernel modules can be difficult and messy.  In all honesty, you're probably better off waiting until Gutsy.  The patch should be a part of the module by then.

If you're feeling adventurous however, you can check out the following link:
[http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/](http://www.cyberciti.biz/faq/appy-patch-file-using-patch-command/)

I've only patched one package in my 1.5 years of linux experience and it was pretty involved.  Basically, you have to save the code from the link i gave in my previous post to a file called 'patch'.  Then the link I gave in this post gives the command to apply the patch.

Just be warned, I haven't tested applying the patch or the patch itself.  Good luck!
Yeah, I can't cut and paste code without getting some form of error message. Thanks.

---

