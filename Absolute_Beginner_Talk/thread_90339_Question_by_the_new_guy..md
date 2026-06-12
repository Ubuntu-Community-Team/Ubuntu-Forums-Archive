---
title: "Question by the new guy."
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-11-14
Im quite to new to all of Linux. My first experience was with Mepis but i wasn't sure about it so i came here. I tried Ubuntu on livecd and realised i prefered KDE over GNOME. So i tried Kubuntu and i love it. Anyway enough of my life story :razz: 

I was just wondering there are alot of guides and things round the forums but they are all mostly for Ubuntu. For example installing media codecs, playback, dvd ripping etc. Would i install these the same way as Ubuntu users do? Or would i use a diffrent method to install them in Kubuntu.

Thanks :smile:

---

### Post by arcanistherogue on 2005-11-14
:D good to see another KDE lover :D

Well, I have had the same problem you have had when I started with Kubuntu.  Everything can be done in the same way, but you want to make a couple of tweaks to the instructions.

for instance, when it says "gedit" or references to that app just replace it with "kedit" or "kate".  I prefer the latter, but kedit is much lighter from what I have seen and better for quick fixes.

If you don't have these, do 

```
sudo apt-get install kedit
``` 

in the **Konsole**, which Is the KDE equivalent of the Terminal.  Whenever it says to enter a command, put it in there.

If you have any other problems or need more help, I suggest posting on the Kubuntu 5.10 Desktop Support board.  Great board, and they will help you alot.

---

### Post by Rackerz on 2005-11-14
Thanks for the quick reply and thats cleared alot of things up for me Thankyou! :D. I guess i'll have to start learning about commands a little more now since im more or less hopeless with the Konsole. But i've seen a few tutorials around and bookmarked them for abit of a read. 

Another 2 questions i'd like to ask;

1.) Do i need a /swap partition as i've been looking around and some people have them.
2.) I've noticed some website's look strange (diffrent fonts) i was wondering if i can install all the default fonts that windows comes with to my Kubuntu installation.

Thanks again!

---

### Post by bored2k on 2005-11-14
1. You want one. Remember the Virtual Memory in Windows? It kinda works that way. Utilizes some space in your HDD as if it was actual RAM (more or less).
2. After adding some nice repositories (ask [here]("http://www.ubuntuforums.org/showthread.php?t=89077&highlight=sources.list")) , install the package msttcorefonts using the Synaptic Package Manager found on your System menu.

---

### Post by Rackerz on 2005-11-14
Thanks for the quick reply :). 

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) - are those the respositories i need? Sorry if there not im really new and couldn't really see which one's i needed or what exactly is was asking for. :( 

Thanks!

---

### Post by bored2k on 2005-11-14
```
##Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

##OOo2 Final
deb http://people.ubuntu.com/~doko/OOo2 ./

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```Those are fine on UBuntu Breezy 5.04.

---

### Post by Kapre on 2005-11-14
[QUOTE=bored2k]```
##Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

##OOo2 Final
deb http://people.ubuntu.com/~doko/OOo2 ./

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```Those are fine on UBuntu Breezy 5.04.[/QUOTE]


That's Breezy 5.10.

K

---

### Post by bored2k on 2005-11-14
[QUOTE=Kapre]That's Breezy 5.10.

K[/QUOTE]
That..

---

### Post by aysiu on 2005-11-14
[QUOTE=arcanistherogue]
for instance, when it says "gedit" or references to that app just replace it with "kedit" or "kate".  I prefer the latter, but kedit is much lighter from what I have seen and better for quick fixes.[/QUOTE] I'd recommend against using kate when you're instructed to edit config files as sudo. It does something weird. ```
sudo kwrite
``` tends to work better than ```
sudo kate
```

---

