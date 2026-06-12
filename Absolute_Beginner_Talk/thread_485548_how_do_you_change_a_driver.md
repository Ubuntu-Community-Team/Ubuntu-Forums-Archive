---
title: "how do you change a driver?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by why? on 2007-06-27
Is there a "device manager" like Windows that I can use to change drivers for hardware?

I think I'm going to have to use ndiswrapper instead of madwifi, which doesn't support my particular Atheros chipset. With PCLinux, I can get my wifi to work with ndiswrapper and a windows driver and it was actually fairly easy.

---

### Post by zanglang on 2007-06-27
I don't think there's an interface like that for generic drivers, but for Ndiswrapper you can try Ndisgtk ;)
> sudo aptitude install ndisgtk

---

### Post by why? on 2007-06-28
rather than focus on the wifi, in general, how do you change drivers for a device?

I think I may be thinking the wrong way about how drivers work in Linux vs Windows and maybe that's the problem I'm having. I know I can install ndiswrapper, but the madwifi still seems to control the device.

It seems theres some basic principle I'm missing.

---

### Post by Seisen on 2007-06-28
If you go to the ndiswrapper website they have a list of all the cards that people have reported that work and what drivers they used.

---

### Post by chandler on 2007-06-28
Umm..  well..  It's not as easy as with windows.  All the drivers are built into the kernel.  So to add or remove a driver you have to take the kernel source, do your stuff then re-compile the kernel for your needs.  The drivers for ndiswrapper nver actually get installed, they just sit in a folder and get accessed like it would on windows.  Hope that helps...

---

### Post by chili555 on 2007-06-28
The key is to *stop* the atheros drivers from loading. Please open a terminal and do:```
lsmod | grep ath
```It will show the atheros drivers that are loaded and that we want to stop. You may find, among others, *ath_pci*, for example. Do:```
sudo rmmod -f ath_pci
```or whatever lsmod found. Then blacklist the module with *gksudo gedit /etc/modprobe.d/blacklist* to add a line:```
blacklist ath_pci
```and/or whatever lsmod found. Then you will be able to use ndisgtk to set up your ndiswrapper driver and atheros will be permanently banned from the castle.

---

### Post by why? on 2007-06-29
> **chandler said:**
> Umm..  well..  It's not as easy as with windows.  All the drivers are built into the kernel.  So to add or remove a driver you have to take the kernel source, do your stuff then re-compile the kernel for your needs.  The drivers for ndiswrapper nver actually get installed, they just sit in a folder and get accessed like it would on windows.  Hope that helps...

ouch, thanks for the answer. Considering I have yet to compile anything with sucess, I bet the kernel will be even more difficult. However, that info will put me on the right path.

Thanks!

---

