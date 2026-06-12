---
title: "Micro SD not working on Acer"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by chameleonkid on 2007-03-29
So I got a 1 GB Micro SD card with adapter SD and for some reason Ubuntu will not recognize it. Any Ideas or Solutions?

---

### Post by jadda on 2007-03-29
sudo modprobe tifm_sd

Now to insert a SD media card and it should auto mount. 
If all went well you can now edit the the /etc/modules file so you can load the drivers for the card reader on boot up 
From terminal type: 

sudo gedit /etc/modules

Add the drivers to the modules file 

tifm_sd

this did the trick for me

---

### Post by flowbot on 2007-10-10
> **jadda said:**
> sudo modprobe tifm_sd

Now to insert a SD media card and it should auto mount. 
If all went well you can now edit the the /etc/modules file so you can load the drivers for the card reader on boot up 
From terminal type: 

sudo gedit /etc/modules

Add the drivers to the modules file 

tifm_sd

this did the trick for me

great stuff ... this worked for my SanDisk 2GB Micro SD.

---

