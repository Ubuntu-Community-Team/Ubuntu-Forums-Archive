---
title: "Flash Sound Slowdown"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by hl2gamer on 2006-10-07
I did do a search, and although there are plenty of threads about problems with flash I couldnt find one with my specific problem.

Problem: When I run a flash video (such as a YouTube video) it plays fine and I can hear sound but the sound un-sincs with the video after like 20sec.  How do I fix?

Thanks

---

### Post by ayllu on 2006-10-10
Hi... i have the same problen wiht my flash firefox plugin i can not hear any sound,  tell me please when you resolved the the problem.

---

### Post by CarpKing on 2006-10-10
I think the no sound problem can usually be solved, but I never had it so I don't know how.  The syncing problem with Youtube, though, is trickier, and I have yet to solve it.  I have heard that it is mostly due to the fact that the highest version of Flash player for Linux is 7, and that version has a lot of problems.  Try this (didn't work for me): [http://www.ubuntuforums.org/showthread.php?t=75237](http://www.ubuntuforums.org/showthread.php?t=75237)

Otherwise, take comfort in the fact that Flash 9 will be out for Linux soon; I think I've heard they plan to release a beta late this fall.  In the meantime, you could install the Windows version of Firefox and its Flash plugin through WINE and use it when you want to go to sites such as Youtube.

---

### Post by Nangineer on 2006-10-10
Here's how I fixed it. Open a terminal and enter

sudo aptitude install alsa-oss

then

sudo gedit /etc/firefox/firefoxrc

then change FIREFOX_DSP="none"
to FIREFOX_DSP=aoss"

This fixes the sync problem but may cause Firefox to crash while trying to open up a site that uses Flash. (That problem occurs less if at all with newer versions of ALSA than the version in Dapper.)

---

