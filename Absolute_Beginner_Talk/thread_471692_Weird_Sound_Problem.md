---
title: "Weird Sound Problem"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-06-12
Fellow Ubuntuns:

I've had some odd sound problems since updating to Feisty; the sound would come and go, and I could tell at bootup, because the initial bongo sound wouldn't. If I rebooted, then the sound would come back. The problem often followed my system freezing  up from what I traced to a Via 3D driver problem and the screen saver kicking in. 

I have a Soundblaster card in my system. I went through the usual drill: device manager recognizes both the on-board sound chip and the Soundblaster card, as does Alsamixer. But the output seems to flip between the two. Sometimes the output comes from the card, sometimes from the on-board chip. How can I make Feisty choose one or the other once and for all?

Thanks in advance!

---

### Post by muximus on 2007-06-12
open gstreamer-properties and select the output device.. that should solve your problem

---

### Post by Crafty Kisses on 2007-06-12
> **wmichaelb said:**
> Fellow Ubuntuns:

I've had some odd sound problems since updating to Feisty; the sound would come and go, and I could tell at bootup, because the initial bongo sound wouldn't. If I rebooted, then the sound would come back. The problem often followed my system freezing  up from what I traced to a Via 3D driver problem and the screen saver kicking in. 

I have a Soundblaster card in my system. I went through the usual drill: device manager recognizes both the on-board sound chip and the Soundblaster card, as does Alsamixer. But the output seems to flip between the two. Sometimes the output comes from the card, sometimes from the on-board chip. How can I make Feisty choose one or the other once and for all?

Thanks in advance!

Try installing codecs and proper drivers for your sound card, and that should solve your issue.

---

### Post by wmichaelb on 2007-06-14
> **muximus said:**
> open gstreamer-properties and select the output device.. that should solve your problem
Muximus: I selected the via 8237, which is my motherboard chipset, under Device under Multimedia Systems Selector. That made no difference; the system is playing through the sound card as I type this, but played from the motherboard when I booted up yesterday. Am I missing something else?

Thanks!

---

### Post by wmichaelb on 2007-06-14
Codename: I installed the Gstreamer Extra Codecs from Ubuntu Applications Add/Remove before I posted this question. Is there something else I'm missing? 

Thanks!

---

### Post by BobLand on 2007-06-14
Look at your /etc/modules.  You may find your SB driver and most likely the chip driver.  Comment out one of the other so there is only one.  This may or may not help.

I had this problem since I installed U until I found a solution that is, so far, resolving the issue.  I documented the steps in these two threads.  Perhaps they will help or at least give you some ideas to the problem.  Interestingly enough, the resolution didn't have anything to directly do with sound.

[http://ubuntuforums.org/showthread.php?t=441374](http://ubuntuforums.org/showthread.php?t=441374)
[http://ubuntuforums.org/showthread.php?t=457373](http://ubuntuforums.org/showthread.php?t=457373)

bobland

---

### Post by Crafty Kisses on 2007-06-14
> **wmichaelb said:**
> Codename: I installed the Gstreamer Extra Codecs from Ubuntu Applications Add/Remove before I posted this question. Is there something else I'm missing? 

Thanks!

Hmmm, you should try running a sound test. Just a thought.

---

