---
title: "Installing only Ubuntu?"
date: 2007-05-28
forum: Apple Intel Users
---

### Post by thully on 2007-05-28
Hi,

I've heard a few people running only Ubuntu on their Mac Intel machines.  How exactly did you do your install?  Did you wipe the drive clean?  

Also, I've heard from some that only-Ubuntu machines boot slow - is this always the case?  It seems like keeping the EFI partition and using the normal Feisty installer would allow the system to be installed and used without a slow boot (as there will be a GPT *and* and MBR).  Has anyone tried this?

---

### Post by viciouslime on 2007-05-28
> **thully said:**
> Hi,

I've heard a few people running only Ubuntu on their Mac Intel machines.  How exactly did you do your install?  Did you wipe the drive clean?  

Also, I've heard from some that only-Ubuntu machines boot slow - is this always the case?  It seems like keeping the EFI partition and using the normal Feisty installer would allow the system to be installed and used without a slow boot (as there will be a GPT *and* and MBR).  Has anyone tried this?

I have done this and it works perfectly well. I haven't tried it wiping the EFI partition out though so I can't compare speeds.

---

### Post by DucentiVigintiDuo on 2007-05-28
Wiped the hard drive clean as well and it works just fine.
Boot times are better than OS X, that's for sure. :D

---

### Post by ronocdh on 2007-05-29
> **DucentiVigintiDuo said:**
> Wiped the hard drive clean as well and it works just fine.
Boot times are better than OS X, that's for sure. :D
Do you have numbers? My OS X boot time from a cold system is about 11 seconds to get a login screen. Disabling this login screen means I boot up from cold to an active desktop in about 17 seconds. My Ubuntu boot times, discounting the GRUB times, of course (never did bother to set up ELILO), typically averages around 25-30 seconds till I see a login, then about 5 till I have an active desktop.

*Edit: I should note that right now I'm not using a kernel specially compiled for my machine (Dirk had a sweet how-to a week ago or so). When I was using this kernel, however, it shaved at least 5 seconds off my Ubuntu boot time. Still, it wasn't close to OS X.*

---

### Post by DucentiVigintiDuo on 2007-05-29
I can't time it anymore seeing as I don't have OS X on the machine, but I think both were around 30 seconds for me, only Ubuntu is just a bit faster.

Might be because I have a Macbook and you have a Pro? I don't know.


By the way , I know this is a bit off topic, but I want to ask you, how does Ubuntu sit with the MBP?
I'm seriously thinking of getting one and have it run both OS X and Ubuntu which I think you're doing now so could you tell me your overall experience?

---

