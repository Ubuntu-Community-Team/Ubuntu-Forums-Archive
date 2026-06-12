---
title: "messing around with nvidia drivers, need help"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by babygoose on 2007-07-23
i know this topic has probably been done to death by now, i have read many posts regarding this issue as well, but i would like to get a concise answer on a specific thing--
i have messed around with installing nvidia drivers for about 3 days now--the first one would be using the restricted drivers method, then next one being using "envy", and the next one being some troubleshooting after losing my gui for some reason!
now, i just finished getting my gui back after the "incident", i ended up in the xorg file etc etc, and i wasnt sure if i messed anything up or not by doing that so i just did a fresh install! now, i have good knowledge of windows systems, but am relatively new to ubuntu--
after this friesh install, i am wondering the best method to get the nvidia drivers to work:
1. enabling the restricted driver
or
2. using "envy"
or
3. this guide [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
or
4. some other way i have to read about!
please help, as i said, i have been messing with this for a couple of days and i want to be able to use the new OS normally just for awhile at least ;)
thanks very much

---

### Post by rax_m on 2007-07-23
I would say enabling the restricted drivers because its the Ubuntu default and will most likely work. 

I have used Envy in the past and it does a great job, but why install it if Ubuntu will do it automatically. Actually, to answer my own question I think Envy might allow you to install more recent versions of the driver. 

Using the restricted drivers has worked perfectly for me..

---

### Post by babygoose on 2007-07-23
okay, so if i use envy lets say, thats that, i shouldnt have to do anything else??

---

### Post by babygoose on 2007-07-23
and if i do, do i not have to worry about the restricted driver now? i want to get this right the first time so i dont have to do another fresh install!

---

### Post by rax_m on 2007-07-24
Yep.. that's my understanding of it. 

They are just different methods of installing the Nvidia driver. Envy just allows you to install the latest version. 

If you're new to Linux, I would suggest going for the restricted driver method and learning from that point on..

---

### Post by babygoose on 2007-07-24
okay, just to clarify:
i am leaning towards the envy method, i have used it before, but i ended up trying to mess around with it and it stopped working..anyways, if i do the restricted driver method, then say, i am feeling bold and want to do the envy thing later, will the envy driver automatically become the default one? or would i have to uninstall the other one!

---

### Post by jmlock on 2007-07-24
hey ive been having nvidia probs for days now  please post the way you go and the results .
restricted drivers=evil

---

### Post by spur on 2007-07-24
I would keep things as clean and simple as possible. Don't use both envy and restricted. It's the same driver. Envy gives you the latest driver for your card. Retsricted driver gives you the last stable one for ubuntu. Having different versions installed at the same time could cause conflicts and problems.I am using the restricted driver on my 64bit system and it works fine. No fiddling. When I tried envy or restricted on my system with 32 bit os installed I had serious problems.
Upshot is I would go restricted driver if I was you (and I am not!)

---

### Post by babygoose on 2007-07-24
thank you! i was waiting for a definitive answer! i used the restricted driver on my first install and it worked fine, but then i started reading about envy and the million other ways to get the driver on there, thats when my problems started! thank you again, and you are very right, you are not me! :D

---

### Post by babygoose on 2007-07-25
well, i enabled the restricted driver! no problems so far...i got beryl, and that works fine! thanks for the help people! 
oh and one more thing, could the restricted driver be updated at some point ever?? if so, would the system automatically pick it up?

---

### Post by FuturePilot on 2007-07-25
> **babygoose said:**
> well, i enabled the restricted driver! no problems so far...i got beryl, and that works fine! thanks for the help people! 
oh and one more thing, could the restricted driver be updated at some point ever?? if so, would the system automatically pick it up?

They will be updated when the next version of Ubuntu is released. If you upgrade I think it should automatically pick it up.

---

### Post by babygoose on 2007-07-25
and the card is a nvidia geforce go 7800 gtx,

---

### Post by doomster on 2007-07-25
Just an addition
when i tried to use envy without enabling the restricted drivers support, i got the usual "x-server was unable to start" problem.. i enabled restricted drivers support, and used then envy to fetch the latest drivers, from nvidia.com. everything worked perfectly.

---

### Post by babygoose on 2007-07-25
okay, did you use the automatic envy install? or the manual install?

---

### Post by doomster on 2007-07-26
i used automatic envy install.. i have a Nvidia 6200 installed on my system, and the auto-one, worked flawlessly

---

