---
title: "Fedora to Ubuntu..."
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Rice_slayer on 2007-04-11
Hey, I have been using Linux on my PC for some time. My current distro is Fedora Core 6 and I like it, but doesn't suit my needs for multimedia video playback(SUCKS badly at playing videos as audio is always delayed or video  is distorted) and 5.1 just wont work right online... or at all online. Anyways I hear Ubuntu is another very good Distro of Linux and I have a few questions.

1. Will it be easy to set up any applications compared to what Fedora Core offered? 

2. Does it use KDE or Gnome GUI?

3. Is it good with multi-media playback ie, MP3,WMV,AVI,MPG etc?

4. Are there any issues with 5.1 surround sound and Online video sites as Youtube and Google Video?

Thanks and any reply is greatly appreciated!

---

### Post by 3rdalbum on 2007-04-11
1. I'm not entirely sure what you're asking, but it should be as easy as Fedora offers. Package management is pretty similar in Ubuntu as in Fedora, except ours is faster :-)

2. Ubuntu uses Gnome, but KDE and XFCE are available. Actually, there are a lot of desktop environments available in the repositories, but Gnome, KDE and XFCE are the supported ones.

3. Ubuntu Feisty is great with multimedia. Edgy is also good if you download a third-party program called Automatix, which sets up everything for you.

4. There are no issues with Youtube or Google Video. I haven't tried 5.1 surround sound, but Ubuntu should be able to use that too.

---

### Post by sloggerkhan on 2007-04-11
I think the sound issue will be dependant on your sound hardware more than anything else.

---

### Post by Rice_slayer on 2007-04-11
I use a Soundblaster Live! 24 bit sound card. And thanks for the answers! Answered all questions except for sound card one. Might have easier time with Ubuntu. I will reformat my Fedora Hard drive and try out Ubuntu, see how it is. Fedora is not what i needed media wise...

---

### Post by oilchangeguy on 2007-04-11
before you reformat your harddrive. i suggest you create a ubuntu live cd, and run the cd to see how your computer will respond to ubuntu. if everything's a go then you can install it from the live cd.

---

### Post by sloggerkhan on 2007-04-11
I think some creative cards have issues no matter what linux you have. I have a friend who was telling me something about it. Don't remember which creative he had, though.

---

### Post by lamalex on 2007-04-11
I have 5.1 sound working with Creative Audigy ZS Notebook. It didn't work immediately, by default my center and rear (L&R) speakers were muted, I just right clicked on the volume control applet > open volume control > Edit > preferences and enabled the controls for all of the volumes. Now I have great 5.1 audio all the time, much better than windows which was only when it really wanted 5.1

---

### Post by CornMaster on 2007-04-11
I'd like to comment on 4.

I've had troubles with online videos, but I'm still using 6.06, and I also (finally) realized that it was a flash issue.  Now that Flash 9 is available for Linux, I haven't had any problems.  

I have the occasional sound issue, as I haven't bothered to configure my sound system, but all in all it has been a good experience.  I do not have 5.1 however, and cannot comment on that.

---

### Post by Rice_slayer on 2007-04-12
Ok I have everything prepped for install, just need to go out and get CD's for it. Just 1 more question, for installing things with fedora I used yum, what is Ubuntu's thing like yum and how does it work compared to yum? Yum DID get me mad at times...

---

### Post by cub on 2007-04-12
> **Rice_slayer said:**
> Ok I have everything prepped for install, just need to go out and get CD's for it. Just 1 more question, for installing things with fedora I used yum, what is Ubuntu's thing like yum and how does it work compared to yum? Yum DID get me mad at times...
I went from Fedora to Ubuntu as well and the hardest part for me was to change from yum to apt. I liked yum, I'm getting the hang of apt-get but usually use the "Synaptic Package Manager" to find stuff.

The answer to your question is that apt-get is the similar thing to yum.

---

### Post by Maestro23 on 2007-04-12
> **Rice_slayer said:**
> Ok I have everything prepped for install, just need to go out and get CD's for it. Just 1 more question, for installing things with fedora I used yum, what is Ubuntu's thing like yum and how does it work compared to yum? Yum DID get me mad at times...

Synaptic Package manager: [https://help.ubuntu.com/community/Synaptic?highlight=%28synaptic%29](https://help.ubuntu.com/community/Synaptic?highlight=%28synaptic%29)

Installing Software in Ubuntu:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by Henry Rayker on 2007-04-12
I actually made the reverse switch. I went from Ubuntu to Fedora 7. I felt that software management was easier in fedora (yum does search, install, remove etc. wherease apt-get is more for getting/installing and removing -- apt-cache is more for searching)

Additionally, Fedora 7 (despite being in a beta currently) is more stable (than either Edgy or Dapper, even, which was supposed to be the stable release), has MUCH better wireless support (IE, every wireless card I've thrown at it has needed, at most, firmware--in Ubuntu, it was drivers and firmware; even then the wireless configuration tools had troubles and needed to be reinstalled) and in my experiences, the package management has been a lot faster (unless you rely on the GUI, in which case, Fedora does fall behind Ubuntu in this regard).

If you have the time, I'd give F7 a shot, as well as Ubuntu Feisty. While the transition may not be too rough, your issue could be resolved in F7, you never know...

---

### Post by juantovarm on 2007-04-12
Try running the live cd first, try it, see if you like it, before formatting your drive.

I have had no problem with multimedia, of cours, after installing the codecs, you should check this out:

for windows media and real player:

[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

Everything else regarding multimedia :

[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

The Sinaptic Package Manager is excellent. The Add/Remove option in the Applications is an excellent graphical interface to add and remove programs, and of course there is always apt-get in the terminal.

Enjoy your Ubuntu (GNOME), or Kubuntu (KDE) or Xubuntu (XFCE)

---

### Post by cub on 2007-04-12
> **Henry Rayker said:**
> , has MUCH better wireless support (IE, every wireless card I've thrown at it has needed, at most, firmware--in Ubuntu, it was drivers and firmware; even then the wireless configuration tools had troubles and needed to be reinstalled) and in my experiences, the package management has been a lot faster (unless you rely on the GUI, in which case, Fedora does fall behind Ubuntu in this regard).
Funny, in my case it was the exact opposite. I worked long and hard with my wireless in Fedora but never got it to work, but it works in Ubuntu. :)

---

### Post by Henry Rayker on 2007-04-12
> **cub said:**
> Funny, in my case it was the exact opposite. I worked long and hard with my wireless in Fedora but never got it to work, but it works in Ubuntu. :)

Weird. Which Fedora release were you working with? What hardware was it? My particular case was with the Ralink rt2500usb and rt61 laptop cards. My girlfriend's desktop has a full-size pci card based on the rt61 chipset that works fine with Ubuntu...however, none of the ralink cards were supported in the NetworkManager-applet unless I recompiled not only that, but also my drivers after every kernel update. Under Fedora, I didn't even have to install the applet or the drivers.

---

### Post by Rice_slayer on 2007-04-12
Well i have it installed and its great, but my surround sound doesn't work :(. Only subwoofer+ 2 front speakers work. I use a SoundBlaster Live! 24 bit sound card, anyone know how to get 5.1 working on it. This is THE worst thing with Linux its VERY hard to get 5.1 working at all :(.

---

