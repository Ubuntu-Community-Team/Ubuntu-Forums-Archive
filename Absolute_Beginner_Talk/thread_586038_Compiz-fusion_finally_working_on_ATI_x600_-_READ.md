---
title: "Compiz-fusion finally working on ATI x600 - READ"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by chris.m.ball on 2007-10-21
As an FYI to all, I've spent the majority of yesterday and half of today going down each and every path I've found on the forums and on IRC attempting to get my ATI x600 card working with compiz-fusion.

First off, here's an interesting tidbit:  Using the 7.10 RC Live CD, my system would boot up with compiz-fusion working without touching a single thing.  Likewise, "right" after installing it worked out of the box.  After applying the 94 or so updates waiting for me, then rebooting, my system would come up with no compiz-fusion enabled.  Couldn't enable them from this point onward.

This lead me down the path of installing the restricted drivers to no avail (faced the whitelisted error, or the "composite" error which I tried to brute force in xorg.conf, or the other not so useful error "could not enable desktop effects").  

I also went down the whole road of letting the envy script handle installing the latest and greatest drivers - to no avail.  I also tried installing the xgl server - not only did that completely hose my system (can you say horridly slow graphics with tearing on page scroll?), but upon removing that package, my system was flat out screwed.

I installed a completely fresh copy of my OS to start over again.  After applying all the 94 updates again, same story.  Decided to try typing "compiz" at the terminal.  Noticed it said the following: "Blacklisted PCIID '1002:3150' found".  So I think to myself, am I blacklisted, whitelisted, wtf is going on - my card is fully capable.

SOLUTION (that worked for me at least):
1.  Backed up my /usr/bin/compiz
2.  Edited it and commented out the following line:
"#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700"
3.  Reboot my machine, went to the "Appearance" tool and voila - I was finally able to select whatever level of compiz-fusion I would like.

The unfortunate thing here is that everyone facing these issues will likely go down ALL of the roads I did and burn countless hours in frustration, only to realize they have the correct drivers and this is an issue with one of the patches, particularly with the incorrect blacklisting for compiz.

I hope that this post manages to save some of you the vast amount of energy I have put into this.  Let's all hope that this issue gets fixed ASAP.

---

### Post by JohnSGruber on 2007-10-21
For some recent history on this please see bug report 115283.

To see about a suggestion for an easier way to bypass the blacklist for compiz see:
[https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/115283/comments/51]("https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/115283/comments/51")
in the same bug's thread courtesy Travis Watkins.

It appears that people using the graphics cards in question should be on the lookout for freezes.

---

### Post by chris.m.ball on 2007-10-29
After approximately 1 week solid of using all features of Compiz-fusion enabled, I have had zero freezes on my ATI x600.  This card has been incorrectly blacklisted by my experience, so for those with this card, you might try the notes I placed above if you're interested in getting compiz working.

---

### Post by zeller on 2007-12-02
Is everything still working correctly all these weeks later? Have you had any problems, such as X Window Manager simply crashing on you for no reason?

I'm wondering if I should just search my files and comment out the same line you did. As soon as I enable the restricted ATI driver through Gutsy's Restricted Driver Manager my laptop simply crashes for no apparent reason and X Window Manager is unable to give me back my GUI.

PM me if you'd like. I need all the help I can get.

FYI, too have a x600 card on my HP zd8000 laptop.

---

### Post by zeller on 2007-12-02
That trick seemed to work so far, it's only been about 5 minutes since I commented out that line in /usr/bin/compiz and the laptop hasn't crashed yet.

I'll post again after further testing. Usually it would crash about an hour into normal usage. Nothing remotely taxing on my x600.

Until later...

---

### Post by zeller on 2007-12-03
I've had this working now since my last post with no troubles. Thanks chris.m.ball!

---

### Post by mramsey on 2007-12-03
I will be curious to try this.  The only real trouble I have had with mine has been since 7.10. My pc will not wake after it hibernates and some of my games the graphics are all screwed up (like open arena, nexius etc)

---

### Post by zeller on 2007-12-03
Unfortunately, I was unable to get Nexiuz or Tremulous to work. I figured it may have something to do with the above solution. I don't know. Basically my system just freezes once either game is opened. That is something I can easily deal with though.

---

### Post by zeller on 2008-01-17
Just an update:

Tremulous and Nexiuz as well as other 3D intensive games are working fine now. I just turn Compiz-Fusion off when I want to play and back on when I'm done.

Apparently, for me, that works without problems.

---

