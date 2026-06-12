---
title: "No screen found error during initial bootup and install"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by greywind101 on 2007-05-16
Ok, so I burned a copy of the UBUNTU iso file to a disc and it boots up fine.  It goes through a warmup prodecure where it configures iself, then it gets to a point where it says that ServerX won't run properly because it doesn't detect a video device...even though I can see the text on the screen as plain as day.  Something about no video device found at PCI BUSID 0:2:0 or something.  I have both a default intel vid card, and an ATI one, both with the latest WINDOWS compatible drivers.  I'm starting to wonder if my PC just doesnt' have the stuff to run linux at all.  I tried everything from booting up UBUNTU from a cold boot to looking for appropriate settings in the BIOS, even to enabling/disabling the cards in series through windows.  What am I doing wrong, and if it's not me, is it my hardware that isn't compatible?

---

### Post by icechen1 on 2007-05-16
> **greywind101 said:**
> Ok, so I burned a copy of the UBUNTU iso file to a disc and it boots up fine.  It goes through a warmup prodecure where it configures iself, then it gets to a point where it says that ServerX won't run properly because it doesn't detect a video device...even though I can see the text on the screen as plain as day.  Something about no video device found at PCI BUSID 0:2:0 or something.  I have both a default intel vid card, and an ATI one, both with the latest WINDOWS compatible drivers.  I'm starting to wonder if my PC just doesnt' have the stuff to run linux at all.  I tried everything from booting up UBUNTU from a cold boot to looking for appropriate settings in the BIOS, even to enabling/disabling the cards in series through windows.  What am I doing wrong, and if it's not me, is it my hardware that isn't compatible?

So do you have 2 video card?
If yes,i think removing one will fix it(i recommend remove ATI card because linux don't like it very much)

---

