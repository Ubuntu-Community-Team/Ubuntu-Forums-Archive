---
title: "I have lost sound"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by shanka on 2007-02-11
Hey guys.. I installed ubuntu edgy  a few months ago and was working fine till yesterday. 
then I suddenly I can't get the audio form my system; not even the audio that plays during the splash screen during the bootup. 
Is the audio driver corrupted?
Pls help!

---

### Post by kno on 2007-02-12
Hi,
I've got the same problem :-k

---

### Post by ricardisimo on 2007-02-12
Similar problems here. Got some great advice [in my thread]("http://www.ubuntuforums.org/showthread.php?t=323110"), although I'm still largely without sound. Hope it can help you more than me. ;-)

---

### Post by NiksaVel on 2007-02-12
same thing happened to me yesterday....   somebody help :)

---

### Post by NiksaVel on 2007-02-12
I have also resolved the issue...

I had to start alsamixer and turn on PCM  (press M) the sound came immediatelly back online.

---

### Post by kno on 2007-02-12
> **NiksaVel said:**
> I have also resolved the issue...

I had to start alsamixer and turn on PCM  (press M) the sound came immediatelly back online.


Thanks (I've increased the *IEC958 Playback AC97-SPSA* volume)

---

### Post by Blaster95 on 2007-02-12
i'm also having an issue on my laptop with sound. It works fine untill it hibernates then after that i seem to be having problems. I'm not too sure what it is though. I have to restart my computer each time now. After it restarts it all seems to be working though. I'm thinking it might be a problem with a recent update or something because it used to work fine with me. But now all of a sudan it doesn't for some reason.

---

### Post by NiksaVel on 2007-02-12
I also have major problems with both suspend and hibernate on my laptop...

for some reason when returning from suspend my network dies..  and i have to reboot.

and hibernate never really worked in edgy for some reason...  it starts shutting down and than just returns to the desktop...  I think I cought a glimpse of an error message about insufficient swap space, but I am not sure... :/

---

### Post by nickoli_02 on 2007-02-12
To the best of my knowledge, when you put your computer in hybernate it transfers everything that is in RAM + what is already in SWAP to the swap space. If you don't have enough swap, then that's probably why you can't hybernate.

---

### Post by nickoli_02 on 2007-02-12
As for suspend killing your network... you using a wired or wireless network? Ubuntu is probably turning off your network interface to conserve power. You don't really have to do a complete restart, try telling the interface to wake up. For example, for interface eth0:

```
ifup eth0
```

You may need to run this with sudo, not sure.

---

### Post by arkangel on 2007-02-12
If you lost the sound  , was because of ....

did any of you update the kernel or any module  or something ?

---

### Post by shanka on 2007-02-14
> **arkangel said:**
> If you lost the sound  , was because of ....

did any of you update the kernel or any module  or something ?


Yeah I did an update of the kernal module.

**Edit**:
It's working now!!
The speakers were burnt due to a voltage spike. I did'nt realise this in the first place because the light from the speaker where still there. (I connect the speaker to direct AC while the CPU, moniter and modem go to UPS). 
I tested using my headphones, the audio was fine. 


Cheers!

---

### Post by nickoli_02 on 2007-02-14
ouch... that sucks. Hope they weren't too expensive.

---

