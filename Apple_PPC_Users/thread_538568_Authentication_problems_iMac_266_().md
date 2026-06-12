---
title: "Authentication problems iMac 266 (??)"
date: 2007-08-30
forum: Apple PPC Users
---

### Post by PJW on 2007-08-30
I tried to install/boot the live cd Ubuntu 7.04 on an old Imac G3 266 (with 256 mb ram and a new harddrive with OS X on it) but after booting I´m asked to change my Username and Password! What password? The booting stopped and I got a black screen with the text:

Authentication token is no longer valid: new one regquired.
You are required to change your password immediately (root enforced)

Don´t get it...

PS. I tried to do the same with Ubuntu 6 (dapper?) but the result was the same. DS

PPS. Sorry for my bad English. I´m Swedish...:-) DDS

---

### Post by linear on 2007-08-30
Sounds like a date/time problem - see [this thread]("http://ubuntuforums.org/showthread.php?t=438274").

---

### Post by PJW on 2007-08-31
Thanks! That was the problem. I ran the live cd without any problems. then I installed the OS and  it won´t boot. It says "Please wait, loading kernel..." I´ve been waiting for 45 minutes now...

Any suggestions?

PS. Thanks again! Great forum btw! DS.

---

### Post by curly_nostrill on 2007-08-31
[Could be time to try this?]("http://imacquarium.cool-mac.com/monster.html") ;-D

---

### Post by PJW on 2007-08-31
Been there, done that...:) No, really, I tried to build one for a long time ago with an old imac dv, but the result was far from good (an understatement...).

With my old imac 266 I just wanted to try Ubuntu (I really like the idea and the concept). I have as well tried to launch the live-cd on my eMac (700 MHz) and an iMac G5 but I just can´t get it to work! But thats a different thread.

So: why won´t the kernel load?:(

---

### Post by curly_nostrill on 2007-08-31
ha, well then a little more seriously ... why don't you try Xubuntu Dapper PPC[http://xubuntu.org/get#dapper]("http://xubuntu.org/get#dapper") to just see if it will load?  I have a feeling the normal Ubuntu won't run very well on those specs and I even have doubts about Xubuntu but that's the lightest flavor available.  If it works you might even try to use fluxbox as the window manager.

Releases Edgy and up seem to be newer mac centric.  I finally managed to get xubuntu feisty working on my ibook 2usb 256mb after mucho headacheios but the Dapper dist loads right up with no real problems... specifically NO video problems.

Make sure to get the "power pc" image.

NetBSD also has pretty well made ppc ports but not quite as easy as (x)Ubuntu.  Pretty dang cool though depending on what you need.

---

