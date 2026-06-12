---
title: "Freezing problem!"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-07-03
I used to run Ubuntu 5.10 on my old PIII 1.2 GHz, 256 MB RAM and 128 MB GeForce 4 MX 440. The system would freeze after it starts within minutes after installing the nVidia driver. This happened whether the driver is from nVidia.com or from Automatix. I decided to change to OpenSUSE 10.1.

After downloading the large 3.4 GB image, the same problem happened after installing the driver.

OpenSUSE was too demanding for my PC (I never had above 10 MB of free RAM at any time while running it!). So, I am thinking of switching back to Ubuntu or even Kubuntu 6.06. I just want to make sure that the problem won't happen again.

---

### Post by Amorphous_Snake on 2006-07-04
Can someone help me, please?

---

### Post by MaximB on 2006-07-04
I think you've installed incorrect driver...or you didn't install it properly

---

### Post by Amorphous_Snake on 2006-07-05
I did install it properly. It did the same even with the newest legacy driver.

People, please, I need help. If I can't fix this problem, then it's bye bye Linux. And I don't want that!

---

### Post by Apple 101 on 2006-07-06
What nVidia graphics card do you have?  It could be that you need the nvidia-glx driver, or the straight nv driver.

---

### Post by aeto on 2006-07-06
try to get automatix. u can actually just get nvidia-glx & other needed files through synaptic..but automatix saves u time & detects ur card & installs the required driver. normally ubuntu would provide u with the default nv driver if u have an nvidia card. u only need the nvidia drivers for 3d acceleration.

---

### Post by djsroknrol on 2006-07-06
Was this after the install was finished? I had a similar problem with my ATI card and screensavers is the reason I ask...I wound up turning the screensavers off to solve the problem and using a blank screen if that helps...

---

### Post by Amorphous_Snake on 2006-07-08
The problem happened after installing the driver either by automatix or by me.

I saw at the nvidia forums that many people are complaining of the same thing, but I don't think up till now there was any solution.

---

### Post by Amorphous_Snake on 2006-07-08
I installed a fresh copy of ubuntu, updated it to the latest updates (the version is 5.10 by the way, and don't tell me to try 6.06, I tried a completely different distro, OpenSUSE 10.1, and still I had the problem), and then I installed the nvidia driver, this time through EasyUbuntu.

The result was... the same. The system still freezes randomly when using Firefox, Nautilus, the terminal, ...

So, is there some kind of solution to this problem? Because I just can't take anymore of this. I tried many things and still the problem exists. The driver was the only thing I installed, so it must be it. I do need the driver, and my card is not ancient. There are people working with much older cards than mine and they don't complain!

---

### Post by Amorphous_Snake on 2006-07-09
Am I asking in the wrong place, or is my problem too difficult that even the Ubuntu gurus can't fix it?

I am not trying to be rude or anything. I just want to get help!

---

### Post by Apple 101 on 2006-07-09
You might try asking in the General Support area for more help, instead of waiting here.

---

### Post by Amorphous_Snake on 2006-07-18
Problem solved. Thanks to TSELIOT.

Just add:

Option "NvAGP" "0"

in your /etc/X11/xorg.conf and you can download any driver that you want.

This saved my day. Now I am using Ubuntu 6.06 and I am back in the game!

---

