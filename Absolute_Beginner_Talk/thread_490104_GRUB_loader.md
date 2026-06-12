---
title: "GRUB loader"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Raffaz on 2007-07-02
Can anyone tell me why there are so many options on the GRUB screen? They are:

Ubuntu, kernel 2.6.20-16-lowlatency
Ubuntu, kernel 2.6.20-16-lowlatency (recovery mode)
Ubuntu, kernel 2.6.20-16-generic
Ubuntu, kernel 2.6.20-16-generic (recovery mode)
Ubuntu, kernel 2.6.20-15-lowlatency
Ubuntu, kernel 2.6.20-15-lowlatency (recovery mode)
Ubuntu, kernel 2.6.20-15-generic
Ubuntu, kernel 2.6.20-15-generic (recovery mode)
Ubuntu, memtest86+
Windows Vista/Longhorn (loader)

Im guessing that memtest is to test the RAM like in windows. What's the difference between low latency and generic? Do i need all these, and if not, then how do i get rid of them? Is it just a case of deleting them from the boot file? Cheers.

Mick

---

### Post by cookies on 2007-07-02
It's all the different kernel version you have installed. You may not need low latency, unless you work with, say, MIDI.

---

### Post by Istonian on 2007-07-02
Ya you should just be able to delete them from the boot file. The only one you nned to keep is Ubuntu, kernel 2.6.20-16-generic. That's what worked for me.

---

### Post by Inxsible on 2007-07-02
Deleting them from the menu.lst will not remove them from your system. It will just not show them to you at boot. To remove a kernel, you need to search for that number in the Synaptic and mark for complete removal. 

You can remove the low latency ones for sure. However, always keep atleast one older and stabler version of the kernel , just in case the new one gives problems.

Keep the -16 generic and the -15 generic. and get rid of the low latency ones.

---

### Post by Raffaz on 2007-07-02
Cheers, do i need to keep the recovery ones?

---

### Post by indytim on 2007-07-02
Keep the latest version only for booting into recovery mode (if the situation arises). 

IndyTim

---

