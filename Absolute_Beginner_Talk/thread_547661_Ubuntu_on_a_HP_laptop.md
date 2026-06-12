---
title: "Ubuntu on a HP laptop"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by William S on 2007-09-10
Alright, I've tried to install Ubuntu on a HP laptop DV 6000. It runs currently with Vista. It's with an AMD 64 Turion CPU. I got live CD's for AMD 64 and for 32 bits CPU, also got a third one for 32 bits with Xubuntu. I can't get anyone of them to work on that computer. 
And then I try the text based installation. All goes well until the partitioning of the disk. It can't resize the excisting one due to "an unknown reason"
Any suggestions for what to do or has installing Linux distros been more tricky with Vista?

---

### Post by Acglaphotis on 2007-09-10
Resize partitions with vista. It *will* save you trouble.

---

### Post by William S on 2007-09-10
Alright this error message seems to go through every live CD I tried. 
```
 
195.584000 bcm 43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed" 
``` 

Any ideas?
I checked every CD for defects, found nothing.

---

### Post by dptxp on 2007-09-10
Try to partition with GParted. Download GParted and make live CD.
But try with Vista first as suggested earlier here.

---

### Post by Acglaphotis on 2007-09-10
> **William S said:**
> Alright this error message seems to go through every live CD I tried. 
```
 
195.584000 bcm 43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed" 
``` 

Any ideas?
I checked every CD for defects, found nothing.

That's the driver for your wireless not loading properly, dont worry it's normal in hp's, you can get the right driver once you install ubuntu (sudo aptitude install bcm43xx-fwcutter).

---

### Post by William S on 2007-09-11
Still get errors while I try to download it. 
But also it wouldn't display GNOME. 

```
 [0.099517] pnp: PnPAACPI: Method_ Name __ CRS failure for PNP0C02 
[0.12700] PCI: Failed to allocate mem resource #6:20000@dd000000 for 0000:05:00.0
``` 

Yeah I tried to download the driver for wireless using aptitude, but I get 404 not found errors.

---

### Post by misfitpierce on 2007-09-11
Try this in terminal AFTER you download all ubuntu updates...

sudo apt-get install bcm43xx-fwcutter   

Select yes and it will do rest. Now wait a min and restart and should turn on upon boot.

---

### Post by kane77 on 2007-09-11
actualy try 
```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install bcm43xx-fwcutter 
```
what graphic card do you have?

---

### Post by William S on 2007-09-11
> **kane77 said:**
> actualy try 
```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install bcm43xx-fwcutter 
```
what graphic card do you have?

I got a  NVIDIA Geforce 8400 M GS

---

### Post by William S on 2007-09-12
Hmm still haven't sovled this after trying everything you all said here. 
Any suggestions?
And to install fwcutter thingy does not work, I still get 404 not found errors (yes that's after installing all updates)

---

### Post by hessiess on 2007-09-12
try a difarent distro,  and google sertch 
the make of laptop+linux problems

---

### Post by William S on 2007-09-13
This seems to be a problem to every distro I try, not the fwcutter problem though, but to display the x window system.

---

