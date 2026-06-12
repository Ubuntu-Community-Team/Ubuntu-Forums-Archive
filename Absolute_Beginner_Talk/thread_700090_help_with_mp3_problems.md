---
title: "help with mp3 problems"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by giovanni90 on 2008-02-18
Hi guys, I'm new at linux and I've just installed it. I've got to say it, it's a pretty good darn operating system. Anyway, I've got this small problem. When I try to play my mp3's, dvd's, etc... it says that I have to download codecs in order to make it play. So, I did download and install the codecs for audio and video. But, when I go to install my audio codecs it says this "Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."
So, what do i need to do?

---

### Post by corevette on 2008-02-18
go to System -> Administrative -> Synaptic Package Manager
search for: gstreamer0.10-plugins-ugly
now try installing

---

### Post by kaginken on 2008-02-18
You might also fix it by simply installing vlc media player, this thing plays EVERYthing!!

sudo apt-get install vlc

Hope that helps!!  Rock on -:guitar:

---

### Post by wolfen69 on 2008-02-18
applications>accessories>terminal
copy and paste the following:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
then
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 mozilla-mplayer vlc
```
you should then have enough codecs to get started.

---

### Post by ubuntu-freak on 2008-02-19
You may have a currupt apt file which makes Ubuntu think certain packages aren't available for download. You can delete that file and a new one will be generated when you reload/apt-get update.
 
Open the Terminal in Applications>Accessories and paste these commands into it;
 

```
sudo rm /var/lib/apt/lists/partial/*
```

 
and then regenerate it by reloading;
 
```
sudo apt-get update
```
 

Hopefully that will solve your problem. If you have anymore multimedia needs, check out my  [how-to](http://ubuntuforums.org/showthread.php?t=661833). 
 
Nathan

---

### Post by stchman on 2008-02-19
> **giovanni90 said:**
> Hi guys, I'm new at linux and I've just installed it. I've got to say it, it's a pretty good darn operating system. Anyway, I've got this small problem. When I try to play my mp3's, dvd's, etc... it says that I have to download codecs in order to make it play. So, I did download and install the codecs for audio and video. But, when I go to install my audio codecs it says this "Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."
So, what do i need to do?

Follow my tutorials.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This should do you.

---

### Post by giovanni90 on 2008-02-19
Thanks for all the tips and now I can hear my mp3 finally!
Thanks again everybody!

---

### Post by ubuntu-freak on 2008-02-20
> **giovanni90 said:**
> Thanks for all the tips and now I can hear my mp3 finally!
Thanks again everybody!

 
What was the problem then? Did you have a currupt apt list or not?
 
Nathan

---

### Post by giovanni90 on 2008-02-20
i installed vlc and afterwards, i installed the codecs and it worked

---

