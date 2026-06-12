---
title: "regionfree decss needed to play DVDs?"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by jrz on 2006-10-13
I've got vlc installed and working using the Synaptic Package manager, and so far it works with CD's, avi, and mp3 but I am hesitant to put in a DVD not wanting to use up the region changes as I have DVDs from nearly every region. Could someone please tell me 1st what I should install to allow the DVD drive to play all regions without changing or using the 5 allowed changes, and 2nd do I need to install a decss program? The DVDs I have are not copies but originals so I'm not sure if decss is needed, but I can see on the labels they are all various regions. If possible, should I need to install anything please advise the simplest method assuming that I have just dismounted from a camel amazed to find there are other humans on the Earth aside from myself. Thank you.

---

### Post by xyz on 2006-10-13
If I understood you right, take a look here:
[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by jrz on 2006-10-13
I read that, and living dangerously I installed regionset, and could not find an icon for it but using the terminal window executed the command, regionset, which returned the following:

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code Settings:
RPC Phase II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

would you like to change the region setting of your drive? [y/n]:

I'm not certain what this is telling me and I would prefer not to ever change the region setting but would like to be able to play any of the DVDs I own which have been purchased in various parts of the world. What should I do now?

Part2.
The part about the libdvdread3 and libdvdcss2 cause me to be careful as I have an AMD Turion 64 X2 CPU in this notebook, but it appears that the Ubuntu version I have pre-installed is the i386 version which I assume is a 32 but version, so I don't know if the AMD64 architecture is applicable or not, and in addition am reluctant to install from the terminal and would prefer to use the Synaptic Package manager if at all possible, assuming this software is necessary. What would you suggest here?

I'll water the camel while awaiting any response. And thanks.

---

### Post by Aberrix on 2006-10-13
I believe the 5 limit region reset is in the DVD drive itself (hardware limit). I don't belive there is any way of getting around this short of installing hacked firmware to the drive.

My best suggestion for a solution to your problem would be to rip the DVD's to your HD and watch them, and/or do that and re-burn them region free. It's a hassle but you can thank wonderful hollywood for their Content Scrambling System (css) and region locks.

Alternatively you should check out afterdawn.com to try and find out more info regards to the brand/model DVD drive you have. You may also find some hacked firmware I spoke of. best of luck.

---

### Post by celeste on 2006-10-13
What I've done (and I suggest you might look into doing) is ripping the disc in windows (with dvd-region-free of course) and burning a copy.  It's not illegal, since it's a personal-use backup copy, but it does allow you to not have to deal with the hassle that is region coding.

---

### Post by jrz on 2006-10-13
Well, I'm not up to trying to copy well over 100 DVD's right now so I guess I'll leave the DVD situation for later and see what else I have to do to get Ubuntu to perform as needed. Making headway, slowly, but surely. Thanks to all who have given assistance.

---

