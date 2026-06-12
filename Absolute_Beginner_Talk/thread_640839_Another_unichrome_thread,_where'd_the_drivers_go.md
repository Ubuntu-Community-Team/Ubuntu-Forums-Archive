---
title: "Another unichrome thread, where'd the drivers go?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by ebeard on 2007-12-14
I have tried installing openchrome and via drivers with no luck, still stuck with low res vesa.

Specs;
Graphics, P4M800 pro Unichrome integrated.
Gateway 3228 laptop.
Gutsy Ubuntu

I am stuck with 800x600 vesa graphics (even though this is supposed to be a wide screen laptop).

I have tried openhrome installed through synaptic. Changed device to via and openchrome (tried both) in xorg.conf.

Tried openchrome script found on this forum. [http://ubuntuforums.org/showthread.php?t=485646&highlight=openchrome+script](http://ubuntuforums.org/showthread.php?t=485646&highlight=openchrome+script). 

Tried installing drivers from via. (from a run file it had). It appeared to install correctly.

When I change xorg.conf to device via or openchrome I get a dialog during bootup that says something along the lines of running low resolution, graphics or monitor not detected. I go to configure on this and via or anything close is not a driver option. 

I assume that either there is a hardware detection error (lspci shows P4M800) or the drivers are not available for some reason.

Can anyone suggest a next step? Do I need to remove any drivers (since I tried multiple installs), before trying again. 

This hardware worked at one time (openchrome) in edgy.

Thanks

---

### Post by markmaus on 2007-12-17
ebeard,
I am in a similar situation as you.  I have an Averatec laptop with KM400 Via graphics chipset.  Edgy worked great, but apparently the 3d graphics have been removed from the latest "via" driver.  I've tried installing OpenChrome from Synaptic and also from the tutorial you quoted above, with no success.  I can't even get X to load with the vesa driver any more. I wonder why 3D accelleration was removed from the "via" driver?

---

### Post by Matataki on 2007-12-17
markmaus, I think I had the same problem.

There's something wacky with the via provided files for 3D, so you'll have to recompile them yourself. It's not hard at all though, just follow these directions:

[https://help.ubuntu.com/community/OpenChrome#head-61015b8de079166a76899b391e1dca3f843fa11d](https://help.ubuntu.com/community/OpenChrome#head-61015b8de079166a76899b391e1dca3f843fa11d)

This gets 3D to slightly work for me, but my K8M800 is a troublesome beast that hasn't worked without freezes in anything sophisticated 3D wise since Ubuntu 5.10 or so. 

Best of luck.

---

### Post by markmaus on 2007-12-20
Matataki
Thanks for the link.  I'll have to try that after the holidays.  The instructions look pretty easy.  Whether or not it will work remains to be seen.  It seems like linux is moving backwards with respect to the via/unichrome chipset.

---

### Post by markmaus on 2008-01-06
I tried the directions for compiling the unichrome driver mentioned above.  I couldn't get it to work.  So I found an old Mint Linux disk laying around that is based on Edgy and installed that on my Averatec.  Now everything works just fine.  (Although I don't think that Edgy is still supported in the repositories)  I had also tried Suse 10.3 and Fedora8 and neither of them will install anymore.  I guess that the Linux movement has left my Averatec behind.  The moral of this story is:  Don't buy the VIA chipset if you want Linux compatibility.

---

