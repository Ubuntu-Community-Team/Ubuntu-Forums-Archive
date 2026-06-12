---
title: "Some configuration pointers"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by michael_besselman on 2007-05-04
I have just finished installing Ubuntu and I am happy.  I am just having two issues that I need some advice on.

First, I am looking for an audio player something like iTunes or MediaPlayer.  I want to get some net stations like NPR as well as play my MP3s.  I would like it to have a selection somwhat like MediaPlayer where I can just play from a particular genre or artist or etc.  I was looking through several applications (not all of them because there is a lot), but haven't really seen any that fit.  Any advice on this point would be appriciated.

The other problem I am having is a video setup.  I have searched and searched and can not find the configuration for it.  Admittadly I have only looked in the GUI (I'll break the nasty windows habbits soon I hope).  The actual problem I am having is that when I run a game like KOBO the video is jumpy and for BZFLAG it does not display well at all.  I have a Radeon 9600 video card and a MAG innocision flatscreen monitor.  Any advice on where I can find some information would be helpful.

Thank you

---

### Post by raja on 2007-05-04
Welcome to Ubuntu!
You have plenty of applications to choose from to play your music. You might have looked at rhythmbox already. Everyone is raving about amarok, but the analogous application more native to gnome would be exaile.
```
sudo aptitude install exaile
```
For listening to streaming radio, I would suggest that you try streamtuner - something unlike anything you can see with windows or mac.
I cant help you much with your display problems, but the configuration is all in a file  located at /etc/X11/xorg.conf. Dont meddle with it though, unless you know what you are doing, and even then not before you backup the working version.

---

