---
title: "[SOLVED] No Internet, no mp3s, surely not!!!"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by johnthemong on 2007-06-03
I'm new to Ubuntu (infact new to all linux distros) and really really want to be able to play my MP3s. However, it seems there is a codec missing (easy to sort out in windows) and I have not internet connection at my linux pc (wifi issues that I will tackle one day if I ever feel brave). Can anyone explain to me (in child speak) exactly how I make ubunto7.04 play my mp3s.

If possible, I would also like to know if I can play my various video files, idealy with VLC which I thought was included but I can't find it.

---

### Post by Lord Illidan on 2007-06-03
First, give us details of your hardware, your Ubuntu version, and your wifi card and network.

In Ubuntu, mp3 codecs are not included for legal reasons, but in Feisty (7.04) they are very easily installed, however, you need an internet connection.

So first, we'll solve your internet connection. Also, vlc is not included in the main distros, it is in the central repository (a "server" full of programs) - again, you need the internet.

---

### Post by rickycodie on 2007-06-03
good news is that it's easy bad news is that you need to get to the internet. the easiest way to get the codecs is to install automatix2, but first the internet is needed. if you can get to it on a different computer, then great, save a a .deb file and it will be very easy to install. just double click it and follow the wizard.

why do you not have internet?

---

### Post by Hendrixski on 2007-06-03
> **Lord Illidan said:**
> In Ubuntu, mp3 codecs are not included for legal reasons, but in Feisty (7.04) they are very easily installed, however, you need an internet connection.


Are those codecs included in windows either?  I thought you had to download them from some microsoft website.

But yeah, installing mp3 codecs on Ubuntu is easy!  When you try to play an mp3 it asks you if you would like to install the codecs.  But, again, you'd need the internet.

The internet works out of the box in most cases.  If your internet provider requres you to put in a password, then somewhere in the System menu there's a networking option that you can supply the password.  First check that the cables are all plugged in, or that it's connecting to the wireless (there's a little network indicator on the top right hand corner of your screen)


Most importantly.  Welcome to the UBUNTU community.  Don't be affriad to come here (the forums) for answers, that's what we're here for because at one point someone answered our questions for us.  And eventually, you'll  be here answering peoples questions too because you'll love Ubuntu that much.  We do.  :-)

---

### Post by annda on 2007-06-03
well, you need to get the codes from the internet - you can use another system or computer and download the packages from

packages.ubuntu.com

to have all multimedia enabled you will need those:

gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll flashplugin-nonfree gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs

only gstreamer codecs are needed for mp3. burn or save them to a flash disk and double-click on the packages in ubuntu to install.

you can do the same with vlc.

---

### Post by johnthemong on 2007-06-07
Thanks for all the advice folks. I'm going to get those packages downloaded and save them to my usb stick soon. Then I can install them the next time I have a day in my shed. That's where my linux box is at the moment and I can't run any perminant cables to it so not easy connection to my existing windows lan. Also no access to the wireless lan because I can't figure all this building your own code thing the relevent driver supplier has.

 I will get there, especially with more time and all your help. I think i'm going to need it. Meanwhile i'll download those packages I need and see if I can run them. Then I'll start and see if I can tackle the problem with the box not recognising the wifi card I put in it. I guess I could post the cards maker and chipset to this post as well. Does anybody know if you can set this forum to forward replies to your email inbox? So much to learn, such a short life.

Cheers

---

### Post by forestpixie on 2007-06-07
re forward replies

thread tools at beginning of thread, subscribe and when asked get email notification

good luck with the wireless card and welcome
:)

---

