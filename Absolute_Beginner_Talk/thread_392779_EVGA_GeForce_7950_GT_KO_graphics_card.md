---
title: "EVGA GeForce 7950 GT KO graphics card?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Butthead on 2007-03-24
Hi,

Total Linux newbee here.  I have a Shuttle SN27P2 barebones rig that I assembled with an Athlon FX2 (dual core) 4600+ CPU in it (excuse me if the chip nomenclature isn't totally right :confused: ) that also has an EVGA GeForce 7950 GT KO (512 MB) graphics card in it that's currently running on Kubuntu Dapper Drake 64 bit Linux.  I'm assuming that I can install one of the NVIDIA 64 bit Linux drivers on this rig (since I think I remember reading somewhere that the EVGA graphics card has NVIDIA (controller?) chips on it).  My question is is can anyone on the forum here explain to me exactly (in easiest terms, please! :) ) on how about doing that?

I tried the Envy route as suggested, but seemed to get nowhere with it. :mad:

Can anyone on the forum here kindly offer me some assistance? :confused: 

Thanks for any help!

---

### Post by sleeperknight on 2007-03-25
All cards that have the name Nvidia are based off of Nvidia's specifications and graphics processor for the card they are build after. (ie 7950 have Nvidia G71 Graphics processor)
The EVGA is just the company that built the card and may have a few extras added in.

---

### Post by Dark Lord Peaches on 2007-03-25
you could download the driver from the Nvidia website and install it yourself

---

### Post by Butthead on 2007-03-25
Um, I already tried doing that, but I'm not totally sure on how to go about configuring the xorg.conf file by hand first. :( 

Wouldn't KATE (the text editor) try to save the newly edited file under a new file extension? :confused: 

Forget about attempting to do it under VI...:shock:

---

### Post by igknighted on 2007-03-25
easiest way (although if you intend to try beryl you will need a 3rd party repo with a newer driver, or go back and give envy another try):
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

then restart X (ctrl+alt+backspc) and an nvidia splash screen should come up before you get to the login.

---

### Post by Butthead on 2007-03-26
Thanks, I'll give it a try. :) 

I'm really not sure how the new driver gets installed that way though. :confused:

Envy kept on telling me that my card was unsupported somehow, that's the reason for my first posting. ](*,)

---

### Post by Butthead on 2007-03-27
Hi igknighted,

Thanks, that seems to have done the trick!  Your help was much appreciated! :)

---

