---
title: "Cannot get past loading screen with ATI Card"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by rgraves22 on 2007-06-05
Have an ATI Radeon 9250 PCI 256MB card that I would like to use.. downloaded the generic driver for it and cannot get past the loading screen when ubuntu loads. 

Followed this link [http://ubuntuforums.org/showpost.php?p=2353434&postcount=18](http://ubuntuforums.org/showpost.php?p=2353434&postcount=18)

still to no avail.. luckily, I did backup my xorg.conf

And I will display my xorg.conf when I switch the graphics card back to onboard in the bios...

---

### Post by rgraves22 on 2007-06-05
Or an nVidia card.. FX5500+

thoughts?

---

### Post by theorem_hunter on 2007-06-06
have you tried booting in safe mode? are you using a 32bit or 64bit version?

---

### Post by rgraves22 on 2007-06-06
Both safe mode and regular crash..  With both cards. 

32 bit Ubuntu 7.04

Dell Gx260 
1GB Ram
nVIdia FX5500 128MB card, its a PCI card, on an AGP expansion card. ( possibly my issue ). 

Its an old dell desktop we had laying around..

when I do an lspci, it lists the card at 1:07.1 but xorg dosnt like the .1 on the end..

---

### Post by rgraves22 on 2007-06-06
It crashes off of the live CD as well.. I have to use the onboard video, which is an intel chipset with 64MB of video RAM.

---

