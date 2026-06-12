---
title: "ubuntu 19.04 on newish apple hardware"
date: 2019-09-15
forum: Apple Hardware Users
---

### Post by ivo-welch on 2019-09-15
I read the sticky forum FAQ. I have information to add (perhaps someone in charge can update the FAQ), and I have information to ask.

**macbook**** air 2019:** I can positively confirm that it is possible and replicable to boot a vanilla installation ubuntu 19.04 stick on an unprepared macbook air 2019. this requires simple steps: [1] boot with cmd-r and disable in the boot utilities (top menu) all the boot security precautions. [2] boot with option-r. [3] choose the third entry ("EFI") from the offered list. (there is no indication that it is a usb stick, much less one holding ubuntu.) you will get all the way to the installation GUI, which looks terrific. (it seems to use the high-res of the 2019 air.) I did not play much further with it, because the trackpad did not work. I just shut it down. given that apple air 2019 hardware can boot a ubuntu USB stick, presumably it should be able to boot a full linux from an external HD, too, provided [2] is executed.


**iMac Pro 2018:** however, trying to replicate my success on an iMac Pro 2018 was less successful. although I can see that ubuntu is beginning to start up, the display never switches to a valid mode again after a second or two. so, it is not an EFI problem. it is a device driver problem.


are there versions of ubuntu compatible with recent iMac Pro and iMac 5K (both from the last <4 years)?  [most posts here seem to have been about older apple hardware]

if so, is there a list of what works and what does not work?

---

