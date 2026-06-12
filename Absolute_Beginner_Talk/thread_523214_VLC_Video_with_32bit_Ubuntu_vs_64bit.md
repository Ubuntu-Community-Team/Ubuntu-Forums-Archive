---
title: "VLC Video with 32bit Ubuntu vs 64bit"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by pylorns on 2007-08-11
Ok I pulled down a 10gig version of Serenity - its encoded as an mkv file in .264 format? Anyway it is from an HDDVD or Blueray etc.  Its also 1080p resolution. So, I played it first on my windows box which is a p4 3.4GhZ with 2GB ram, Sata drives etc - it jerks and the audio is not in sync with the video.   I looked at the processor and it was tapped out. 

I then puled down VLC player for Ubuntu and the associated codecs and tried on my Ubuntu machine which is a AMD 3800 (Dual Core 54bit) processor.  I watched the performance at the same time I tried to play it - and the same thing the system choked and jerked and the processor was tapped out - but the other core was not even being used. So VLC wasn't really taking full advantage of the dual core processor.  My question is - if I installed the 64bit version of Ubuntu (current stable build) do you think that it would make use of that other processor core and actually play the video smooth?

Thanks,
pylorns

---

### Post by starcraft.man on 2007-08-11
First right off the bat, I don't think it's wise to admit to movie piracy on a public forum, ever. As for the question, fraid I don't know about multicore usage in VLC. It isn't dependant on 64 bit usage, you can use multiple cores in 32 bit. It really has to be a feature of the program, if it isn't in options/native then your out of luck.

---

### Post by pylorns on 2007-08-11
Did I say it was "pirated"? oh no, this was a personal copy that was encoded by me :).  So basically what you're saying is that VLC player just doenst make use of the multicores.

---

### Post by starcraft.man on 2007-08-11
> **pylorns said:**
> Did I say it was "pirated"? oh no, this was a personal copy that was encoded by me :). 

Semantics. Even that would be a violation of the DMCA. And it's best not discussed on forums in any case, it's just not information we need to know if you choose to do that. Oh and you said pulled down...

>  So basically what you're saying is that VLC player just doenst make use of the multicores.

Curious, I just checked the CPU options. It specifies it has instructions set for SSE and SSE2 but not SSE3 which is for most CPUs today. I'm not sure why. Maybe it is just limited today, I wonder when next release will come out maybe it will be aimed at dual/quad cores. My answer is really that I don't know (I'm not a VLC expert). However, in either case I'd say you need a better CPU (on either machine) to drive a whole HD movie at full 1080p, that is a seriously intensive task.

---

### Post by pylorns on 2007-08-11
Yeah i've been looking at the options as well, nothing that seems to handle it - I did a search on google and found Cool DVD player - which handles dual core decoding but its only for windows.    Legitimately though, the AMD 3800 while a slower core speed on each core, if the cores are not being fully utilized then it should be able to handle decoding 1080p - if there is software out there to handle it.  As I have not seen anything out there yet after looking for the past 15 minutes that seems to work for linux - and of course the faster processor is on my linux box and not my windows box (dont ask why)...

---

### Post by pylorns on 2007-08-11
fyi, I just tried CoolDVD player for windows - it utilizes the hyperthreading portion of a p4 that I have and it does play the video better.  The software claims to be the first fully functional DVD/HDDVD player that supports dual core processors. I suspect that had I XP or Vista on my Linux box this player would be able to fully play the video.

---

### Post by starcraft.man on 2007-08-11
> **pylorns said:**
> fyi, I just tried CoolDVD player for windows - it utilizes the hyperthreading portion of a p4 that I have and it does play the video better.  The software claims to be the first fully functional DVD/HDDVD player that supports dual core processors. I suspect that had I XP or Vista on my Linux box this player would be able to fully play the video.

*shrug* Maybe time to upgrade your p4 box to a new core 2 duo machine? It's not bad right now to buy a decent system that'd run Linux or Vista/XP. I just stick to plain DVDs, I'm not into the whole HD thing especially when I'm more interested in stories anyway.

---

