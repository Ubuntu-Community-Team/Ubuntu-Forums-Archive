---
title: "Eyetoy"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-08-07
how can i use this as a webcam for ubuntu and i have the new smaller silver on btw thanks for any help

---

### Post by mcduck on 2007-08-07
I remember that the EyeToy should work out-of-the-box, you just need to plug it in ;)

---

### Post by por100pre1 on 2007-08-07
> **mcduck said:**
> I remember that the EyeToy should work out-of-the-box, you just need to plug it in ;)

Fine. What about the PS2 headset?

---

### Post by llzero1337 on 2007-08-07
no it dont

---

### Post by por100pre1 on 2007-08-07
> **llzero1337 said:**
> no it dont

So it doesn't work... that's bad. :(

---

### Post by mcduck on 2007-08-07
> **por100pre1 said:**
> Fine. What about the PS2 headset?

Do you mean the one that came with SOCOM? At least I'm sure that that works. I use it myself with Skype. :)

Also I'm sure it's possible to get the EyeToy working as well. I've seen posts about it working on these forums, and I know Sony has also made Linux drivers for it.

---

### Post by sailor2001 on 2007-08-07
for your headset: rt. click sound icon and open volume control....select preferences and tick everything you need....... your mic maybe "mic#2" so be sure to tic "mic select"

---

### Post by llzero1337 on 2007-08-08
i ment the eye toy >_>

---

### Post by Wyrmling on 2007-11-04
Yeah I know, this post is one of the older one and I dont know, if there is still interrest in answers, but I tried to get my eye-toy working and it went like this for me:

First you have to install the **ov51x-jpeg-source**-Package.

After installing you have got a new file **/usr/src/ov51x-jpeg.tar.bz2**.

Open a terminal and change to **/usr/src/**.

Enter
```
sudo tar -xvf ov51x-jpeg.tar.bz2
```

switch to the new folder (/usr/src/modules/ov51x-jpeg/) and enter
```
sudo make
```
followed by
```
sudo make install
```

To get your cam working you now have to start some modules.
```
sudo modprobe videodev
sudo modprobe i2c_core
sudo insmod /lib/modules/`uname -r`/extra/ov51x-jpeg.ko

```

The 'uname -r'-Part is the Number of your current Kernel - just use the TAB-key some times to get to view your folders.

Interested if it worked? Sure ;)

Install camgrap
```
sudo apt-get install camgrab
```
switch to the folder where you want to have the snapshot and type ```
camgrab
```

BTW: Unless you dont know how to start the modules together with your system starting up, you have to start them manually every single time.

---

### Post by barney_1 on 2007-12-11
Worked like a charm in Gutsy for me.  Thanks!

---

### Post by Jose Catre-Vandis on 2008-01-11
I get three black and white images in Camorama and neither Skype nor Amsn will pick it up?

---

### Post by nikoPSK on 2008-01-11
That works, :KS

---

