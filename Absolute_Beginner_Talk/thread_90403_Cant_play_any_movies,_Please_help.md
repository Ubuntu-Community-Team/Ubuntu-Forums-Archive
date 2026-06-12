---
title: "Cant play any movies, Please help"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by generalstoner on 2005-11-14
I am using Kubuntu and wenever I go to play a movie I get an error message.
The error in totem reads
> Totem could not play 'file:///home/darren/Desktop/jo1.wmv'.
There were no decoders found to handle the stream, you might need to install the corresponding plugins
With Kaffeine
> There were no decoders found to handle the stream, you might need to install the corresponding plugins
This is with WMV format, also when I try to load a video through Konqueror It just displays like a play button etc etc.
I can play flashes though so I cant figure out what to do, Please help.

---

### Post by Kapre on 2005-11-14
[QUOTE=generalstoner]I am using Kubuntu and wenever I go to play a movie I get an error message.
The error in totem reads

With Kaffeine

This is with WMV format, also when I try to load a video through Konqueror It just displays like a play button etc etc.
I can play flashes though so I cant figure out what to do, Please help.[/QUOTE]

General -  Please check this [thread]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix") and read the apps that are included. What you require is there.

K

---

### Post by linewb on 2005-11-14
sounds amazing.  is there a version still out there for hoary?  i'm having a terrible time with a similar problem to this poster.  help is greatly appreciated.

---

### Post by generalstoner on 2005-11-14
I installed them and It still isnt working, I think the fact Im using Kubuntu is whats keeping automatix from working, I got it to run but the downloads dont actually do anything.

---

### Post by rlange on 2005-11-14
[QUOTE=Kapre]General -  Please check this [thread]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix") and read the apps that are included. What you require is there.

K[/QUOTE]

from above thread:


Kubuntu: Users can test this script on Kubuntu (some users have reported problems on Kubuntu) but they need to install a few deps (which DO NOT come preinstalled with kubuntu) to make this script work. To install these deps do the following from terminal:
Code:

sudo apt-get install zenity gksu gnome-terminal

I have not tested Automatix on Kubuntu, and as it appears, I will have to rewrite a large fraction of Automatix if I want to port it to Kubuntu. As u must have noticed, most of the packages on Automatix are Gnome (Ubuntu) based and will take 100 MB downloads on Kubuntu to make them work fully. I dont use KDE myself but I do plan to port Automatix to Kubuntu (KDE) sometime in the future. Again, if it works for u on Kubuntu, well and good. if it doesnt, I am sorry but I cant help u right now.

---

### Post by generalstoner on 2005-11-15
I already did all that and it still doesnt work.

---

### Post by btdown on 2005-11-15
Yeah my totem doesnt play wmv files either, even though I know i have w32codecs installed, and , I believe, all the gstreamer stuff....

---

### Post by sjh on 2005-11-15
You don't say if you are using totem-gstreamer or totem-xine.  I spent the better part of a day trying to get totem-gstreamer working and getting the same errors.  I followed some advice I read on a few other threads and told Synaptic to install totem-xine and now I can watch dvd's and news videos from the BBC (which I think are .wmvs but I don't have an actual .wmv file to test).

If you are using totem-xine then just consider this post as noise.

SJH

---

### Post by kruz on 2005-11-15
soiunds like ur a new user
are you sure all those packages installed?
did u in-tick the sources.list file to get apt-get to work?

---

