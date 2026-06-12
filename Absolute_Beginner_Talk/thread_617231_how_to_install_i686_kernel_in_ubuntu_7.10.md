---
title: "how to install i686 kernel in ubuntu 7.10?"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-11-19
i have heard a little bit of talk about a kernel upgrade via synaptic that will allow pentium 2 and above cpu's to really fly.

can anyone shed any light on the topic?

---

### Post by Arthur Archnix on 2007-11-20
Ubuntu used to have different kernel versions, but now they're all combined into one. The default kernel works very well on PII+, SMP, and many other setups. Some distributions, like Arch for example, release what they call a 686optimized kernel, which may offer some performance benefit. But, last I read about this the Ubuntu kernel team had decided that supported different kernels in ubuntu required too much time for too little gain. I think it was around the time of 7.04 that the switch happened to just one kernel, though hopefully someone will correct me if I'm wrong. 

In any event, you can be sure that Ubuntu is using your hardware to the maximum extent possible and you're not missing out on any features that 686 optimized kernels offer. The only difference would be a small to moderate performance increase.

EDIT: I suppose you may be asking about the rt-kernel? Aka Real time kernel. I'm afraid I can't tell you much about it, other than not to install it without learning more and having a good reason for doing so. My understanding is that it only helps in some cases with some applications. E.g., audio and video editing. Regular computer users may find it introduces more problems than benefits. This is all just as far as I understand, so don't make any decisions based on this post alone.

---

### Post by stinger30au on 2007-11-21
thank you for the info

---

