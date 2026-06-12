---
title: "where's lib/firmware/ea? [installing echo mia from wiki]"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by csl on 2006-08-20
hi chaps - just started with ubuntu and i'm totally new to linux. having some probs.

after getting my display driver and mouse to work properly, next up on the list is my Echo Mia soundcard. Now, I've been following the wiki instructions over at [https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia), but when I get to the part about:

```
You will now need to copy the content of /lib/firmware/ea into /lib/firmware/<your kernel version> i.e:

sudo cp /lib/firmware/ea/* /lib/firmware/2.6.15-26-686/
```

...I hit a problem. I can't find this directory for the life of me, and fear I've missed a fundamental part of the installation process not documented on the wiki.

Does anyone know where I find this /lib/firmware/ea dir? Is it just the 'echo audio' folder inside the lib install files?

Please help - I'd love to get my Mia up and running.

---

### Post by robb. on 2007-07-07
this is a guess, but i think when you download all the ALSA stuff (alsa-drivers, alsa-utils, alsa-lib, and **alsa-firmware**) you will create a folder for alsa-firmware like you did for alsa-drivers, you'll want to copy the files from that /lib/firmware/ea to /usr/lib/firmware.

i could be wrong -- my current efforts are stalled at ./configure...

robb.

---

### Post by pekko on 2007-07-10
If I remember correctly, this step was only needed because alsa version 1.0.12 installed the firmware files to wrong place. So, if you compiled with newer version, this step is not needed. Basically everything you should need to do with clean Feisty install is to compile firmware for Echo Audio cards, search the forum for my earlier post for instructions.

---

### Post by robb. on 2007-07-12
/usr/lib/firmware/ea

i just did this myself, whether i need to or not.  ;)  i now have sound, and i have pekko to thank for the help!  i'm rocking some dizzie gillespie right now, and it sounds great!

robb.

---

### Post by Hendrixski on 2007-07-12
By the way....

WELCOME TO THE COMMUNITY!
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others. 

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too!  Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on these forums.  If dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

### Post by theorganloft on 2007-07-19
> **robb. said:**
> /usr/lib/firmware/ea

i just did this myself, whether i need to or not.  ;)  i now have sound, and i have pekko to thank for the help!  i'm rocking some dizzie gillespie right now, and it sounds great!

robb.

OK. Please tell me how you got the Echo to work? I am stuck.

I have Ubuntu Studio (Feisty) and it cannot see the card.  I know it is good because Windows and Mepis works with it.  

Thanks in advance!!:guitar:

---

