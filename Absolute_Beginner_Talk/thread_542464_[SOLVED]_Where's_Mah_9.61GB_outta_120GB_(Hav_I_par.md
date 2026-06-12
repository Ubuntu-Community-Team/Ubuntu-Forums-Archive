---
title: "[SOLVED] Where's Mah 9.61GB outta 120GB (Hav I partitioned / Formated correctly?)"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-04
120GB laptop drive divided into:

/dev/sda1 11.18 GB  ext3
/dev/sda2 97.79 GB  ext3
/dev/sda3   1.42 GB  linux-swap

adds up to 110.39 GB

so 110.39 minus 120 = 9.61
---------------------------------

um, where's the 9.61GB hiding?

and whats a good partition tool for ubuntu? I tried QTParted, gives me errors.

(ok, just got me gparted, looks same as QTParted)

I guess I'lll just get the latest Hiren'sBootCD and have a some looking around

Thanks

---

### Post by BLTicklemonster on 2007-09-04
No idea, but I noticed that I was getting extremely full on my last two ubuntu installs and totally dumped one and installed gutsy. I tried making sure everything was totally gone that I had no use for, yet my hard drives stayed full. I haven't messed with my old feisty since I installed gutsy, though, so I'll probably wipe it later and put gutsy on it when it comes out officially.

Good luck finding that extra space!

---

### Post by FuturePilot on 2007-09-04
That sounds about right. The box of the hard drive may say 120GB, but you won't get 120GB out of it since a little bit is used for formatting and such.

---

### Post by MozartlovesUbun2 on 2007-09-04
> **FuturePilot said:**
> That sounds about right. The box of the hard drive may say 120GB, but you won't get 120GB out of it since a little bit is used for formatting and such.

ok, sure i thought about that but still i'm missing almost 10GB ain't that a lot?

little bit should be i'm guessing 2 or 3GB right?

hmm...:confused:

---

### Post by shirilover on 2007-09-04
120 GB in HDD speak = 120 x 10^9 bytes = 111.76 x 2^30 bytes = 111.76 GiB in computer speak.
So, it seems you only lost about 1.4 GiB to file system overhead.

Hard drive manufacturer use the standard SI unit scale(G = 10^9). 
Most computer system information is displayed in binary(Gi = 2^30)

---

### Post by MozartlovesUbun2 on 2007-09-04
> **shirilover said:**
> 120 GB in HDD speak = 120 x 10^9 bytes = 111.76 x 2^30 bytes = 111.76 GiB in computer speak.
So, it seems you only lost about 1.4 GiB to file system overhead.

Hard drive manufacturer use the standard SI unit scale(G = 10^9). 
Most computer system information is displayed in binary(Gi = 2^30)

Ah, ok

thank for the info, but if you say "So, it seems you only lost about 1.4 GiB to file system overhead." what is "system overhead" can I still recover this 1.4 GB and make it usable?

---

### Post by FuturePilot on 2007-09-04
It's the space used for the file system. EXT3 in this case. No, it cannot be made usable since it's already being used by the file system.

---

