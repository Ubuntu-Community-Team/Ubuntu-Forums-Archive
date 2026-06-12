---
title: "Need help changing background and setting up internet"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Mo1 on 2007-02-11
I installed a copy of unbuntu, decided to have a play around. I like the GUI and all the nice little folder and icons things and, I have ben using Windows frm Day 1,  However, I have complete zip knowlegde about using this, Installing the right drivers and so on, let alone , trying to change the background picture on my desktop!??. 
I also need help "how to connect to the internet" :cry: . The SO has seemingly installed the drivers for the Modem but, but dosent dial, :-({|= 

Frm Confucious

---

### Post by annda on 2007-02-11
as for the dektop background, right click on your desktop.

as to internet: what is your modem? have you tried searching the forums / googling for that? how are you trying to connect? at what point doesn't it connect? (i assume it's a dialup usb or serial)

---

### Post by alextj on 2007-02-11
First thing you would have to do is to get that connection working, that's for sure.
I have absolutely no experience with dial-up conenctions, so I barely can help here,
but here is a [_Ubuntu Edgy Guide_]("http://ubuntuguide.org/wiki/Ubuntu_Edgy"). It has information on installing drivers, programs and just all kind of guides.
You should check out [_How to configure dialup connections_]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_dialup_connections").

To change desktop background, right click on desktop and select "Change Desktop Background" :)

---

### Post by oilchangeguy on 2007-02-11
even if ubuntu does see your modem you may not be able to connect. for example i doubt any isp's disc will work with linux, so you'll have to know the phone number that you dial into, even then some isp's will not let you create a manual connection AOL for example, you have to use their software (disc). don't know where you live or what you're paying for dial-up. but you may want to consider highspeed, most phone and cable companies have several packages to choose from, many with prices about the same as dial-up. except with a lot more speed, with a low end broadband connection you'll connect at somewhere around 300-500kps, with dial-up you're lucky to get 50kps. so it's time to graduate to a high speed connection.

---

### Post by damu on 2007-02-11
I won't be able to solve your problem of modem. 

As for changing preferences in Ubuntu, go to system/ preferences/
/Desktop background : a window will open with the already available wallpapers. You can add any wallpaper that you downloaded by clicking on the buton "add wallpaper".
/Theme : you can change of theme, or click on the theme details buton to change some part of it only.

For codecs that you need to add to Ubuntu, to have a decent multimedia experience, just download [Automatix for Ubuntu Edgy here]("http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.10_.28Edgy_386.29").

Once you have downloaded this .deb file, double click on it, and it will launch the installation process the same way it would for a .exe on Windows. Automatix will then be available in your menu under Apllications/system tools.

With Automatix you can install the codecs needed for mp3, DVDs,  mplayer plugins for firefox (which will allow you to read videos on the web, etc). I would stick to this with Automatix.
You will probably find anything else that you woud need  in the add/remove section of the menu apllications. You will find most of the softwares proposed by Automatix (including flash) and hundreds of others...enjoy

---

### Post by shareMenaPeace on 2007-02-11
Foa cable adsl modem try

```
pppoeconf
```
and if you done this 

```
pon dsl-provider
```

---

### Post by nickoli_02 on 2007-02-11
If you're on dialup, good luck... Linux dialup support is notoriously bad, though I do believe it's getting better. The reason for this is not the fault of linux, it's because pretty much every dialup modem is different and you need to know the chipset used in it and such (at least, this was my understanding from my attempt of getting dialup to work in linux). It is possible to do it, though, so don't give up. Look for howtos and guides and such. Good luck, and welcome to linux :)

---

### Post by shareMenaPeace on 2007-02-11
Hmm to my experiencing and what i read here there are some modems which are not easy to setzup yet. Like Broadcom and Linksys USB

Dialup in general seems to be not much of a problem i think. Or i just had luck wih my hardware (Intel) :)

---

### Post by nickoli_02 on 2007-02-11
ShareMena, you probably just had good luck ;) Intel is quite good with getting their open source drivers to the linux community. I had a terrible time getting dialup to work with an AOpen dialup modem.

---

