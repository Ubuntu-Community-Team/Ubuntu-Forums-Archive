---
title: "Audio and Video Questions"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by Wmknox on 2005-09-21
I managed to install Ubuntu, and so far everything has run smoothly except for one or two things.

First of all, I've noticed that often, the audio output will get unsynched with my video, but it only seems to happen in some applications, or it's just unnoticeable in others (I've noticed it when using the Flash Plugin for Firefox). I'm unable to give a model name or number at the moment, but it's an integrated Intel sound card, I believe.

Secondly, I've noticed that the highest resolution I seem to be able to get is 1024 by 768 with an nVidia Geforce 4 MX 420. Is this the highest I can get, or are there higher settings?

---

### Post by KingBahamut on 2005-09-22
[QUOTE=Wmknox]I managed to install Ubuntu, and so far everything has run smoothly except for one or two things.

First of all, I've noticed that often, the audio output will get unsynched with my video, but it only seems to happen in some applications, or it's just unnoticeable in others (I've noticed it when using the Flash Plugin for Firefox). I'm unable to give a model name or number at the moment, but it's an integrated Intel sound card, I believe.

Secondly, I've noticed that the highest resolution I seem to be able to get is 1024 by 768 with an nVidia Geforce 4 MX 420. Is this the highest I can get, or are there higher settings?[/QUOTE]
 Are you using the nvidia Drivers with respect to the system itself. 

apt-get install nvidia-glx nvidia-settings

then

nvidia-glx-config enable 

------------------------------

That all be said, If you still experience the problem with respect to resolution, you can go in and edit your xorg.conf file directly to reflect the resolution settings you want. 

sudo nano /etc/X11/xorg.conf 

Near the bottom youll find the depth and resolution entries. Just modify on that level to the resolution you want....if it doesnt jive it wont.

---

