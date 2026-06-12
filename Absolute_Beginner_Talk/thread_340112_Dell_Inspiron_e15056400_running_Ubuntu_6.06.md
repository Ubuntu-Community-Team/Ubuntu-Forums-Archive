---
title: "Dell Inspiron e1505/6400 running Ubuntu 6.06"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by alphaakenny1 on 2007-01-16
Hey I just bought a new laptop, the Inspiron e1505/6400 and I was wondering if anybody else who is running this could help me with a few problems.

1.)  How can I make sure that both my processors (Core 2 Duo 7200) are working, so I can have optimum performance.

2.)  I have a widescreen WSXGA+ screen with 1680 x 1050.  I love it, but Ubuntu does not support this so I just have everything stretched making it all look very akward.  I would Like to know how to change this screen resolution.  It does not have to be that high but it would be very nice seeing as how I have paid for it.  I have heard this can be done by installing some ATI drivers but I don't know how to.

3.)  I also need help installing Adobe Flash Player (kinda off topic but help given is much appreciated).

I am pretty new at this but I am not an idiot, so if someone would be able to spare some time on this issue I would be grateful.  If anybody is really interested and capable of helping me, please leave a message, I will provide an aim screenname.  Thank you.

---

### Post by alphaakenny1 on 2007-01-16
For anybody who knows about automatix, can you please explain its importance and how I can  put it on this computer.

---

### Post by geezerone on 2007-01-16
Easiest way to install most programs is by using Automatix2 which will install Adobe Flash Player.

Find it [** here **](http://www.getautomatix.com/)

---

### Post by mbv93 on 2007-01-16
automatix will help you a lot!!  with this you can install adobe flash player and hundreds of other programs click here to see how to install automatix [http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29")

---

### Post by alphaakenny1 on 2007-01-16
Thanks.  But does anybody know how to solve the other problems.

---

### Post by alphaakenny1 on 2007-01-16
Wow.  Thanks a lot for Automatix, its really convenient.

---

### Post by geezerone on 2007-01-16
If you don't have the option for the resolution of 1680x1050 check if it is in the 'xorg.conf' file (located in /etc/X11/).

To update check [** this **](http://www.ubuntuforums.org/showthread.php?t=333173&highlight=xorg.conf)thread, one of many on the subject.

:)

---

### Post by mbv93 on 2007-01-16
no prob. oh yeah and sorry don't know how to solve your resolution problem :(

---

### Post by alphaakenny1 on 2007-01-16
Sorry for sounding like an idiot but I really don't understand how to install this, could you please show me.  Thanks.

---

### Post by mbv93 on 2007-01-16
how to install what?

---

### Post by alphaakenny1 on 2007-01-16
Sorry that was misleading not install but change the "xorg.conf" file.

---

### Post by kbsuperstar on 2007-01-16
You'll have to figure out what chipset your (integrated) graphics card is before finding a way to fix the resolution.

```
lsmod
```

I think that should help you. I have widescreen on my laptop, and someone told me to do that, and then he told me what chipset I have.

Sorry, but I'm a noob, so it probably wasn't much help

---

### Post by geezerone on 2007-01-16
Regarding xorg.conf, double click the file to see if you have the resolution and if not run through the steps following the 'dpkg... ' configuration command I posted previously accepting most of the defaults if I remember correctly.

---

### Post by mbv93 on 2007-01-16
edit the xorg.conf  file with this ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by alphaakenny1 on 2007-01-16
Hey kbsuperstar I have a ATI Mobility Radeon X1400 with 1680 x 1050 resolution what do I do.

---

### Post by alphaakenny1 on 2007-01-16
Hey I did that mbv93 so now what should I do?

---

### Post by arnieboy on 2007-01-16
> **alphaakenny1 said:**
> Hey kbsuperstar I have a ATI Mobility Radeon X1400 with 1680 x 1050 resolution what do I do.

Automatix Bleeder supports a few ATI cards. You can give it a go (I cannot tell you from the top of my head if your card is specifically supported or not. If it isn't supported, AX Bleeder will let you know).
```
sudo apt-get install automatix2bleeder
```
Now run Automatix Bleeder from Applications --> System Tools and install the ATI cards option.

---

### Post by mbv93 on 2007-01-16
pfff well... hmm tht's as far as i can get on that thing i don't know

---

### Post by arnieboy on 2007-01-16
If Bleeder says that it doesn't support your card, try the following howto:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by alphaakenny1 on 2007-01-16
***@***-ubuntu:~$ sudo apt-get install automatix2bleeder
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix2bleeder
***@***-ubuntu:~$

---

### Post by alphaakenny1 on 2007-01-16
Do you know a how to for Ubuntu Drapper?

---

### Post by arnieboy on 2007-01-16
> **alphaakenny1 said:**
> Do you know a how to for Ubuntu Drapper?

yeah Bleeder is only available and supported on Edgy. The Dapper howto can be found here:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by alphaakenny1 on 2007-01-16
I'm trying this but just as I start the second step it says this:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-restricted-modules

---

### Post by arnieboy on 2007-01-16
paste the following (copy and paste in future):
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

---

### Post by alphaakenny1 on 2007-01-16
All right it is downloading right now but how will I be able to change the resolution through this.

---

### Post by arnieboy on 2007-01-16
> **alphaakenny1 said:**
> All right it is downloading right now but how will I be able to change the resolution through this.

This guide is for installing the correct drivers. changing the resolution comes later. read the whole howto carefully.

---

### Post by alphaakenny1 on 2007-01-16
Hey thanks a lot arnieboy, the first set of steps changed my ATI Mobility Radeon X1400 (for anybody else trying this) back to its native resolution.  I didn't have to do anything else.  You just made the money I paid for this worth something.  Thanks.  Also if you know anything on how to install and use Wine I would be very grateful.

---

### Post by arnieboy on 2007-01-16
> **alphaakenny1 said:**
> Hey thanks a lot arnieboy, the first set of steps changed my ATI Mobility Radeon X1400 (for anybody else trying this) back to its native resolution.  I didn't have to do anything else.  You just made the money I paid for this worth something.  Thanks.  Also if you know anything on how to install and use Wine I would be very grateful.

Automatix will install the latest version of wine for you and add the correct repository.

---

### Post by Zaffe on 2007-01-16
> **alphaakenny1 said:**
> 
1.)  How can I make sure that both my processors (Core 2 Duo 7200) are working, so I can have optimum performance.


```
cat /proc/cpuinfo
``` 

U should see the 2 processors and their info.

---

### Post by alphaakenny1 on 2007-01-18
Hey Zaffe I tried that but it only shows it as one processor, I was under the assumption that it would be shown as two different processors.  If this is not okay, please can you tell me how to fix it.

---

### Post by trashjedi on 2007-01-21
EDIT: I solved the problem after a bit more research on the forum, and following instructions more thoroughly...
Found a HOWTO made by someone who had the same specs as me. Very useful.

> **arnieboy said:**
> This guide is for installing the correct drivers. changing the resolution comes later. read the whole howto carefully.

Hello there. I have the same laptop computer as alphaakenny1 : Dell E1505/6400 but I only just installed ubuntu 6.10, and am a newbie on linux. it's my first time ever.
I have the Ati Mobility X1400, and a centrino core duo.
Where is that guide arnieboy talks about? What did you do alphaakenny1?
I have the resolution problem, and a flickering problem on firefox and any other page, when I scroll down the page... very annoying.
What can I do?:( 
Thanks

---

