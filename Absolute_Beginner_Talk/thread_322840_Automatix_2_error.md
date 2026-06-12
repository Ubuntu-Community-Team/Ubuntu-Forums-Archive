---
title: "Automatix 2 error"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by V-600 on 2006-12-21
Hi all,

This is my first post so apologies for any glaring mistakes.

I updated to ubuntu 6.10 a few weeks ago. One of the first things i did was to install Automatix 2 (all went smoothly with that) for various codecs etc. A few days ago i tried to use it to install the ClamAV package it provides (off the top of my head, i think its ClamAV/firestarter). However the install failed and presented an error message (sorry i can't remember what it was) and now whenever I install anything i am presented by the same error.

Updates and new packages still install, its just i would prefer not to have an error everytime they do.

Any assistance on fixing this would be appreciated

---

### Post by Unknowndeepness on 2006-12-21
Can you post the errors your getting?

---

### Post by V-600 on 2006-12-21
To generate this error I selected the Abiword package in Add/remove programs

"E: clamav-base: subprocess post-installation script returned error exit status 1"

The same error pops up when i try to install anything though.

I also include the terminal output from Add/remove programs (i couldn't figure out how to copy and paste so included as an attached screen shot)

Lastly i'll add that Abiword installed and runs successfully.

---

### Post by Medieval_Creations on 2006-12-21
I've seen Automatix throw a similar error.  All I did was go through and try and install teh Security Programs through Automatix again & it went through fine.

Haven't quite figured out why yet.

---

### Post by PriceChild on 2006-12-21
```
sudo apt-get -f install
```
In future please do things yourself... automatix breaks :)

Pricey

---

### Post by V-600 on 2006-12-21
Thanks. i'll try again. I'd thought it may have something to do with firestarter already being installed in System>Administration.

Also went to synaptic and removed anything related to ClamAV. I removed abiword and installed GNU paint (again just as a trial) without error.

Is there a way to install an antivirus program without using Automatix (which is best and do i really need one).

sorry. you posted answer as i was writing this

---

### Post by PriceChild on 2006-12-21
```
sudo apt-get install clamav
```

AVG Free: [http://ubuntuforums.org/showthread.php?t=136064&highlight=howto+avg](http://ubuntuforums.org/showthread.php?t=136064&highlight=howto+avg)

---

### Post by arnieboy on 2006-12-21
An FYI for Pricechild and the rest: The clamav package in Edgy universe is broken and Automatix simply reports the apt error. The fix is to try and install it twice in which some of the broken files from the first attempt get overwritten.

---

### Post by V-600 on 2006-12-21
This will probably seem stupid but i managed to install clamav successfully. How do i run it or change options etc. There is no menu shortcut created and typing clamav in a terminal does nothing

---

