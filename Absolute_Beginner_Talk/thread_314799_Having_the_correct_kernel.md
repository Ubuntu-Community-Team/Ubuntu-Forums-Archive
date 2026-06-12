---
title: "Having the correct kernel?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-12-08
I have an AMD Turion 1.6GHz.

uname -r:
```
2.6.15-27-386
```

Do I have the right kernel?

---

### Post by Sef on 2006-12-08
That is the kernel for Dapper.  Are you running Dapper?

---

### Post by anti_microsoft on 2006-12-08
Depends if your 64bit or not (distro)?

---

### Post by PartisanEntity on 2006-12-08
> **Sef said:**
> That is the kernel for Dapper.  Are you running Dapper?

Yes I am running Dapper, so all is well?

---

### Post by PartisanEntity on 2006-12-08
> **anti_microsoft said:**
> Depends if your 64bit or not (distro)?

My processor is capable of 64bit but I have not bothered with that.

---

### Post by Sef on 2006-12-08
> Yes I am running Dapper, so all is well?

Yes, all is well.

---

### Post by PartisanEntity on 2006-12-08
Thanks!

---

### Post by PartisanEntity on 2006-12-11
Hello again, new question:

What would be the correct kernel for Dapper running on an Acer Aspire with a Turion X2 (dual core) ?.

Thanks again.

---

### Post by zgornel on 2006-12-11
> **PartisanEntity said:**
> Hello again, new question:

What would be the correct kernel for Dapper running on an Acer Aspire with a Turion X2 (dual core) ?.

Thanks again.

The k7-smp kernel.

---

### Post by PartisanEntity on 2006-12-11
Thank you, now one last silly question, how would I go about installing that kernel?

---

### Post by zgornel on 2006-12-11
I don't remeber the exact name of the package, go into synaptic and search "linux image k7" or "kernel k7". It should find it :D .

---

### Post by mcduck on 2006-12-11
> **PartisanEntity said:**
> Thank you, now one last silly question, how would I go about installing that kernel?

'sudo apt-get install linux-k7-smp' and a reboot.

The new kernel now appears in Grub menu, and after you have used it for a while you can just remove all 386-kernel packages with synaptic.

---

### Post by PartisanEntity on 2006-12-12
Did I understand it correctly, the the linux-k7-smp kernel is for AMD dual cores?

What about an AMD Turion, what would be the correct kernel for that? (I am not sure I was given the correct info at the start of this thread).

---

### Post by tudawggz on 2006-12-12
The correct Kernel depends on what you want to do.  You can run a 64 bit kernel, but there are a few things that you would have to work around, such as flash player and other codecs.  But I would say use a K7 kernel if possible, others will work fine, but these should be optimized for amd chipsets.  You can always look in the repositories for the latest possible kernel avaliblity.

---

### Post by PartisanEntity on 2006-12-12
Can I use any k7 kernel for the Turion?

---

### Post by tudawggz on 2006-12-12
yes, but watch the numbers, the higher ie 2.6.16-27 would be more up to date then 2.6.16-25.

---

### Post by mcduck on 2006-12-12
> **tudawggz said:**
> yes, but watch the numbers, the higher ie 2.6.16-27 would be more up to date then 2.6.16-25.
no, don't care about the numbers and *don't install specific kernel versions*!

Instead, install the metapackage for the kernel you want to use, 'linux-686', 'linux-k7-smp', 'linux-generic' or whatever you your CPU. These packages always depends on the latest kernel version, kernel headers and restricted modules so installing kernel this way will make sure that you'll get updates for your kernel and all related files.

The most common reason for people's graphics card drivers and such breaking with updates is that they don't have this metapackage installed..

---

### Post by PartisanEntity on 2006-12-12
@ mcduck: please let me know if I have installed the kernel correctly:

Basically I used synaptic package manager and installed linux-image-k7, this then edded several other file and packages.

Was this the correct way?

---

### Post by mcduck on 2006-12-12
> **PartisanEntity said:**
> @ mcduck: please let me know if I have installed the kernel correctly:

Basically I used synaptic package manager and installed linux-image-k7, this then edded several other file and packages.

Was this the correct way?
that gives you the kernel but no headers or restricted modules..

It might be OK if you don't need those but I'd recommend getting the linux-k7 package, so you don't need to think about if you need them or not. Anyway, they hardly take any disk space at all and it's easier that way.

---

### Post by PartisanEntity on 2006-12-27
[QUOTE=mcduck]that gives you the kernel but no headers or restricted modules[/QUOTE]

Sorry haven't replied in a while, forgot about this thread:

Whats the name of the metapackage for the AMD Turion (_non dual core_) kernel in Synaptics?

---

