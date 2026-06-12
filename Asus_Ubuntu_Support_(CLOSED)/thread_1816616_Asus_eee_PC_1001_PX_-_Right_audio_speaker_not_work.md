---
title: "Asus eee PC 1001 PX - Right audio speaker not working properly"
date: 2011-08-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by moskiz.rnr on 2011-08-02
Hello guys!
I installed ubuntu in my netbook a few months ago, and it is really cool and fast. Unfortunately, this morning I encountered a problem while listening to some music, both with Banshee and VLC.
I was listening to some DOORS songs (in these songs, all the instruments are splitted, some come from the left speaker, other ones from the right one) and I noticed that no sound was coming from the right speaker (I also tested it in the speakers test in Audio Preferences --> Hardware). I'm wondering whether this is a hardware problem (eg. my right speaker has broken) or it is a issue experienced by other people too. If there any commands that can help, anything is appreciated (although I'm a new Ubuntu user).
Thanks in advance.

---

### Post by Beacon11 on 2011-08-02
First of all, what version of Ubuntu are you running?

> **moskiz.rnr said:**
> (I also tested it in the speakers test in Audio Preferences --> Hardware).

Do you mean you went to Sound Preferences > Hardware > Test Speakers? And it still only output to the left speaker? If so, I'd lean towards hardware issue. Have you tried booting with a LiveCD and checking if it still happens?

---

### Post by moskiz.rnr on 2011-08-02
I'm running Ubuntu 11.04 and, yeah, I meant Sound Preferences (I translated from the italian). I tried it from a Ubuntu Live CD from USB (11.04), but it did not work anyway. Somebody exprienced the same problem (with notebooks and not netbooks), but they also said that everything worked fine on Windows in dual boot settings. That's why I'm not still completely sure that it is a hardware problem.

---

### Post by ricardofilipemoreira on 2011-09-09
I have the exact same problem, and the same computer as well, the right speaker doesn't work in ubuntu 11.04 (and 11.10 beta). I used 10.10 and at the time I sent my netbook to the store I bought it to get it fixed and by the time it came back I installed ubuntu natty and saw the right speaker wasn't working, but I thought it was broken when getting fixed (ironic, I know). Now I'm thinking it's a bug. I'm going to try with another OS to find out why this happens.

---

### Post by moskiz.rnr on 2011-09-18
A few weeks ago I uninstalled 11.04 and installed 10.04, this time I had issues with headphones. When I listened to music with built-in speakers, it was ok, both the channels worked. Then, as soon as I plugged in the headphones, audio was not working anymore.

I don't want to go back to Windows and I won't (it's too slow on such a little machine) but at least on that OS sound worked out well. I hope Ubuntu developers keep these problems in mind and try to sort them out as soon as possible.

---

### Post by ricardofilipemoreira on 2011-09-18
I don't know for sure but I think Asus Eee PC 1001PX has only one speaker (just to the right side of the touchpad) that plays both channels, but I'm not sure, and I can't open it to see for myself. Maybe that's why Ubuntu can only play one channel now, it doesn't 'emulate' both channels on one speaker right with the kernel (I assume it's a driver issue) used.

---

### Post by moskiz.rnr on 2011-09-22
I don't think it's like this. Or at least, it could also have a single channel, but it should work as if there were two. A few months ago, when I had installed 11.04, everything worked fine. Then, suddenly, after some updates I guess, this problem came out. I really hope the Ubuntu developers try to focus on this issue, with VLC and both channels working properly, a netbook with Ubuntu is really a worthy deal. Apart from watching movies (which is not the best thing with such a little screen, but it can work), any other common thing can be done, and listening to music, in my opinion, is one of the best thing one can do on a computer  :guitar:

---

### Post by ricardofilipemoreira on 2011-09-22
i don't know. when i got my eeepc back from asus, 11.04 had already been released for some time and i installed, i thought it was a hardware problem. now i installed win8 to test it and the speaker works. when oneiric comes out i'll install it again and then file a bug in launchpad

---

### Post by moskiz.rnr on 2011-10-05
Suddenly, everything's fixed and my sound works. I have not updated anything, the issue solved itself or something like that. Finally I'm able to listen to The Doors and many other groups as they deserve.
Hope something like this happens to you as soon as possible. I don't think I'll update Ubuntu to 11.10, or at least, not as soon as it comes out. Maybe I'll wait the next LTS release, which should be in April.

---

### Post by ricardofilipemoreira on 2011-10-05
I already have upgraded and apart from a few bugs, I believe that it's going to be an excellent release :) haven't tested the sound yet, will do tomorrow

---

### Post by moskiz.rnr on 2011-10-06
It WORKED. Today my pc has gone back to the sound issue.

Ubuntu's so weird some times :/

---

### Post by ankkit on 2012-07-16
> **moskiz.rnr said:**
> Hello guys!
I installed ubuntu in my netbook a few months ago, and it is really cool and fast. Unfortunately, this morning I encountered a problem while listening to some music, both with Banshee and VLC.
I was listening to some DOORS songs (in these songs, all the instruments are splitted, some come from the left speaker, other ones from the right one) and I noticed that no sound was coming from the right speaker (I also tested it in the speakers test in Audio Preferences --> Hardware). I'm wondering whether this is a hardware problem (eg. my right speaker has broken) or it is a issue experienced by other people too. If there any commands that can help, anything is appreciated (although I'm a new Ubuntu user).
Thanks in advance.
Hi,

I am facing the same problem but in my case the affected inbuilt speaker is left speaker(not working) while right speaker is working and my Laptop is HP g6-1302 tx. 

Please share the steps you followed to overcome the problem. Any suggestions are highly appreciated.

Thanks 

Ankit

---

### Post by ricardofilipemoreira on 2012-07-16
ankkit in my case this was solved by installling upgrades. maybe it's a bug and it'll be fixed in a later version. maybe you should file a bug in launchpad.

---

