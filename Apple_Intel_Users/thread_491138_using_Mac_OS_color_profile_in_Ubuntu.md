---
title: "using Mac OS color profile in Ubuntu"
date: 2007-07-03
forum: Apple Intel Users
---

### Post by anujseth on 2007-07-03
Alright ... I dont know if there is another post detailing this but I'm so excited with the results  I decided to
post this anyway. Most of you using Mac OS and Ubuntu  must have noticed the color being out of sync
etc. an excellent way to test this is facebook.com, the blue just looks horrible. 

well here's how you fix everything. before we begin as a side note you can tinker with xgamma to set these
values manually but to be honest it just doesnt seem to click. Kubuntu users can use a GUI based gamma 
calibrator in there System Settings. this again is difficult to do.

Alright the fix. Boot Mac OS X, System Preferences -> Display -> Color. the gentoo MacBook wiki tells you
to select the expert option so that you can set up more in detail. this again gives you gamma calibration colors
etc. I suggest let the expert mode be unchecked select the 1.8 standard Mac Color profile. Save it give it a name.

Boot Ubuntu. Get xcalib here->
[http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/]("http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/")

The latest 0.7 version doesnt seem to compile for some reason, so i just got the ready binary for 0.6.
 You then need to mount your mac os partition. the easiest way to that is add the Disk Mounter applet to
your panel or ofcourse you can use mount. then you need to enter something like this. basically you need 
to run xcalib with the mac os saved .icc profile and it picks up the settings. 

```
sudo ./xcalib /media/Anuj\ Seth\ Mac\ HD/Users/anujseth/Library/ColorSync/Profiles/Color\ LCD\ Calibrated.icc

```

and ... bravo ... everything is beautiful again. this does not persist across boots you might want to add
it to a script or something.

---

### Post by thully on 2007-07-12
This is really cool.  I had wondered in the past why Ubuntu's colors in VMware Fusion looked better than in a native boot, and now I know why.  I just copied over my MacBook's default profile, downloaded the binary, stuck it in /usr/local/bin, and ran it.  I figure there's an X startup script I can put this in now...

---

### Post by thully on 2007-07-12
Instructions are now posted on the Ubuntu MacBook wiki on how to do this.  It looks really good on my MacBook's LCD..

---

### Post by anujseth on 2007-07-13
@thully

yeah it makes such a difference its not even funny ... wonder why no one was talking about it ... anyway sadly im off ubuntu ... the heat is just getting unbearable i havent tried gutsy though is it any better? ... even after compiling in the latest kernel power top fixes it still gets really hot specially the top and middle left part ... any suggestions :(

---

### Post by anujseth on 2007-07-13
ohh and just as a side note you don't need to mount the mac partition everytime ... just once ... make a local copy of the .icc file it works just fine

---

### Post by thully on 2007-07-13
All I can say is try the fan speed settings - that can help a bit.  Also, disable any unnecessary kernel modules (i.e. wireless if you're using wired ethernet) by putting them in /etc/modprobe.d/blacklist
Other than that, I dunno - it's a known issue that Linux power management isn't as good as other OSes.  It is improving with the last few kernel updates, though - Gutsy should definitely be an improvement over feisty.  BTW, I'm actually on Feisty now - may upgrade to Gutsy, though, as it does seem to support my hardware better.  Then again, I may just go back to OS X - I dunno for sure at this point.

---

### Post by anujseth on 2007-07-13
@thully 

i 've done all that already and i use wireless primarily and it does heat up a lot more with the wireless on, infact a lot more ... have to resort to sudo modprode -r ath_pci for now as my wireless switch ... OS X is nice even i keep going back to it ... but it lacks a lot, i mean once you get used to doing everything on the keyboard the linux way clicking icons is a pain and other things in general just dont seem to gel ... atleast for me ... oh how i miss my old dell P3 laptop :(

---

### Post by vh1 on 2007-07-15
I just tried this out, so far everything seems to have a red / orange tint to it

---

### Post by cyberdork33 on 2007-08-22
> **anujseth said:**
> The latest 0.7 version doesnt seem to compile for some reason, so i just got the ready binary for 0.6.

As a follow up, You have to install the dependency first!
```
$ sudo aptitude install libxxf86vm-dev
``` Now the 0.7 version should compile.

---

