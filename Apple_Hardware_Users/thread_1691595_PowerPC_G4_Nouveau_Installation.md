---
title: "PowerPC G4 Nouveau Installation???"
date: 2011-02-20
forum: Apple Hardware Users
---

### Post by aaronpc on 2011-02-20
Hi, I just installed Ubuntu 10.10 on an old iMAc, 1.25 GHz PowerPC G4, 768 MB DDR SDRAM, with an nVidia GeForce FX 5200 (AGP). 

And I installed xserver-xorg-video-nouveau, but I don't have any video acceleration. It is stuck in VESA mode and xorg.conf does not exist. Everything else seems to be working fine.

Can someone please tell me the correct steps to get Nouveau working properly? I would appreciate it. Thanks.

---

### Post by linuxopjemac on 2011-02-20
You need a working xorg.conf file for your type of Mac:

wget [http://mac.linux.be/files/xorg/imac8.txt](http://mac.linux.be/files/xorg/imac8.txt)
sudo mv imac8.txt /etc/X11/xorg.conf

This is the nv driver, which should always work. If you want to try nouveau, change 'nv' into 'nouveau'

---

### Post by aaronpc on 2011-02-21
Downloading the txt file worked immediately, but I got a 'no such file or directory' message when trying to move it to /etc/x11/xorg.conf. 

Is there something I can do to create the appropriate directory?

---

### Post by aaronpc on 2011-02-21
Btw, I tried this and it didn't work either:
[http://ubuntuforums.org/showthread.php?t=1493835](http://ubuntuforums.org/showthread.php?t=1493835)

Any help would be greatly appreciated. Thanks!

---

### Post by linuxopjemac on 2011-02-21
you guys never really read what I say:
```
sudo mv imac8.txt /etc/X11/xorg.conf

```
X11 is with a capital X

---

### Post by aaronpc on 2011-02-21
Thanks. I used the capital X, but now when I re-start my computer, it goes straight to tty mode and I cannot get out of it. Any idea of what might be happening?

---

### Post by linuxopjemac on 2011-02-21
don't know, login, then:
```
sudo /etc/init.d/gdm start
```

---

### Post by aaronpc on 2011-02-21
When I did that it said: 
> Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start gdm

When I tried running these, I get the message: "start: Job is already running: gdm" yet I am definitely in tty mode and cannot get out. 

As soon as I moved imac8.txt to the xorg.conf file this happened.

---

### Post by linuxopjemac on 2011-02-21
CTRL-ALT-F7 or CTRL-ALT-F8, not sure

---

### Post by aaronpc on 2011-02-21
Totally stuck on a black screen when I used those commands. Tried several times to restart, but it just takes me to a black screen (tty). Can't load Ubuntu. Oh well.....thanks anyway.

---

### Post by linuxopjemac on 2011-02-21
can you post output of
```
cat /var/log/Xorg.0.log
```
please ?

---

### Post by aaronpc on 2011-02-21
Sure...I can't type everything, because it is too long, but there is a long list of GeForce and Quadro model types followed by this:

(--) NV: using VT number 7
(EE) NV: Kernel modesetting driver in use, refusing to load
(EE) NV: No devices detected.

Fatal server error: no screens found

---

### Post by linuxopjemac on 2011-02-21
can you change the driver "nv" into "nouveau" ?

```
sudo nano /etc/X11/xorg.conf
```

after editing
CTRL-X and "y" to save

---

### Post by linuxopjemac on 2011-02-21
of courser after editing this file:
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

---

### Post by linuxopjemac on 2011-02-21
of course after editing this file:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by aaronpc on 2011-02-21
Hi. That worked! I'm out of the tty mode and back into normalcy. I still have a lot of issues that need fixing concerning my ability to play video and move windows around without that jerkyness and the trailing effect. Not sure why that is happening. 

Ok...thanks again for your help. I'm off to bed...

---

### Post by linuxopjemac on 2011-02-21
great that it worked for you and good night...

---

### Post by tora201 on 2011-02-26
linuxopjemac,

Hi, just to clarify: if I help Aaron reinstall Maverick and apply the xorg.conf (from the link you provided), then all will be OK? 

I know that the xorg.conf file link you provide contains the information to initialize the Nvidia driver, but is it actually there in Maverick by default? (I suspect it isn't). Then how to I install it? Any links?

Sorry, and thanks very much for your help!

---

### Post by linuxopjemac on 2011-02-26
I am not sure whether the nouveau driver gets installed by default. If it's not installed you might just want to do:
```
sudo apt-get install xserver-xorg-video-nouveau
```

And you need the same xorg.conf file, but I guess you figured that out by yourself :)

---

### Post by tora201 on 2011-02-26
> **linuxopjemac said:**
> I am not sure whether the nouveau driver gets installed by default. If it's not installed you might just want to do:
```
sudo apt-get install xserver-xorg-video-nouveau
```

And you need the same xorg.conf file, but I guess you figured that out by yourself :)

Hey there linuxopjemac. Yeah, I installed Nouveau, but am confused. why then does the Xorg mention "NV" ?  Is that referring to Nouveau? Or? And, another thing: will this give full video acceleration? 

Sorry for all the questions.

---

### Post by linuxopjemac on 2011-02-26
In the xorg.conf file, if you want to use nouveau instead of nv, you have to change 'nv' into 'nouveau'.

---

### Post by tora201 on 2011-02-26
That, I understand. But then, why install  xserver-xorg-video-nouveau?
That was why I asked. I thought, "NV" = Nvidia. Isn't it better than Nouveau? Then, why use Nouveau? Why not just use the original xorg you posted the link to, and forget about Nouveau?
Does "NV" give acceleration? Sorry for all the questions....

---

### Post by linuxopjemac on 2011-02-26
nouveau is the accelerated driver, nv is the older driver without acceleration. For nouveau to work, you need to have the driver installed.

---

### Post by tora201 on 2011-02-26
Excellent! Thanks so much for your kind help and sorry for the stupid questions. I just wanted to make absolutely sure.  So, we had been so incredibly close in the first place. All we needed was the xorg.conf you provided. Lovely! Looking forward to getting the machine up and running with acceleration.

---

