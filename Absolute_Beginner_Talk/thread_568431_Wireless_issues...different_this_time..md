---
title: "Wireless issues...different this time."
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by pilot_guy415 on 2007-10-05
Well, I finally gave up and installed 7.10 beta...now my wireless card works...but I still cant connect to the net! It detects my network...I enter in the password...I have tried all the different encryption protocals and NOTHING WORKS! any advice?

---

### Post by wormser on 2007-10-05
Try connecting first with out any encryption.  I had a issue like this when first setting up my wireless.  It was resolved with a reboot (probably won't help but worth a shot).

---

### Post by pilot_guy415 on 2007-10-06
Ok, that didnt work...I will try to give as much info as possible.

First of all its run off a linksys router (dont remember the exact model). The encryption method (according to my step dad who set up the encryption) is WEP something or other. The code is all numbers so I figured hexidecimal right? Well the code is two short of the 26 required for the code so I put 2 0s at the end...Im totally at a loss...its so fustrating to FINALLY get my card working after weeks of messing with it and now I cant connect to me own network :\:mad:

---

### Post by shifty_powers on 2007-10-06
have you ever thought of using ndiswrapper? it is a utility that lets you use the windows drivers for your card. (Doesn't support EVERY card but does pretty well). Helped me out on more than one occasion ;)

---

### Post by pilot_guy415 on 2007-10-06
I will try that tool but I dont think its my drivers...my wireless card is working and detecting my network...it just wont connect...anyway...anything is worth a shot

---

### Post by usmanlinux on 2007-10-06
i have the same issue, i got my card working finally its an internal wireless nic, and now i can see everything, but cant seem to pull the IP.

---

### Post by pilot_guy415 on 2007-10-06
bump bump bump it up

---

### Post by pilot_guy415 on 2007-10-07
ANY more clues...I appreciate all the help I have recieved so far....the one thing I have found with linux I dont like is that I cant bitch out anyone when things arent working right! lol

---

### Post by shifty_powers on 2007-10-07
Well what happened with ndiswrapper? And as for the kernel drivers, when i was on 7.04, (7.10 beta now), then i found that the drivers would apparently work and recognise the network but not connect, the exact same problem you've got. Solved it by using ndiswrapper.

However, i since i installed 7.10, the kernel drivers work perfectly, without any need for ndis. So maybe the problem will be solved for you on the 18th ;)

---

