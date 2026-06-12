---
title: "System Monitors: what and where?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by ricesteam on 2006-08-04
I noticed some desktop have system status monitors embedded into their desktops and it looks very useful. That monitors displays how much space a particular partition has, the temperature of various hardware, the CPU usage, the memory usage..etc..

What and where can I find those tools?  I tried using gdesklet ones but they are not the one I'm looking for.  I want a total desktop-embedded one, or at least one that creates the ebedded illusion.

Thanks in advance.

---

### Post by jd65pl on 2006-08-04
I think this effect is obtainable in gdesklets if you turn off the borders on the desklet it gives the illusion of being embedded in the desktop

---

### Post by kurniawands on 2006-08-04
> **ricesteam said:**
> I noticed some desktop have system status monitors embedded into their desktops and it looks very useful. That monitors displays how much space a particular partition has, the temperature of various hardware, the CPU usage, the memory usage..etc..

What and where can I find those tools?  I tried using gdesklet ones but they are not the one I'm looking for.  I want a total desktop-embedded one, or at least one that creates the ebedded illusion.

Thanks in advance.

use **sysinfo**. you can get it using add/remove application gui. don't forget to check the unsupporteds.

---

### Post by ricesteam on 2006-08-04
Thanks for the replies.

I don't really like the gdesklet ones...and they seem to take alot of resource.

I'm more interested in the stats and I want it to be easily accessible ie. on the Desktop than having lots of windows open.

So sysinfo will allow me to display all the info I seek?

---

### Post by jd65pl on 2006-08-05
I hear aDesklets is far less resource heavy than gDesklets

---

### Post by confused57 on 2006-08-05
Are you looking for something like lm-sensors?  If so, you'd need to check if your motherboard chipsets are supported:
[http://www.lm-sensors.org/wiki/SupportedDevices](http://www.lm-sensors.org/wiki/SupportedDevices)

Also, there's a "HowTo" for configuring lm-sensors & gkrellm can be used as a frontend monitor.

This may not be what you're looking for...

---

### Post by qrm on 2006-08-05
IIRC conky should be what you are looking for. In the Howtos7tips section should be a tutorial

---

### Post by tjansson on 2006-08-06
I use gkrellm which is very lightweight and with the invisible skin it integrates nicely into the desktop - see a screnshot here:
[http://www.tjansson.dk/phpAlbum/main.php?cmd=imageview&var1=screenshots%2Fgkrellm.png&var2=1](http://www.tjansson.dk/phpAlbum/main.php?cmd=imageview&var1=screenshots%2Fgkrellm.png&var2=1)

---

### Post by ricesteam on 2006-08-06
what theme is that in the gkrellm you have?

---

### Post by seshomaru samma on 2006-08-06
wow, gkerllm is great
the only problem is that my screen resolution is high and gkerllm comes out in very small letters, is there anyway to make it bigger?

---

### Post by tjansson on 2006-08-06
> **ricesteam said:**
> what theme is that in the gkrellm you have?

It was one that was include in the gkrellm-skins package when I ran Mandrake and loved it, so when I couldn't find it on Ubuntu I downloaded the the skin, which is called "invisible" from the page: [http://www.muhri.net/gkrellm/](http://www.muhri.net/gkrellm/)

Direct link to the skin: [http://www.muhri.net/gkrellm/invisible.tar.gz](http://www.muhri.net/gkrellm/invisible.tar.gz)

---

### Post by tjansson on 2006-08-06
> **seshomaru samma said:**
> wow, gkerllm is great
the only problem is that my screen resolution is high and gkerllm comes out in very small letters, is there anyway to make it bigger?

If you right-click on gkrellm in the top of the gkrellm window (or focus on the gkrellm and press F1) then you can chose configuration. Under Themes->Fonts you can change the font size.

---

### Post by seshomaru samma on 2006-08-06
Great, thanks
:grin:

---

