---
title: "Ububtu as Jukebox"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by EdKranich on 2006-11-11
Please bear with me here:

I am new to Ubuntu, I installed version 5.10 on a PC and I would like to use it as a music jukebox. I also have a PC running Windows Media Center 2005. What I would like to do (I don't have a network or wireless internet, just one cable modem on the 
WMC2005 PC)is move my music from iTunes to the Ubuntu PC using my iPod as removable drive. The Ubuntu does not have internet, so this brings me to a few questions:

1) What program is best for playing music on Ubuntu 5.10

2) Will any codecs be required to play .m4a files, .m4p files, and .mp3 files?

3) Is it possible to download all of the neccessary components onto my Windows PC, drag them onto my iPod, and plop them onto the Ubuntu and install with no problem?


Apologies for the lengthyness, but I'd like to get all my info out. Help would be very very much appreciated. Thank you.

---

### Post by IYY on 2006-11-11
> 1) What program is best for playing music on Ubuntu 5.10

Depends on the style you prefer. If you like the iTunes organization style, your best bet will be Banshee (another alternative is Rhythmbox, which comes installed by default but isn't quite as good.)

If you prefer the Winamp style, you can go with XMMS (lightweight, but a bit ugly) or Beep Media Player.

If you like the command line, mocp is a good choice.

Many users also claim that KDE's Amarok has an excellent organization model, but I've never personally tried it.
> 
2) Will any codecs be required to play .m4a files, .m4p files, and .mp3 files?

Yes.

> 3) Is it possible to download all of the neccessary components onto my Windows PC, drag them onto my iPod, and plop them onto the Ubuntu and install with no problem?

Yes, you can get the deb files from packages.ubuntu.com

---

### Post by .t. on 2006-11-11
If you use GNOME but like Amarok, try [Exail](http://www.exaile.org), or [Listen](http://listengnome.free.fr).

Why aren't you using Dapper anyway?

---

### Post by EdKranich on 2006-11-11
Where do I find a Banshee download? Maybe I'm blind but I cant find it.

---

### Post by .t. on 2006-11-11
apt-cache search banshee

---

### Post by EdKranich on 2006-11-11
I don't understand commands. Maybe I should burn my computer.

---

### Post by .t. on 2006-11-11
"apt-cache search" searches the apt database for pacakges. It's easier than opening up synaptic and messing around. You'll learn very quickly, I promise :D. I know I did!

---

### Post by bobbob94 on 2006-11-16
To use commands, just go to applications>accessories>terminal and you can cut and paste the relevant line from the forum to avoid typos. Easy!

Media players are of course a matter of taste, but my favorite is amarok, available through synaptic package manager (system>admin>synaptic). 
If you like iTunes, Songbird is very similar, from  [http://www.songbirdnest.com/download](http://www.songbirdnest.com/download) (for what to do with the downloaded file, see [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) for instructions on how to install from source)

For codecs see [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by lofgren on 2006-11-16
> **EdKranich said:**
> What I would like to do (I don't have a network or wireless internet, just one cable modem on the 
WMC2005 PC)is move my music from iTunes to the Ubuntu PC using my iPod as removable drive. The Ubuntu does not have internet, so this brings me to a few questions:

3) Is it possible to download all of the neccessary components onto my Windows PC, drag them onto my iPod, and plop them onto the Ubuntu and install with no problem?

Perhaps transfer the music via the ipod, but you're going to find it pretty difficult to download all the packages you need via windows and then transfer them to ubuntu via the ipod.

Debian and ubuntu are one of the better (best in my opinion) distributions for installing software/package management..
The reason being, they handle dependencies better than many others. ie: say you want Banshee.
You type 'apt-get install banshee'  - it probably needs a library or two, perhaps has a separate package for a gui interface.
apt-get will download and install them all.

You will probably be able to find the banshee package via windows, but I bet you will have difficulty tracking all of the dependencies for it.

Could you perhaps unplug your windows box and plug in your ubuntu box to connect to the internet? Or better yet, buy a cheap network switch and a couple of cables? Share your internet via "internet connection sharing" in windows..

Much more fun in the long run ;)

---

### Post by hyper_ch on 2006-11-16
You could also use amarok on gnome :)
I used to love Winamp on windows but I think amarak is far superior :)

---

### Post by xpod on 2006-11-16
Mabey using "aptitude" to install things would be a better option.

It deals with depandancies a lot better than "apt-get" apparently

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by lofgren on 2006-11-17
> **xpod said:**
> Mabey using "aptitude" to install things would be a better option.
It deals with depandancies a lot better than "apt-get" apparently
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Yep - agreed.. my main point being to connect to the internet from ubuntu directly. 

Using windows to download packages and then transfer files via iPod will be painful :(

---

