---
title: "my screen goes blank"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by nismotime on 2007-07-23
well I installed ubuntu, and wenever I "enable effects" in "desktop effects" the screen goes completely blank, after about 20 seconds it comes back to normal but the effects wont take place, then I installed the "beryl" program and when I open the beryl manager it goes blank in the same way, but it dosent go back after time it stayed blank, so luckily the mouse was still in vew so I guessed at were the quit button was and then I managed to guess were the log off button was, that was pretty scary, anywho, I want to know if there is a way that I can enable desktop effects.

---

### Post by kvonb on 2007-07-23
Need more info:

1. What video card do you have?
2. Which driver did you install for the video, or how did you install it?
3. How much RAM does your video card have?

A simple way of recovering if the screen goes blank is to press ctrl-alt-backspace, that restarts the whole X subsytem :).

---

### Post by nismotime on 2007-07-23
ATI radeon express 200M
I havent installed a driver or anything on ubuntu, I did download every update though.
and im not sure how to check how much ram my video card has, how would I find this out using... lets say windows XP.

---

### Post by kvonb on 2007-07-23
OK, on the main menu, goto System->Administration->Restricted Drivers Manager and run it.

Enable the video driver and let it do it's thing.  You might have to reboot, I'm not sure.  Then try "Desktop Effects" again, see if that works :)

---

### Post by nismotime on 2007-07-23
now my card is in use but when I go to desktop effects it says "the composite extension is not availible" ???

---

### Post by DaCheetah on 2007-12-10
I have the same problem on my laptop with an ATI Radeon Xpress 200M.
I've installed the ATI driver using the Restricted Drivers Manager, everything else seems to work, but turning on Visual Effects results in nothing but a dialog box saying "The Composite extension is not available"
It's a fresh install of 7.10 with almost nothing done other than the updates and installation of restricted drivers.
Any help would be greatly appreciated, obviously.

---

### Post by DaCheetah on 2007-12-10
Ok, seems the driver that the Restricted Drivers Manager installs do not support the composite extension thingy.
Installing xserver-xgl (followed by a logout/login) should fix the problem.

(Solution stolen from [http://ubuntuforums.org/showpost.php?p=3585934&postcount=8](http://ubuntuforums.org/showpost.php?p=3585934&postcount=8) )

Now I have all the pretty Compiz effects, and they don't break video either. (Wobbling video is funny) Everything still seems to work nicely, although the above-linked post says there is a performance drop using this package and when ATI releases better drivers xserver-xgl can be removed.

---

