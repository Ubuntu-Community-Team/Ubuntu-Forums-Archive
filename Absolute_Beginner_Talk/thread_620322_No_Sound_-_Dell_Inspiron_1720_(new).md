---
title: "No Sound - Dell Inspiron 1720 (new)"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by dest581 on 2007-11-22
I recently installed Gutsy, and have been unable to get any sound.  I get the following error whenever I double click on the sound icon or attempt to access volume controls otherwise:
> No volume control GStreamer plugins and/or devices found

I get a similar, larger message about GStreamer that gives no additional information the first time every startup.  

To start fixing the problem, you'd need to know additional information such as what the sound card is.  I don't know how to get that, either.  

I appreciate any help I get.

---

### Post by Arthur Archnix on 2007-11-22
This will spit out your card information
```
lspci | grep Audio
```
Under >system >preferences >sound you can try various settings and test sounds.

---

### Post by corncob on 2007-11-23
I have the exact same problem with a Dell OptiPlex.  That code gave me nothing.  I tried it with both "Audio" and "audio":
```
user@user-desktop:~$ lspci | grep Audio
user@user-desktop:~$ lspci | grep audio
user@user-desktop:~$
``` 
The onboard sound is working when I duel boot to Windows ME.  I started my own thread on this but seem to have lost it.

---

### Post by Arthur Archnix on 2007-11-23
If that returns nothing then its not detecting your audio card. What is the make and model of your audio card?

---

### Post by corncob on 2007-11-24
Its on board audio.  When I boot to Windows ME, where the sound works fine,  the Device Manager says its a Crystal WDM MPU-401 Compatable.  The computer says "designed for 98, NT" so its about 8 or 9 years old.

---

### Post by Arthur Archnix on 2007-11-25
Hmm... well I found this on the web:
```
gksudo gedit /etc/modules
```
Then add under all the rest
```
snd-cs4236
```
Save and exit, Reboot. When it comes back up, make sure your sound channels are unmuted. In a terminal type:
```
alsamixer
```
when you're done in alsamixer type
```
sudo alsactl store
```
to save your changes

---

### Post by corncob on 2007-11-29
I threw in the towel!  I remembered I had an extra PCI sound card (Cobra) and I put it in.  Sound is now working fine, in winME also so I'll put a piece of tape over the onboard sound ports and forget about them.

---

