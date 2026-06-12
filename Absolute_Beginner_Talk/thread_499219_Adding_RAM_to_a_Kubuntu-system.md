---
title: "Adding RAM to a Kubuntu-system"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by odinb on 2007-07-12
Hi!

Have bought a second stick of 512MB-RAM for a Laptop, giving a total of 1GB.

As far as I understand, the swap-partition is set according to RAM at time of install. Do I need to/can I change that when I double the RAM in the machine?

Sorry for the question, but I am a relative new Linux-user, moving over from the dark side (Windows) to avoid the P-O-S called Vista, and I am used to the swap-size being taken care of by the OS, but as far as I understand, on Kubuntu, the swap is partitioned.

---

### Post by Nekiruhs on 2007-07-12
> **odinb said:**
> Hi!

Have bought a second stick of 512MB-RAM for a Laptop, giving a total of 1GB.

As far as I understand, the swap-partition is set according to RAM at time of install. Do I need to/can I change that when I double the RAM in the machine?

Sorry for the question, but I am a relative new Linux-user, moving over from the dark side (Windows) to avoid the P-O-S called Vista, and I am used to the swap-size being taken care of by the OS, but as far as I understand, on Kubuntu, the swap is partitioned.
You don't need to change it. There is no direct relationship between RAM and Swap. Merely that they both serve a similar purpose. No need to adjust the swap if your adding more RAM.

---

### Post by LaRoza on 2007-07-12
> **odinb said:**
> Hi!

Have bought a second stick of 512MB-RAM for a Laptop, giving a total of 1GB.

As far as I understand, the swap-partition is set according to RAM at time of install. Do I need to/can I change that when I double the RAM in the machine?

Sorry for the question, but I am a relative new Linux-user, moving over from the dark side (Windows) to avoid the P-O-S called Vista, and I am used to the swap-size being taken care of by the OS, but as far as I understand, on Kubuntu, the swap is partitioned.

Install the RAM, if it is dual-channel make sure it is in the right place.

SWAP should stay the same, the recommendation is a myth, whatever you have now is probably more than enough.

---

### Post by deadgobby on 2007-07-12
Your BIOS should pick that up and no changes to be done.
Gobby

---

### Post by odinb on 2007-07-12
> **Nekiruhs said:**
> You don't need to change it. There is no direct relationship between RAM and Swap. Merely that they both serve a similar purpose. No need to adjust the swap if your adding more RAM.

Thanks for all responses!

In regards to this, how is the size of the swap-partition then decided? In other words, if you are partitioning, what factors would decide the size of the swap?

---

### Post by Seisen on 2007-07-12
Its usually 1 1/2 times the amount of ram you have in your computer.

---

### Post by sailor2001 on 2007-07-12
a word of caution A) RAM sticks should be match by mfg so there wouldn't be a conflict B) check with you mobo mfg to see if you can use that much RAM........you maybe already maxed out....

---

### Post by phr0ze on 2007-07-12
Rules of thumb for swap size are just that. You can make your swap as big as you want or small if you want. We give a rule of thumb to make it = to your ram or double your ram just to help new users make an easy decision. None of it is set in stone.

---

### Post by odinb on 2007-07-12
Thanks for the info, so the swap should be good enough as it is then.

Also, from a HW-perspective, I am familiar with how it works with RAM from building computers for the past 20 years or so for myself, family and friends.

I have never seen an instance where different brands of RAM could not work together, under the assumption that the brands are big name quality companies, and the RAM is fulfilling the requirements of the mobo/BIOS. No-name or "new-name" RAM is a different story though...
I have bought Crucial, they have worked flawless so far for me...

* I have made sure the RAM-specs match from the existing stick.
* I have made sure it is 1 stick of 512 in the machine (not 2x256).
* I have made sure the mobo/BIOS can handle 1GB of RAM.

so I do not worry about that part!

I am just new to Linux, that is all!

Microsoft showed me the way in the end by introducing in my opinion a new OS (Vista) which introduced no useful new functions over XP, that needs twice the everything in terms of HW, is extremely bloated for no apparent reason, and still runs slow. The fact that it is spyware-infested by design ([http://tinyurl.com/2ptclh](http://tinyurl.com/2ptclh)), and very annoying to someone that wants to know approximately what is going on "under the hood" is also good reasons for staying away. I felt extremely exposed and crippled using Vista!

This is for a machine bought brand new about a week ago "designed for Vista" that came with Vista basic on. It was extremely slow with its 512megs of RAM, since Vista needs over 700megs just to boot the OS (talk about a big flaw in dimensioning from HP). I could/would not install XP on it, since no drivers are (officially) available for XP for this machine.

Kubuntu is winning on me everyday!!!

---

