---
title: "Yet another graphics problem (3monitors)"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by splatcat on 2007-08-03
Hi all, and thanks in advance for any help :)

I am currently running ubuntu 7.04 32bit desktop version and am completely lost when it comes to the graphics front. I am new to ubuntu and linix in general so please bear with me....

My system contains;

AMD 3200+
AGP Radeon 9600XT (this has two monitor ports)
 connected is 2x Samsung LCD syncmaster913n 19"
PCI  Radeon 9200 (also two monitor ports)
 connected is 1x CTX LCD 15"

I have installed the latest radeon drivers using the "get packages" built into ubuntu. I have then manually installed the ati catalyst control centre. As is probably obvious i would like two set up all 3 monitors to work "Big desktop stylee" i would settle for 2 monitors working in that configuration, i cant get anything to work! i have set it up in the ati control centre only to have the settings ignored after the restart.

 i have tried settings in the aticonfig command line but all that ever works is a cloned desktop on the two identical monitors connected to the 9600 with my secondary monitor set 5mhz over the recommended refresh rate so it blurs....

If anyone can help me i would be more than helpful!!!

THANK YOU!!!

Stu

---

### Post by S15_88 on 2007-08-03
try, sudo dpkg-reconfigure xserver-xorg , i know that will send you on a path to configure your xserver but i have no idea what happens with multiple monitors, i'm quite curious to know what happens!  message me with the details!

Thanks, Alain

---

### Post by mattmole on 2007-08-03
Hi,

Unfortunately I cannot be much help here, but, I have never managed to get my laptop to work with an external monitor and have a large desktop.

I have managed to do it at work using a single, dual headed nvidia card on my office PC, using the nvidia tool twinview. Also I have got it working using two separate graphics cards using xinerama.

Not sure about ATI. Try a forum search for xinerama or twinview. There is a thread (I am sure) which deals with ATI, NVidia and xinerama.

Also, try the following link:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

Mattmole

---

### Post by splatcat on 2007-08-03
i am a complete n00b at this....i dont have any idea what i am doing with

sudo dpkg-reconfigure xserver-xorg

i am trying to do a bit of research but still any help would be great..

:) thank you

---

### Post by Hospadar on 2007-08-03
first off, do you have the proprietary drivers installed? I'm not sure if/how this will work with two graphics cards, but I think your best bet would be to get envy and let that do it for you.
first I would go to a text terminal with ctrl-alt-F1, then```
sudo apt-get install envy
envy -t
```
and see how that does for you.
If it seems to work and you can get back into your gui, I would check in your menus and see if ATI has any configuration utilities ( I know that nvidia does) that might ease the multiple monitor setup.

You may also want to start with just the primary card and two monitors, That is probably a very doable setup with some howtos in the ubuntu wiki, but the second card and third monitor may make the whole setup not work.  Hence i would begin the process with that card removed altogether and wait till you get the single-card dual monitor business working.

cheers!

---

