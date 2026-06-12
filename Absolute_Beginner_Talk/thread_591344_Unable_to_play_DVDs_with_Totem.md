---
title: "Unable to play DVDs with Totem"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by beno4433 on 2007-10-25
I'm a newbie and have just installed Ubuntu version 7.10 on my Dell Deminsion 4550.  Everything seems to work fine except for playing DVDs with Totem.

I've looked through all the documentation on installing multimedia codecs and plugins and have tried many options suggested in this forum and in books.

I've also installed Automatix and downloaded the codecs and plugins from this program.  I got the information from a book called Ubuntu for Non-Geeks.

Anyway, nothing I've tried seems to work.  I can play audio, but whenever I try to play a DVD I get the following message:

"Totem cannot play this mtype of media (DVD) because it does not have the appropriate plugins to be able to read from the disc".

Again, since I'm new to Ubuntu, I'm not sure what technical information I should provide for better assistance.  I'm just hoping someone can provide some suggestions to help me with this situation.

---

### Post by vexorian on 2007-10-25
Normal behaviour would have been : you enter the DVD, totem opens and asks you to download the restricted codecs.

Did you try with any other DVD, could be something about that DVD disk.

---

### Post by beno4433 on 2007-10-25
Yes - I was asked to downlaod the restriced codec when I first put in the DVD.  I thought I downloaded them correctly.  But I still get the message of missing plugins.

Is there anyway to check and make sure I have everthing installed correctly?

---

### Post by SnTholiday on 2007-10-25
> Normal behaviour would have been : you enter the DVD, totem opens and asks you to download the restricted codecs.

This is indeed normal behavior, but it doesn't work. 

My suggestion to the OP is to uninstall Totem and install VLC. VLC has played anything I have thrown at it.

---

### Post by jdfreshwater on 2007-10-25
The problem is that you probably need the libdvdcss files.  You can download them from medibuntu.  [http://www.medibuntu.org/]("http://www.medibuntu.org/")  You need to install this before you can decrypt dvds.  You also need libdvdread and a few others.

---

### Post by roschell on 2007-11-04
You may want to try also this, as I did on Feisty (it may differ for other flavors) after getting message saying cannot play dvd...
[https://help.ubuntu.com/community/MythTV_media_Feisty](https://help.ubuntu.com/community/MythTV_media_Feisty)

---

