---
title: "VLC only plays the first chapters on DVDs"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-09-02
Hi again.
So, I've managed to get VLC playing my DVDs. Sort of... When I insert some of my DVDs, VLC only plays some of the chapters. How many chapters it plays varies from DVD to DVD, but it suddenly stops playing when it comes to a given chapter. I.E. I've got an instructions DVD, where VLC only plays the first three lessons. In a Mr.Bean DVD I've got (getting too specific now? :p) It stops playing in the middle of an episode, after playing several other episodes flawlessly.

Can anyone help?

Thanks!
Joakim

---

### Post by InGunsWeTrust on 2007-09-02
Xine is a very good DVD player for Linux and Windows. I would suggest using that over any other DVD player. Other things to check for would be to make sure you have libdvdcss as you can't play content scrambled dvds without it.

---

### Post by Joakim Stokland on 2007-09-03
Thanks for the reply. I was certain I had installed all necessary drivers, but Totem says "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it." when I try to play DVDs. Would you please help me through with this?

Actually I like Totem and want to use it over VLC, but since VLC was the only one working until now...

---

### Post by RomeReactor on 2007-09-03
Hi. To get totem playing DVDs you need to add the medibuntu repositories. From the terminal (Applications->Accessories->Terminal):
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
to add the Medibuntu repositories to your sources.list. Then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
to get the gpg key and update the repositories, and then:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4 w32codecs
```
to install the needed packages. That should give you DVD playback in totem.

---

### Post by Joakim Stokland on 2007-09-03
Well that was plain and straight forward! Thanks a lot!
It seems it was gStreamer i installed, not Xine.
Totem plays DVDs as h... now! Great! Thanks again! :D

Joakim

---

