---
title: "Gnome Questions"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by SuperD2000 on 2006-07-13
Greetings Ubuntu World!!!
I have just recently switched from Win XP to Ubuntu onm my IBM Thinkpad T-20.  I have been looking over the programs that come install with Ubuntu and I just had some questions I was hoping tha tyou guys could help me out with.

1) Can I uninstall the Games that come with GNOME? If so how?
2) Can I uninstall the Ekiga Softphone?
3) Can I configure Juice Extractor to rip to MP3s?
4) Is there are program for linux similar to DVD Shrink of DVD decripter?
5) Can I remove Movie player and just leave M Player installed.
6) What is the best download manager for Ubuntu that works with Firefox's Flashget?
7) What is a good antivirus and firewall for ubuntu?
8) Is GAIM skinable?
9) I followed the tutorial on how to install a wireless network card, the network card works, but I was wondering if there is a way to set up network manager to not ask me for my password everytime I boot up.
10) I have an USB adapter for a PS2 controller which I use to play games, will it work with Ubuntu?
11) How do I set un the third mouse button (the scroll button) on my IBM T20?

Thank you all in advance!!!!

---

### Post by Kilz on 2006-07-13
> **SuperD2000 said:**
> Greetings Ubuntu World!!!
I have just recently switched from Win XP to Ubuntu onm my IBM Thinkpad T-20.  I have been looking over the programs that come install with Ubuntu and I just had some questions I was hoping tha tyou guys could help me out with.

1) Can I uninstall the Games that come with GNOME? If so how?
2) Can I uninstall the Ekiga Softphone?
3) Can I configure Juice Extractor to rip to MP3s?
4) Is there are program for linux similar to DVD Shrink of DVD decripter?
5) Can I remove Movie player and just leave M Player installed.
6) What is the best download manager for Ubuntu that works with Firefox's Flashget?
7) What is a good antivirus and firewall for ubuntu?
8) Is GAIM skinable?
9) I followed the tutorial on how to install a wireless network card, the network card works, but I was wondering if there is a way to set up network manager to not ask me for my password everytime I boot up.
10) I have an USB adapter for a PS2 controller which I use to play games, will it work with Ubuntu?
11) How do I set un the third mouse button (the scroll button) on my IBM T20?

Thank you all in advance!!!!
1,2,5) the way to install and uninstall programs in Ubuntu is Synaptic. [Here is a good page]("http://www.monkeyblog.org/ubuntu/installing/") to read that explains all about it, and how to remove things.
3) In juce click Edit, then Preferences. Click on the help tab, scroll down for instructions on how to setup to rip to mp3. You will need to install some things. Read The link above and make sure to [enable extra repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") before trying to install mp3 applications
4)k9copy is good, and in Synaptic.
7)Ubuntu comes with a firewall already, you dont need to manualy change things, but if you really want to there is a program called firestarter in Synaptic that can. Antivirus programs for Linux are a huge waste of time imho. If you install programs with Synaptic the chances of a virus are slim and none.
Maybe someone else can answer the rest as I'm not sure of the answer.

---

### Post by Jansson on 2006-07-15
Hmm, well, I've tried to remove both ekiga and the gome games, but it won't remove them without taking gnome-desktop with it, don't know if it's some whay to go around this...

---

### Post by Nonno Bassotto on 2006-07-15
It will remove ubuntu-desktop, not gnome-desktop. Ubuntu-desktop is a meta package. This means that it contains no software, it is useful just to track dependencies. In particular ubuntu-desktop depends on everything is installed by default, so it will be removed if you uninstall anything. This is safe.

When you upgrade to Edgy, it will be convenient for you to make sure that you have all the software you had at the beginning, because otherwise you may experience problems (it is quite difficult to plan a way to make lots of different systems with different configurations and software upgrade smoothly to a new version of the operating system). At that time, you will only need to install ubuntu-desktop, and it will carry all the dependencies.

By the way, I don't remove software in ubuntu-desktop, because I know I will have to reinstall it some months later. This is quite annoying, but being able to upgrade the operating system has a price.

Finally a word about totem. If it doesn't work well for you try totem-xine instead. If you remove it, you will lose video thumbnails.

---

### Post by mostwanted on 2006-07-15
> **Jansson said:**
> Hmm, well, I've tried to remove both ekiga and the gome games, but it won't remove them without taking gnome-desktop with it, don't know if it's some whay to go around this...

ubuntu-desktop is a meta-package, it just depends on other packages, so removing it is harmless.

---

