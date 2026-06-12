---
title: "Hi All, I need some help please"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by sMC 2k7 on 2007-06-29
Hey Ubuntu community, i am a very recent ubuntu user, i recently installed 6.06 for 1 night then the next day (today) i have installed 7.04 BUT i am getting some problems with both. my basic problem is i get no picture on my 27" and 40" tv's but i do on my 19". i get the start or install ubuntu screen then i run it and then just when the desktop is about to load my screen goes black and i get the message mode not supported, (will it work once installed onto the HDD?) 

i don't really know much about Linux, i have windows xp on my main computer and that is the OS i know most about, i have a mac powerbook g4 which im using to write this and now im looking to learn linux, so any help or advice would be very helpful

Thank you much
sMC

---

### Post by Zzl1xndd on 2007-06-29
More then likely its using the Versa driver and its very basic and probably can't handle the screen size, What type of Video card is the the machine?

---

### Post by sMC 2k7 on 2007-06-29
the graphics card is NVIDIA® GeForce 6150 LE graphics. can i get it to work with a monitor that size?

---

### Post by Uncle Gates on 2007-06-29
It seems like you got it bad. Don't worry this forum should get you up and running. What video card do you use? It wouldn't be an ATI card would it???

---

### Post by sMC 2k7 on 2007-06-29
the graphics card is NVIDIA® GeForce 6150 LE graphics, i assume the graphics card is the video card???

---

### Post by Seisen on 2007-06-29
Have you installed the nvidia drivers for your card on Ubuntu that could be the problem.

---

### Post by Zzl1xndd on 2007-06-29
after you install Ubuntu then you can install the Nvidia driver via the Restricted driver manager or with a Script called envy it should also install the Nvidia settings manager under Applications -> system tools and that should allow you to set it to a res that the Monitor will suport.

---

### Post by sMC 2k7 on 2007-06-29
ok so ill have to use my 19" so i can get a picture, then download the nvidia drivers from their site then try on the bigger monitors??

---

### Post by Zzl1xndd on 2007-06-29
> **sMC 2k7 said:**
> ok so ill have to use my 19" so i can get a picture, then download the nvidia drivers from their site then try on the bigger monitors??

You can use their site but system -> admin , there is a restricted driver tool if you just click the check mark next to your video card it should do the rest ;)

---

### Post by sMC 2k7 on 2007-06-29
ok, well im out tonight but i will try this and see what happens, ill be back and let you know how it goes. thanks  you for the help. keep ubuntuing...

---

### Post by Uncle Gates on 2007-06-29
I can't check my restricted drivers for my ATI video card. What do I do then?

---

### Post by costa_g on 2007-06-29
I recommend installing your graphics card using a program called Envy, it makes the process a whole lot easier for those using an Nvidia graphics card.

Please find here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Zzl1xndd on 2007-06-29
Ok then I will recomend using envy but I am gonna tell you that using envy almost always works but often after a Kernel update you will need to re-run it [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by sMC 2k7 on 2007-06-30
hi guys, i tried checking the box in restricted drivers but it did not work it stays unchecked, so ill use the envy program and try that. once these are installed will i be able to use ubuntu on a 27" monitor with compiz or beryl???

---

### Post by costa_g on 2007-07-01
Installing the Nvidia drivers allows hardware acceleration so I see no problem with you been able to do this.

Here's Beryl's installation instructions for Ubuntu Edgy:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

Feel free to skip to **"Adding Beryl repository"**

Good luck and tell us how it goes.

---

