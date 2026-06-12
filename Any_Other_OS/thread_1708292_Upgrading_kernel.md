---
title: "Upgrading kernel"
date: 2011-03-16
forum: Any Other OS
---

### Post by Rubicon421 on 2011-03-16
Currently running Linux Mint 10 32Bit with the 2.6.35-22-generic-pae kernel on an Intel Core2 Q6600 quad-core. I've heard a lot about the imporovements in the last few kernels and I would like to try out the newest one just released but I'm not sure how.

I currently do not get a GRUB loader menu on boot. I would like to have it set up so that I can choose which kernel to run on boot incase there are any issues with the new one. Could someone please point me in the right direction to install it and configure the GRUB menu? 

Thanks!

---

### Post by andrewthomas on 2011-03-16
Edit your /etc/default/grub file 

changing what you have for the following entries to 

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

and you will get a menu at start

---

### Post by Rubicon421 on 2011-03-16
OK, sounds easy enough. I won't be able to try it until this evening but thanks for the info. 

So after that, how do I go about installing the new kernel? I searched synaptic and it doesn't come up. I know that's because I don't have the source added but I don't know which one to add and what to install from there. There are several packages for each kernel so once I add the right source, I'm sure there are going to be several versions of the 2.6.38.

---

