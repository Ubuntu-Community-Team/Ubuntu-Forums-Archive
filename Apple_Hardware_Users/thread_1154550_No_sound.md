---
title: "No sound ????????"
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by AussieHolden on 2009-05-09
This new version Ubuntu has no sound at all what the hell is going on guys this ain't funny ????????????? :confused:

---

### Post by AussieHolden on 2009-05-10
I know I am not the only one with this issue so why no help in getting it fixed it's driving me nuts not having any sound :mad:

---

### Post by inphektion on 2009-05-10
which mac you on?  most wiki's for the mac have a way to get sound working.

---

### Post by AussieHolden on 2009-05-10
> **inphektion said:**
> which mac you on?  most wiki's for the mac have a way to get sound working.

Apple Intel iMac 24"

---

### Post by khelben1979 on 2009-05-10
Have you tried checking the volume meters through [Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")?

Also, [alsaconf]("http://www.linuxmanpages.com/man8/alsaconf.8.php") is a good program where you can change which default soundchip/soundcard which is supposed to be used by the system. I've read that it's not a part of the Ubuntu Jaunty release, so you might get it elsewhere if you feel you want to try it out.

```
sudo lspci
```
will reveal if the system has more than one soundchip/soundcard. If it only has one of these, then the use of alsaconf might not be the answer.

Getting the alsa source code and compiling it all up and then using an Ubuntu alsa script will definitely solve your problem (if it's not a hardware fault), but until then.. let's hope there's an easier way.

---

### Post by AussieHolden on 2009-05-10
> **khelben1979 said:**
> Have you tried checking the volume meters through [Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")?

Also, [alsaconf]("http://www.linuxmanpages.com/man8/alsaconf.8.php") is a good program where you can change which default soundchip/soundcard which is supposed to be used by the system. I've read that it's not a part of the Ubuntu Jaunty release, so you might get it elsewhere if you feel you want to try it out.

```
sudo lspci
```
will reveal if the system has more than one soundchip/soundcard. If it only has one of these, then the use of alsaconf might not be the answer.

Getting the alsa source code and compiling it all up and then using an Ubuntu alsa script will definitely solve your problem (if it's not a hardware fault), but until then.. let's hope there's an easier way.

Yes checked via Alsamixer all 100%

---

### Post by cyberdork33 on 2009-05-12
Please do not post more than on thread for the same issue. It make support quite difficult.
[http://ubuntuforums.org/showthread.php?t=1154167](http://ubuntuforums.org/showthread.php?t=1154167)

Also, please follow the guide here to properly identify your hardware and find the best documentation:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Unfortunately, the page for iMacs doesn't get updated well, so you may have to do a little searching.

Lastly, if you certainly did have everything working before, and the new version breaks it, you should check for a bug report, and if it doesn't exist, create a new one.

---

### Post by AussieHolden on 2009-05-13
> **cyberdork33 said:**
> Please do not post more than on thread for the same issue. It make support quite difficult.
[http://ubuntuforums.org/showthread.php?t=1154167](http://ubuntuforums.org/showthread.php?t=1154167)

Also, please follow the guide here to properly identify your hardware and find the best documentation:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Unfortunately, the page for iMacs doesn't get updated well, so you may have to do a little searching.

Lastly, if you certainly did have everything working before, and the new version breaks it, you should check for a bug report, and if it doesn't exist, create a new one.

None of that is going to work for me I'm not a programer I have no idea how or were to start all I need is a driver to be installed to make the sound work.

---

### Post by khelben1979 on 2009-05-13
> **AussieHolden said:**
> None of that is going to work for me I'm not a programer I have no idea how or were to start all I need is a driver to be installed to make the sound work.

"All I need is a driver"

Yes! And to know this you need to go through my instructions to be able to take the next step.

---

### Post by cyberdork33 on 2009-05-13
> **AussieHolden said:**
> None of that is going to work for me I'm not a programer I have no idea how or were to start all I need is a driver to be installed to make the sound work.
that has nothing to do with being a programmer.

Not trying to steer you away from Ubuntu or Linux in general necessarily, but if you find these sort of things difficult for you to work around, then maybe Linux is not the right OS for you.

P.S. Unless you get a good Hardware ID from your machine and tell us what it is, we cannot really help you much more.

---

### Post by stream303 on 2009-05-13
> **AussieHolden said:**
> None of that is going to work for me I'm not a programer I have no idea how or were to start all I need is a driver to be installed to make the sound work.

Neither are we for the most part, and as a community are trying to help you.  If we knew the answer off the top of our heads, it would surely be given.

I understand that you are frustrated - but don't hold that against us.  Since we are not sitting at your machine, we can't wave a magic wand to make it all go away. :)

In the meantime, could it be a pulseaudio issue?  If you go into the sound preferences, and change the setting from "Auto Detect" to "ALSA" or one of the other Alsa options and perform the test, do you get any further?

---

### Post by MrJackalope on 2009-05-17
Hi, ty stream 303 that helped with me.  I have a Powerpc G4. I went to System -> preferences -> sound and changed the devices from autodect to powermac snapper.  For those that this post may help.

---

### Post by MrJackalope on 2009-05-17
It is kind of quiet and important to turn the levels up really high as well.

---

