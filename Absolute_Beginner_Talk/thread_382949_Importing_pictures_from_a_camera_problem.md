---
title: "Importing pictures from a camera problem"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2007-03-12
I just tried to hook up my Canon PowerShot S400 to offload some pictures and I keep getting this error

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Not sure what this is as it was working fine a couple of months ago...

Could it be my USB printer that is also hooked up?  Any help is appreciated.

---

### Post by MakLeod on 2007-03-13
/bump ... anyone?

---

### Post by MakLeod on 2007-03-13
/bump for the morning crowd.

---

### Post by cnbiz850 on 2007-03-13
same problem here.  It worked fine before.

---

### Post by crack on 2007-03-16
got the same problem here,

i belive it is an update problem, cause i remember that there was something concerning cameras in update manager few days ago...

---

### Post by onegreenparker on 2008-03-26
Picked up the same problem....

Tried f-spot, gThumb, gtkam and digikam, all not working for my Kodak M753.

....Using Xubuntu Hardy....

---

### Post by Teber on 2008-03-26
did a quick test with my canon powershot s60. downloading went smoothly as usual. gutsy here, fully updated

---

### Post by sargetech on 2008-03-26
> **MakLeod said:**
> I just tried to hook up my Canon PowerShot S400 to offload some pictures and I keep getting this error

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Not sure what this is as it was working fine a couple of months ago...

Could it be my USB printer that is also hooked up?  Any help is appreciated.

Give this a try, instead of connecting the camera to the pc
take the card out of the camera (sd,cf ) which ever your camera uses
and use a card reader instead!!!! works great and  transfers photos a lot faster!!!
My Minolta 7hi will not work when I connect it directly to the pc, but using a 
card reader solved the problem!!!!
usb card readers are cheap and work with linux (ubuntu):popcorn:
hope this helps!!!!

Live Long and Prosper!!!

---

### Post by onegreenparker on 2008-03-26
My camera has a card and onboard memory. 
If I use a card reader, I still won't get the goods off the onboard memory.

---

### Post by sargetech on 2008-03-26
> **onegreenparker said:**
> My camera has a card and onboard memory. 
If I use a card reader, I still won't get the goods off the onboard memory.
most cameras allow you to transfer the onboard
memory contents to the  
card while the card is still in the camera!!
I do that with my cell phone memory
I can transfer the phones internal memory to 
the micro sd card inside the phone!!
are you able to do the same thing????

If all else fails!!! are you able to use a windows pc
just to get the photo files off the camera and then
transfer them to a cd or memory card that your 
camera uses????](*,)

---

### Post by Fernanernie on 2008-04-12
Try launching the Application as root. I know this isn't the best way of doing things, but this is the only way that I've been able to get it to work.

 I wasn't able to get my camera recognized at all either. I closed the Apps (both gThumb and gtkam exhibited the same problem). Opened up a terminal, su'd and then launched App there, and was able too see the camera no problem.  Running Hardy Heron, and trying to pull them off of a Kodak z1275 internal memory.

Hope this helps some of you that really need to get the pics of in a hurry.

---

