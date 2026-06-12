---
title: "Screensaver stopped working"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by ErlyToo on 2006-09-24
I had to reinstall Ubuntu 6.06 yesterday.  Had 18 software updates, and since I'm on dial-up it took me several hours to update two and three packages at a time.  After updating one of the Linux-restrictive packages {I think that it had the Nvidia legacy in it} my screensaver stopped from Random to blank!!!  My system did not crash and lockup, all that I lost was my screensaver applications.

How do it get them back?  I'm a complete noobie, I can't work in Terminal yet, only in Synaptic.

My PCI card is:

ATI Technologies Inc
Radeon RV200 LX [Mobility FireGL
PCI

Thanks in advance

---

### Post by soaro77 on 2006-09-25
I had this exact same thing happen so I am also interested in the answer. Maybe the answer is to uninstall the Nvidia package???

---

### Post by ErlyToo on 2006-09-25
I've been reading up on this regarding the upgrading of the ATI driver package that Ubuntu offered a few days ago.  Apparently the 3d function was broken for my ATI PCI Card due to this update.  Wow, I can't see the 3d screensaver apps, only the 2d ones now.  Not too much trouble, as everything else is still working on my Thinkpad A31p laptop.  I've also read not to accept the updates offered right away, because problems might crop up like this!!!!  Download the updates only after a few days to see if other people are having problems.

Experienced linux users are correcting the problem using Terminal and scripts, but I'm not an experienced user!!!  So, I'll just have to hang in here and wait for a correction to the update, that is IF Ubuntu will correct the issue.

What video card do you have?

ErlyToo

---

### Post by soaro77 on 2006-09-26
Actually I'm using an Nvidia 6800 GT video card. So it could be an ATI drivers problem for yours but apparently that isn't the only problem causing this. I'll mess around with it some but I have absolutely no idea what I did that cause it to stop working. Like you, I installed a bunch of packages and it suddently stopped working. So something I installed broke it. But I have done too much configuration now to start all over. Hopefully someone can suggest a fix for this. If not I'll just have to do with the 2D screensavers until a fix is made or someday I decide to start all over :-(

---

### Post by ErlyToo on 2006-09-26
Yes, you are right the problem exists in the linux-image and linux-restricted-modules that we downloaded in the updates.  Go to Synaptic and click the Status button then click the installed option on your left side of the screen.  Then go alphabetically to linux- and all of the installed packages are there marked installed.  I'm too cautious to uninstall!!!!  Synaptic does not indicate the day and hour that I downloaded anything.

Also Ubuntu should provide a tool for us to go back before we update anything so that we can recover mistakes like we have.  LOL!!!!

ErlyToo

---

