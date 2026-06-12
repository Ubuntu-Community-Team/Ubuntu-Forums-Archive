---
title: "i have problem to open synaptic"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by thungmail on 2008-03-17
I tried to open synaptic manager but I got the message :
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Even though, when i tried in terminal to get update the message was:
tuan@tuan:~$  sudo apt-get update
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
tuan@tuan:~$ 

can somebody help me out

---

### Post by PeterJS on 2008-03-17
You installed medibuntu from an old set of directions and the repository indicated in those directions no longer exists, so when you created the /etc/apt/sources.list.d/medibuntu file it got filled with garbage data (well it's actually a vaild HTML meta redirect, but it's garbage as far as apt is concerned). You should remove /etc/apt/source.list.d/medibuntu, and reset up medibuntu using thse instructions instead:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Oldsoldier2003 on 2008-03-17
> **thungmail said:**
> I tried to open synaptic manager but I got the message :
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Even though, when i tried in terminal to get update the message was:
tuan@tuan:~$  sudo apt-get update
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
tuan@tuan:~$ 

can somebody help me out



edit: NVM PeterJS is on the job :)

---

