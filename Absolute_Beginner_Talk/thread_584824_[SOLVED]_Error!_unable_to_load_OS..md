---
title: "[SOLVED] Error! unable to load OS."
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by bumanie on 2007-10-21
Had a dual boot xp and feisty. Today I installed a new hard drive (slave) and tried to install Gutsy on it. Everything seemed to be going OK until  it came to rebooting at the end of the install. I then got the above message, Error! unable to load OS.
Before installing gutsy on the the new hard drive I wondered whether having two ubuntu's on different drives would be a problem with two GRUB's operating. (This being the problem is only a guess on my part).
Does anyone more knowledgable have any idea whether this would be the problem? Unfortunately with full time work and part time study, I probably will not be able to look into this any furhter until about Thursday (that is unless someone can suggest an easy fix). In the meantime, I may unplug the slave drive and hope the master works as it did previously. 
Any suggestions would be appreciated. Thanks in advance.

---

### Post by mikeyphi on 2007-10-21
1. What if you change your BIOS first boot option?

2. What options do you see on the Grub screen?

3. If no Grub page - use the LiveCD to check/install Grub

I have 3 versions of Ubuntu on 3 different drives - no probs. There should only be one 'master' instance of Grub - unless other OSs are disconnected during the install. What normally happens is that the Main Boot sector points to the Grub menu on the newest Ubuntu install. In your case the system will look to boot from the master disk and should then produce the Grub page from the slave disk which in turn should let you boot into either disk.

If you can't boot into Gutsy try to boot into Feisty and get to the /boot/grub/menu.lst on Gutsy - see what it says.

---

### Post by bumanie on 2007-10-21
> **bumanie said:**
> Had a dual boot xp and feisty. Today I installed a new hard drive (slave) and tried to install Gutsy on it. Everything seemed to be going OK until  it came to rebooting at the end of the install. I then got the above message, Error! unable to load OS.
Before installing gutsy on the the new hard drive I wondered whether having two ubuntu's on different drives would be a problem with two GRUB's operating. (This being the problem is only a guess on my part).
Does anyone more knowledgable have any idea whether this would be the problem? Unfortunately with full time work and part time study, I probably will not be able to look into this any furhter until about Thursday (that is unless someone can suggest an easy fix). In the meantime, I may unplug the slave drive and hope the master works as it did previously. 
Any suggestions would be appreciated. Thanks in advance.

> **mikeyphi said:**
> 1. What if you change your BIOS first boot option?

2. What options do you see on the Grub screen?

3. If no Grub page - use the LiveCD to check/install Grub

I have 3 versions of Ubuntu on 3 different drives - no probs. There should only be one 'master' instance of Grub - unless other OSs are disconnected during the install. What normally happens is that the Main Boot sector points to the Grub menu on the newest Ubuntu install. In your case the system will look to boot from the master disk and should then produce the Grub page from the slave disk which in turn should let you boot into either disk.

If you can't boot into Gutsy try to boot into Feisty and get to the /boot/grub/menu.lst on Gutsy - see what it says.

Thanks Mikeyphi for the answer. Unfortuanately there is no GRUB menu page, it doesn't get that far before coming up with the error. I twon't boot into any of the three OS's on the computer. My BIOS is set to boot from cd - this configuration has never been a problem in the past. In fact where the error comes in is immediately after the start up screen says 'Boot from CD'. Normally the next screen is the GRUB screen, but the above message appears instead. 
If I use the live cd to look at the GRUB menu, what exactly should I be looking for and how does one change things? Although I have been using ubuntu for a few months, I have not had to do this before and have no idea what I am looking for.

---

### Post by bumanie on 2007-10-21
Managed to have a quick look at my computer. I now believe it is a grub error that is preventing me from booting. I will try super grub disc later, unless anyone has a better idea. Seem to have a grub 21 error, which is not that uncommon, I think. I had a quick look via live cd and everything is still in one piece on the master drive. Did not have time to look at the slave, but aren't too concerned about it as I can always do a fresh install on that drive if necessary.

---

### Post by bumanie on 2007-10-23
Fixed GRUB with super grub disc. Downloaded same onto external drive, booted up live cd and burnt super grub disc onto cd. Also deleted partitions from slave drive reformatted with gparted. Will try to reload gutsy onto slave soon.

---

