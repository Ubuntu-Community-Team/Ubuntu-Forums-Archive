---
title: "skype won't work under jaunty 64-bit (MBP 5,1)"
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by Nikos.Alexandris on 2009-05-04
Hi all!

Although I have jaunty installed on my system (MBP 5,1) a week before the official release I just got today trying skype. After some seconds of _only_ hearing the "other side" skype stops to be responsive to almost anything. No sound from the "other side" and written messages are not delivered.

I am unsure if this is related with the soundcard module (music & videos play fine). Anybody else facing this problem?

Kind regards, Nikos

---

### Post by Nikos.Alexandris on 2009-05-13
BUMP-ing

Anyone using skype with latest ALSA?

---

### Post by amd-64 on 2009-08-13
Have you managed to get Skype to work.

---

### Post by Nikos.Alexandris on 2009-08-13
> **amd-64 said:**
> Have you managed to get Skype to work.

Well... not really. Very bad quality... and it breaks/freezes/etc. I (also) have tried the following (without success): 

> The main problem with Pulseaudio and Skype on Fedora 9 (maybe also on other distributions) is stuttering, crackling sound. This stuttering and crackling appears only with Skype - all other applications are working without any problems. We can fix this by changing pulseaudio's resample method and some other settings.
su -
%root_password%
vi /etc/pulse/daemon.conf
Add the following lines at the end of the file:
[B]high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
resample-method = src-sinc-best-quality[/B]

[SIZE="2"]Source: [COLOR="Blue"]http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9[/COLOR][/SIZE]

---

### Post by Nikos.Alexandris on 2009-10-21
BUMP :-?

Anybody that cares to share his working with PULSE skype-configuration?

---

### Post by alexmurray on 2009-10-21
The latest Skype beta works great for me out of the box on my Karmic MBP5,1. I didnt have to configure anything.

---

### Post by Nikos.Alexandris on 2009-10-21
> **alexmurray said:**
> The latest Skype beta works great for me out of the box on my Karmic MBP5,1. I didnt have to configure anything.

It does also under Jaunty. Finally! Thanks Alex!

---

