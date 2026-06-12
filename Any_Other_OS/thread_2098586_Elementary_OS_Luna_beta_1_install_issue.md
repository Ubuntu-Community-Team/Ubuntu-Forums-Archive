---
title: "Elementary OS Luna beta 1 install issue"
date: 2012-12-27
forum: Any Other OS
---

### Post by nankura on 2012-12-27
hey guys

i installed Luna OS beta 1, and on boot i get a screen with a bunch of services starting and stopping and it wont boot to the desktop, im unsure whats wrong

This only happens with there kernel 3.2.35 which grub wants to boot to, but when going to "older versions" and using an older kernel, it seems to boot fine. 

but im still unsure how to fix the problem with the kernel they want to default boot to from grub

---

### Post by TedinOz on 2012-12-31
I have a similar problem trying to launch Luna in VirtualBox.
On trying to start and install I get this message...

```
This kernel requires the following features not present on the CPU
pae
Unable to boot - please use a kernel appropriate for your CPU
-
```

My kernel atm is 3.2.0-35-generic-pae

VirtualBox Log File is extensive and pretty much meaningless to me but if anyone can tell me what to look for there or point in the the right direction, would be much appreciated.

---

### Post by orb9220 on 2013-01-01
CPU needs to have pae does yours?

[Google shows the issue]("https://www.google.com/search?q=cpu+with+pae&hl=en&safe=off&output=search&tbs=qdr:y&aq=t") especially with VM.
.

---

### Post by TedinOz on 2013-01-01
> **orb9220 said:**
> CPU needs to have pae does yours?

[Google shows the issue]("https://www.google.com/search?q=cpu+with+pae&hl=en&safe=off&output=search&tbs=qdr:y&aq=t") especially with VM.
.

Thanks for that and thanks for the link. I explained how I have to enable pae within VirtualBox. I'll give that a try and report back.

---

