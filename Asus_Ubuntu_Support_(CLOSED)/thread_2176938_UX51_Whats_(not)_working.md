---
title: "UX51 Whats (not) working?"
date: 2013-09-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by owerner on 2013-09-26
Hi,

I have been playing around with Linux for the past few days and I am not sure yet if I (can) keep it as my main OS.
I have several Problems and try to collect some in this thread. I hope there are other people who are interested in getting a smooth ubuntu running on that nice Zenbook UX51VZ. I hope you can participate in finding the solutions. 

Everything I tried was on 13.04.

[B]Fancontrol
[/B]Its possible to run without any Speed Sound on win if in idle mode/little browsing. I want this for Ubuntu, too. I tried lm-sensors and fan control. They are NOT working.
I cant detect all sensors. 
[http://askubuntu.com/questions/53762/how-to-use-to-use-lm-sensors](http://askubuntu.com/questions/53762/how-to-use-to-use-lm-sensors)
sensors command works. Showing me some sensors but sudo pwmconfig says "/usr/sbin/pwmconfig: There are no fan-capable sensor modules installed"


[B]FN Keys
[/B]The Keys to dim the keyboard light wont work. No idea how to fix this.

[B]Nvidea + BumbleeBee
[/B]Not tried yet.
Maybe this solution (?!): [http://ux51vz.blogspot.de/](http://ux51vz.blogspot.de/)

[B]Sonic Master external subwoofer
[/B]Working, but if i activate them, my mic in skype stops working. 
[http://askubuntu.com/questions/189304/no-sound-from-external-subwoofer-sonic-master-on-an-asus-n76vm](http://askubuntu.com/questions/189304/no-sound-from-external-subwoofer-sonic-master-on-an-asus-n76vm)



To be continued....

---

### Post by Frysboxen on 2013-09-27
I'm experiencing the following problems:

**External monitor connected to HDMI**
"Works" out of the box, but the display bugs while refreshing, which results in "ghosting"-behaviour. I'll attach a photo of the bug later.

**External monitor connected to VGA**
Works, but the image is tearing/flickering. Don't know if this is hardware related or software related. Seen this behavior on two UX51VZ, but I can't confirm if this issue is Linux-exclusive since I haven't tried connecting an external monitor on Windows.

**Touch screen**
Mouse cursor jumps to bottom right corner when using mouse/touch pad after having used the touch screen.

---

### Post by owerner on 2013-09-28
To get the external monitor working, you need to install Nvidea driver, right? How did you do that? Just used the standard driver? Or some solution with bumblebee? 
This guys seems to have found some kind of solution: [http://ux51vz.blogspot.de/](http://ux51vz.blogspot.de/)

I have no TouchScreen. Which model do you have, I have the UX51VZA from Europe. 

What about the fanspeed. Mine isnt exactly loud, but as I said: In win it was ZERO for most of the time. Which was awesome.

Maybe I am going to try the latest Ubuntu 13.10 Beta. To see if its promising. I will keep you updated.

---

### Post by Frysboxen on 2013-09-30
> **owerner said:**
> To get the external monitor working, you need to install Nvidea driver, right? How did you do that? Just used the standard driver? Or some solution with bumblebee? 
This guys seems to have found some kind of solution: [http://ux51vz.blogspot.de/](http://ux51vz.blogspot.de/)

I have no TouchScreen. Which model do you have, I have the UX51VZA from Europe. 

What about the fanspeed. Mine isnt exactly loud, but as I said: In win it was ZERO for most of the time. Which was awesome.

Maybe I am going to try the latest Ubuntu 13.10 Beta. To see if its promising. I will keep you updated.

I tried the steps described in the link you posted, and it gave me the same results as installing Ubuntu 12.04.3 or 13.10 Beta, where nvidia-prime is available in the repo.
After installing nvidia-prime, the external monitor works with HDMI, while the internal display does not. There seems to be some [Optimus support in the 3.12 kernel]("http://www.phoronix.com/scan.php?page=news_item&px=MTQ2MjI"), but I have yet to try the RC-version of the kernel. 

For me, touchscreen worked out of the box. My model is UX51VZA as well. I haven't experimented with the fan speed, but it is not constant, i.e. it does increase its speed when performing heavy tasks. I haven't tried Windows on the laptop, so I have no reference.

---

### Post by owerner on 2013-10-09
Good to know. I am just waiting for the new ubuntu which will be released in 8 days. The beta I just tested looks promising. I hope that I will find some serious improvement. Interesting though that you have a touch screen...

What about your fn keys? DOes fn+F3/4 work for you to dim the keyboard background light?

---

