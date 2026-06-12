---
title: "Media Player for Ubuntu 7.04"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by MetalheadGautham on 2007-06-17
I am a new user of ubuntu; I installed it only 10 hours back:popcorn:.

I noticed that it can't playback many media formats. But I cant access the net via ubuntu. So are there any .deb packages of the following ?

1. VLC Media Player
2. Xine - Kaffine(or one as good as it)
3.MPlayer - SMPlayer

---

### Post by dptxp on 2007-06-17
Can you access net or not ?

If yes, click on add/remove in applications, choose "all available applications" on top right of add/remove window,
select the first two sets of gstreamer codecs in audio/video.

---

### Post by starcraft.man on 2007-06-17
> **MetalheadGautham said:**
> I am a new user of ubuntu; I installed it only 10 hours back:popcorn:.

I noticed that it can't playback many media formats. But I cant access the net via ubuntu. So are there any .deb packages of the following ?

1. VLC Media Player
2. Xine - Kaffine(or one as good as it)
3.MPlayer - SMPlayer

Ummm, why can't you get access to the net? Ubuntu is very much based on decent net access all the time... for installing new programs, updates, and some program functionality is based on net access. If your situation simply prevents you from getting online, you may want to look at another distro... IMO Ubuntu gets very inconvenient without the net.

---

### Post by MetalheadGautham on 2007-06-17
its because I have to COMPILE the driver for my modem... I don't know how to do it even after looking at the instructions in its driver CD....

---

### Post by Lord Illidan on 2007-06-17
What modem? If I were you I'd get the net working first.

---

### Post by ukripper on 2007-06-17
> **MetalheadGautham said:**
> its because I have to COMPILE the driver for my modem... I don't know how to do it even after looking at the instructions in its driver CD....

Well mate we need to know about your modem first to help you. 

Type this command in terminal:

```
sudo lspci | grep Modem
```

and paste your output here

---

### Post by MetalheadGautham on 2007-06-17
I use HUAWEI SmaerAX MT882 modem.



If this helps, then...


I live in India

I have BSNL DataOne Broadband connection, the Rs 500 scheme.

(Unless you are from India, it may not help you much)


Getting back to topic: where are the deb packages?????

---

### Post by MetalheadGautham on 2007-06-17
> **ukripper said:**
> Well mate we need to know about your modem first to help you. 

Type this command in terminal:

```
sudo lspci
```

and paste your output here

do you realise that I must save this page, restart, go to ubuntu then go through the steps?:-k

---

### Post by rajeev1204 on 2007-06-17
U dont have to compile anything for the bsnl router . 

Just follow these instructions         [http://www.ubuntu-in.org/wiki/Broadband_Howto#Prerequisite](http://www.ubuntu-in.org/wiki/Broadband_Howto#Prerequisite)

---

### Post by steveneddy on 2007-06-17
To answer the question as I see it, after you get your internet connection going, you can DL VLC, or any of the of the others, from Synaptic and it will install itself.

I prefer VLC because it seems to less resource intensive, but I like some of the options in Totem when playing DVD's, although I still use VLC for DVD playback.

---

### Post by TyPhoon101 on 2007-06-18
MetalheadGautham, i am also from india using bsnl 900 UL.. i am using the same modem ;) now why do you need to compile driver for ? is it because you are using usb interface to connect to net.? if so get it [http://www.calcuttatelephones.com/dataoneinstall/linux.zip](http://www.calcuttatelephones.com/dataoneinstall/linux.zip)

but i would advise you to get yourself a decent lan card. it will be so much better:D

---

### Post by TyPhoon101 on 2007-06-18
for movie watching part, download automatix and install all the codecs  and use smplayer it is so much better.:)

---

