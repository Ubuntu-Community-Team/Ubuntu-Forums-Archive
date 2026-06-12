---
title: "Issues following NVIDIA driver installation guides"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by NeptuneUK on 2007-08-20
Tried following some guides to install the latest NVIDIA drivers but kept getting issues (errors etc)
Im using Ubuntu Studio.

Fiesty???? 7.04????  dunno  D:

ATI drivers on my other PC installed ok though, I just copied and pasted some text into the terminal. grr

---

### Post by Bachstelze on 2007-08-20
If you don't tell us what the errors you get are, we won't be able to help you...

---

### Post by nitro_n2o on 2007-08-20
what is the problem??? is this a problem... i don't see a problem.. 
anyways this should solve your problem.. 

```
sudo apt-get install nvidia-settings 
```
then ```
gksudo nvidia-settings
``` this will give u a nice gui to make your graphics card work... 
btw, setting up nvidia is way easier than ATI

---

### Post by NeptuneUK on 2007-08-20
I changed resolution in the settings that I acessed with the terminal, however the settings were lost once I rebooted :S


(this is with the original drivers that came with the installation, kept gettin errors when trying to sort out ones from NVIDIA site)

---

### Post by NeptuneUK on 2007-08-22
Ive followed the above post once more and the resolution settings appear to be missing now! Eek what have I done?

---

### Post by stchman on 2007-08-22
> **NeptuneUK said:**
> Ive followed the above post once more and the resolution settings appear to be missing now! Eek what have I done?

As far as Nvidia drivers I would just enable the Restricted driver.  Once that is done if the resolution you want os not there then you can edit your xorg.conf
```

sudo gedit /etc/X11/xorg.conf

```
Lets say you want to have 1280x1024.  Make sure that "1280x1024" is the first resolution in the line of resolutions.

---

