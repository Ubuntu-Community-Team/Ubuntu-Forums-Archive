---
title: "Graphics Issue - Installation"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by DigitalRedneck on 2006-12-04
Hi, I'm having some issues with getting Ubuntu up and running.

First, I tried using the 6.10 live cd, but the graphics didnt work. It was all multi-colored vertical lines. Same with the safe graphics option.
Second, I tried useing the text version of live cd, and I got it to install, but upon bootup, more of the same graphics issues.
Third, just because I thought 6.10 might be buggy, I deleted my 6.10 install, and installed the 6.06 version, text cd. Unfortunately, more graphics issues.](*,) 

So, I guess it has something to do with my hardware, not supported, or being detected properly, or just a bad installation on my part.

So, here's my hardware:
Asus A8N-E motherboard
AMD Athlon(tm) 64 Processor 3000+
2x1GB DDR-SDRAM (Patriot)
NVIDIA GeForce 6800 GS 
Seagate ST3160023A
Seagate ST3300831A
DVDRW IDE1008

I'm a newb to linux, but I possess the fabled common sense.:-k

---

### Post by Mind my gap on 2006-12-04
I'm having this exact same problem with a GeForce 6600 GT. With Dapper I was able to boot the live CD in safe mode and it was fine (I wanna do a fresh install, not just an upgrade of Dapper). Any help would be much appreciated.

---

### Post by johnny9794 on 2006-12-05
Thats so fricken IRONIC lol

ok last night i tried to run gparted off the live cd and well i got that same problem, so i tried running ubuntu 6.06 and 6.10 same thing, so i tried knoppix 2005 and 2006 i got the same graphics crap.
Now what i have is a MSI NX-6600 gfx card so i started to think this was the graphics card issue... on my mobo i have onboard graphics aswell so i turn off my pc and pulled the 6600 out and hooked my monitor up to the onboard intel intergrated gpraphics... Boom i was able to run all the live cd's that i have, ubuntu, gparted, knoppix, ect.

So im thinking its something to do with the 6-series cards :S i do not have a solution but i will be buying a new gfx card, Ubuntu is worth it.

I did a search and my MSI NX-6600 does not support linux... BS? yes it is...

---

### Post by rajeev1204 on 2006-12-05
hi

u have to install the Nvidia-glx drivers ( not nvidia glx legacy) from the repositories . 

enable this driver by typing "sudo nvidia-glx-config enable".

u will get a warning saying xorg has changed . just manually edit xorg.conf and change nv to nvidia.

u probably did not do that and did that md5 crap warning/ i did too.

next time u boot it will say xserver cannot start

type this "sudo dpkg-reconfigure xserver-xorg"

dont read too much of it , just keep selecting defaults and only check for monitor type,resolution etc

and yes, the 6600 GT is supported.


regards

rajeev

---

### Post by jubxie on 2006-12-07
I am also having similar problems with my 6600gt. I get garbled graphics on live cd boot for both safe graphics mode and normal on edgy and normal on dapper. Dapper used to install fine. This seems to be a new (therefor hardware) problem. For me, it must be 
 
 - a new problem with my graphics card(card works fine on existing install)

or

 - dvd-rom (possible because i've been having problems with  dvd shrink   and dvd:rip) 

or

 - memory(not likely because it is quality memory and only a few months old)

haven't tried changing driver (can't get that far with 386 disc), but really seems like a hardware graphics card issue. no questions, just adding my recent experience.

---

### Post by daka on 2006-12-08
Hi
How do you get to follow this advice???? if you can't see the screen to connect??????

"you have to install the Nvidia-glx drivers ( not nvidia glx legacy) from the repositories .and ...enable this driver by typing "sudo nvidia-glx-config enable".

Daka

---

### Post by HokeyFry on 2006-12-08
try booting into recovery mode and use the command line to do it

---

### Post by padre999 on 2006-12-14
> **daka said:**
> Hi
How do you get to follow this advice???? if you can't see the screen to connect??????

"you have to install the Nvidia-glx drivers ( not nvidia glx legacy) from the repositories .and ...enable this driver by typing "sudo nvidia-glx-config enable".

Daka

Once you are at the login screen after booting you can press CTRL+ALT+F1 (or F2,3,4,...) to get another session. You are at the command line, log in.

Then it would be a ```
sudo apt-get install nvidia-glx
```that makes you install the Nvidia-glx package (please correct me if the command line should be wrong!).

Then as described do a ```
sudo nvidia-glx-config enable
```

To edit the Xorg.conf for replacing "nv" with "nvidia" use ```
sudo nano /etc/X11/xorg.conf
```But be careful not to change anything else!

Follow the rest of the instructions...

That's how you could do it. I don't know though if it will fix the problem. Maybe someone can give feedback? Or maybe there is another proper HOWTO on this? I guess what this here is doing is nothing different than installing the nvidia driver.

---

### Post by Pnikosis on 2006-12-15
> **padre999 said:**
> Once you are at the login screen after booting you can press CTRL+ALT+F1 (or F2,3,4,...) to get another session. You are at the command line, log in.

Then it would be a ```
sudo apt-get install nvidia-glx
```that makes you install the Nvidia-glx package (please correct me if the command line should be wrong!).

Then as described do a ```
sudo nvidia-glx-config enable
```

To edit the Xorg.conf for replacing "nv" with "nvidia" use ```
sudo nano /etc/X11/xorg.conf
```But be careful not to change anything else!

Follow the rest of the instructions...

That's how you could do it. I don't know though if it will fix the problem. Maybe someone can give feedback? Or maybe there is another proper HOWTO on this? I guess what this here is doing is nothing different than installing the nvidia driver.
I'm also new, and I'm having the same issue. The problem is that I haven't installed Ubuntu yet, because of the graphics problem... So, anyone knows how could I make it? ](*,)

---

### Post by drphilngood on 2006-12-15
> **Pnikosis said:**
> I'm also new, and I'm having the same issue. The problem is that I haven't installed Ubuntu yet, because of the graphics problem... So, anyone knows how could I make it? ](*,)

I´m not sure I understand you but you might find this guide helpful:

[psychocat´s-guide]("http://www.psychocats.net/ubuntu/index")

...and if you still need help, start a new thread.

---

### Post by Pnikosis on 2006-12-15
> **drphilngood said:**
> I´m not sure I understand you but you might find this guide helpful:

[psychocat´s-guide]("http://www.psychocats.net/ubuntu/index")

...and if you still need help, start a new thread.

Sorry, my english sucks. But my problem is exactly the same as described in this thread, but I can't edit any file (to install nvidia drivers and edit the xorg.conf file to enable them), because I haven't installed Ubuntu yet (I can't make it to run from the live cd, because the graphics don't work)

---

### Post by drphilngood on 2006-12-15
> **Pnikosis said:**
> Sorry, my english sucks. But my problem is exactly the same as described in this thread, but I can't edit any file (to install nvidia drivers and edit the xorg.conf file to enable them), because I haven't installed Ubuntu yet (I can't make it to run from the live cd, because the graphics don't work)

Your English is fine, I´m just not too bright sometimes.
Anyway, I would try installing from the Alternate Installer CD.  It has solved many an installation problem.

---

