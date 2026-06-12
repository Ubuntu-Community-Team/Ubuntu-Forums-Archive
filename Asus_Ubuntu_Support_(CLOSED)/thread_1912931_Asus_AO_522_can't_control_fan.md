---
title: "Asus AO 522 can't control fan"
date: 2012-01-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Virgjans12 on 2012-01-21
Yesterday I bought an Asus Aspire One 522 with the C-60 CPU. I deleted windows 7 and now have Linux Ubuntu 11.10 installed. Which works great, except for one thing: the CPU will start at 50+ degrees Celcius when Ubuntu is booted, and work it's way up to 70 degrees Celcius in about 20 minutes, at which point I shut it down to prevent damage. I use Xsensors 0.7 to monitor it and at 70 degrees the bar is full and the letters turn red, which is the reason for my precautions. 

To solve this problem I turned to Acerhdf ([http://www.piie.net/?section=acerhdf](http://www.piie.net/?section=acerhdf)). I installed it and followed the instructions from the readme.txt up to 1.3: autostart fan control. It says "to automatically start the fan control you can do: 'echo "options acerhdf kernelmode=1" | sudo tee /etc/modprobe.d/acerhdf.conf'. I type that in the terminal and it asks for my pass. I give it and it says "options acerhdf kernelmode=1.

Then on to step 2.1: loading the module. The readme.txt says: 'to load the module into the kernel type: 'modprobe acerhdf'. However, when I type that into the terminal it says "FATAL: Error inserting acerhdf (/lib/modules/3.0.0-12-generic/updates/acerhdf.ko): operation not permitted".

So what do I do? I can't really use the netbook until I fix the overheating problem. Thank you so much for your help in advance.

Virgil

---

