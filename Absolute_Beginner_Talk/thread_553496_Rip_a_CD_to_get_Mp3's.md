---
title: "Rip a CD to get Mp3's"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2007-09-17
Hello,

Does anyone know of a good app for Ubuntu that can rip a CD and get Mp3 files of the tracks?

---

### Post by SOULRiDER on 2007-09-17
Have you tried soundjuicier?

---

### Post by SOULRiDER on 2007-09-17
Check out this Wiki entry:
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

---

### Post by rsambuca on 2007-09-17
I also use Sound Juicer.

---

### Post by aysiu on 2007-09-17
First, enable MP3 support:
1. Go to Applications > Add/ Remove
2. In the upper-right-hand corner, select to show all available applications
3. Search for the phrase *mp3*
4. Install the "ugly" multiverse metapackage

Second, rip the CD:
1. Insert your CD
2. Sound Juicer should automatically open. If not, go to Applications > Sound and Video > Sound-Juicer
3. In the preferences, select the MP3 profile from the drop-down menu
4. Select to extract all tracks

---

### Post by Odd-rationale on 2007-09-17
I use *Sound Juicer CD extractor*. It is built-in with the Ubuntu installation. If not, go to the Add/remove applications and install it from there.

After you install it, go to the Sound Juicer help menu to find out how to rip to mp3's. (You will need gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse.) The help guide will give you detailed 

See also,
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

---

