---
title: "Installing Beta Driver for HVR-1600"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by wasing on 2007-12-31
kk.. so i downloaded the beta drivers for the  WinTV HVR-1600. and the instructions are not really helping me 

these are the instructions

There is a new beta from LinuxTV.org with a Conexant cx23418 driver which supports the Hauppauge WinTV-HVR-1600 card.
The driver is available here:
[http://www.linuxtv.org/hg/~hverkuil/cx18](http://www.linuxtv.org/hg/~hverkuil/cx18)
The easiest way to build it is to get the tar.bz2 archive:
[http://www.linuxtv.org/hg/~hverkuil/cx18/archive/tip.tar.bz2](http://www.linuxtv.org/hg/~hverkuil/cx18/archive/tip.tar.bz2)
Unpack, 'make', 'make install' (as root), 'make unload' (as root) and run 'modprobe cx18'.
There is still a lot of work to be done, in particular there is nosupport for the ATSC stream. What is working is basic MPEG capturing, raw YUV capture and raw PCM capture. Also pretty much all of the controls that were also in ivtv are working with cx18.
The firmware needs to be extracted from the Windows Hauppauge HVR-1600 driver, available here:
[http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip](http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip)
Unzip, then copy the following files to the firmware directory and rename them as follows:
Drivers/Driver18/hcw18apu.rom -> v4l-cx23418-apu.fw Drivers/Driver18/hcw18enc.rom -> v4l-cx23418-cpu.fw Drivers/Driver18/hcw18mlC.rom -> v4l-cx23418-dig.fw

it says to unpack it which i did and then it tells me to "make then Make install"
how do i do this and then from there i also do not know what i am suppose to do.

Thx for the help in advance i've been struggling with getting the card working for over 3 days now.

---

### Post by csadowski on 2008-01-11
Hi,

I'm actually about to try this out, as I have this card.  To make, make install, etc., you need to open up a terminal, cd to the directory you unpacked, and then type make, let it work, type make install (do this as root, so i guess sudo make install), etc.  I'll let you know if I have any luck though.

---

### Post by gusman21 on 2008-01-14
compiling the driver is cake.

i can  cat /dev/video0 > /tmp/test_capture4.mpg
and see and hear the result in mplayer.

tvtime just comes up with no signal

cx18: Invalid argument
cannot open capture device /dev/video0

---

### Post by ctswhole on 2008-02-06
> **gusman21 said:**
> compiling the driver is cake.

i can  cat /dev/video0 > /tmp/test_capture4.mpg
and see and hear the result in mplayer.

tvtime just comes up with no signal

cx18: Invalid argument
cannot open capture device /dev/video0

Ok, I ran the cat /dev/video0 command and was able to see and hear video.  What would be the steps to take to actually watch and record tv now?  I'm having no luck so far.

---

### Post by bdtgp on 2008-02-11
I would like to have an answer for this too.  tvtime doesn't see the card.  Does anyone know if MythTV works or if that is a good application for this purpose?

---

### Post by ctswhole on 2008-02-11
> **bdtgp said:**
> I would like to have an answer for this too.  tvtime doesn't see the card.  Does anyone know if MythTV works or if that is a good application for this purpose?

I was never able to get mythtv to work with this card.  After struggling to get it working for a while, I've finally given up on this card and and will just look to get a different card I guess.:(

---

### Post by kahrytan on 2008-02-12
> from ivtv mailing list


tvtime won't work since the driver doesn't have any I/O streaming API.
Use apps that can do MPEG decoding like mplayer, xine, MythTV, vlc,
etc. instead.



I have verified that mplayer WILL WORK.  I couldn't vlc to work.

---

### Post by gusman21 on 2008-03-24
> **kahrytan said:**
> I have verified that mplayer WILL WORK.  I couldn't vlc to work.

```
 cat /dev/video0 | mplayer - 
```

---

### Post by saedelaere on 2008-04-23
And [here]("http://ubuntuforums.org/showthread.php?t=763698") is a GUI to switch stations and do many more. Mplayer, Kaffeine, Vlc and Xine are supported. 
It should work with HVR-1600, if it does please give me a short note! Thanks

---

### Post by tomeg on 2008-07-12
> **wasing said:**
> kk.. so i downloaded the beta drivers for the  WinTV HVR-1600. and the instructions are not really helping me 

these are the instructions

There is a new beta from LinuxTV.org with a Conexant cx23418 driver which supports the Hauppauge WinTV-HVR-1600 card.
The driver is available here:
[http://www.linuxtv.org/hg/~hverkuil/cx18](http://www.linuxtv.org/hg/~hverkuil/cx18)
The easiest way to build it is to get the tar.bz2 archive:
[http://www.linuxtv.org/hg/~hverkuil/cx18/archive/tip.tar.bz2](http://www.linuxtv.org/hg/~hverkuil/cx18/archive/tip.tar.bz2)
Unpack, 'make', 'make install' (as root), 'make unload' (as root) and run 'modprobe cx18'.
There is still a lot of work to be done, in particular there is nosupport for the ATSC stream. What is working is basic MPEG capturing, raw YUV capture and raw PCM capture. Also pretty much all of the controls that were also in ivtv are working with cx18.
The firmware needs to be extracted from the Windows Hauppauge HVR-1600 driver, available here:
[http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip](http://hauppauge.lightpath.net/software/install_cd/hauppauge_cd_3.4d1.zip)
Unzip, then copy the following files to the firmware directory and rename them as follows:
Drivers/Driver18/hcw18apu.rom -> v4l-cx23418-apu.fw Drivers/Driver18/hcw18enc.rom -> v4l-cx23418-cpu.fw Drivers/Driver18/hcw18mlC.rom -> v4l-cx23418-dig.fw

it says to unpack it which i did and then it tells me to "make then Make install"
how do i do this and then from there i also do not know what i am suppose to do.

Thx for the help in advance i've been struggling with getting the card working for over 3 days now.

I just bought a HVR 1600 hoping that it would be compatible with Hardy Heron, but no luck.  I also ran into this thread and the links above don't work.  I get this error:
[B]Mercurial Repositories
The specified repository "~hverkuil" is unknown, sorry. Please go back to the main repository list page.
powered by
mercurial [/B]

Any help where I can get the driver for the 1600 would be appreciated.

Thanks
Tom

---

### Post by willoconley on 2008-07-13
> **tomeg said:**
> I just bought a HVR 1600 hoping that it would be compatible with Hardy Heron, but no luck.  I also ran into this thread and the links above don't work.  I get this error:
[B]Mercurial Repositories
The specified repository "~hverkuil" is unknown, sorry. Please go back to the main repository list page.
powered by
mercurial [/B]

Any help where I can get the driver for the 1600 would be appreciated.

Thanks
Tom

[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

if you want help getting them installed, check out post 20 [here]("http://ubuntuforums.org/showthread.php?t=813429&highlight=hauppauge+1600&page=2")

---

### Post by tomeg on 2008-07-14
> **willoconley said:**
> [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

if you want help getting them installed, check out post 20 [here]("http://ubuntuforums.org/showthread.php?t=813429&highlight=hauppauge+1600&page=2")

Thanks. I actually found an old Emuzed Maui-III tuner card hoping I'd have better luck.  You wouldn't happen to know where I can get a driver for this would you.  I'm still running Hardy Heron.

thanks
Tom

---

