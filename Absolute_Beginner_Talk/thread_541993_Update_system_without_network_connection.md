---
title: "Update system without network connection"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by chameleon on 2007-09-03
I've done a basic install of Feisty Fawn, but now I want to update my system. Unfortunately my machine isn't connected to a network (I have a wireless network, but can't connect: I'm using a Belkin USB adapter, but of course need to install ndiswrapper - or something - to get it to work). Is it possible to update some other way, such as from a CD?

Many thanks,
Chris

---

### Post by diatribe on 2007-09-03
you could in theory download the new packages to a cd and install them from that

---

### Post by chameleon on 2007-09-03
> **diatribe said:**
> you could in theory download the new packages to a cd and install them from that

Install each one by hand? That would be a nightmare, surely. Or could you use apt-get with a CD? I thought it only worked with Debian CDs...

---

### Post by VON_CAPO on 2007-09-03
Take a look at " APTonCD "
---> Applications/Add-Remove Applications 
:guitar:

---

### Post by chameleon on 2007-09-03
Thanks! :)

---

### Post by Rev_neil on 2007-09-04
Hi, I originally had the same problem on 1st install, no wireless  then i reinstalled with the card attached(Avaya) it  was picked up during installation. then i had screen resolution probs and stuffed everything up in xorg so Reinstalled, this time it wasn't there again.. so by Right clicking on the network icon selecting Enable Wireless network then when i left clicked it brought up that the wired network was connected(and i do't have 1) but as i enabled the wirless it also brought up the  Dlink network and i had to click to enable it, all good now and for some reason it cranks better than the Main PC, im rapt...

all the best

---

### Post by chameleon on 2007-09-04
Cheers. I'm going to try APTonCD and see if I can get everything updated with that - installing the appropriate network drivers is my main concern. I'm using a Belkin USB adapter on my WinXP box, and I'm going to try that with Feisty. I don't think there are any USB adapters which work natively with Linux.

---

### Post by MenZa on 2007-09-04
> **chameleon said:**
> Cheers. I'm going to try APTonCD and see if I can get everything updated with that - installing the appropriate network drivers is my main concern. I'm using a Belkin USB adapter on my WinXP box, and I'm going to try that with Feisty. I don't think there are any USB adapters which work natively with Linux.

Well, if you looked long enough, I think you'd probably be able to find one. Try looking up the name of your card on the ndiswrapper website. :)

---

