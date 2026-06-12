---
title: "MultyMedia Problem !!"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Janoubie on 2006-11-03
hi all .. this is the frist time work on linux .. really it's perfect than other .. but when i'm touch the world of linux by UBUTNU :cool: .. i have a small problem .. mp3 not work at all .. really .. i tried Amarok 1.4 but not work .. and trid to read some topic about this problem but not solve .. also real player .. the same .. 
MY os ubunto 6.10
My language Arabic but interface is English and everything
.. :D

Just second .. when i open Mp3 songs by amarok come this note " MP3  support now installed you will need to restart amaork "

and i tried restart many times but still appear and not work

---

### Post by Belgatom on 2006-11-03
MP3 and Divx (and some other codecs) are not standard available in Ubuntu. 

You can install these manually or you can chose to install them through an easier interface. 

[Easyubuntu]("http://easyubuntu.freecontrib.org/") or [Automatix]("http://www.getautomatix.com/") provide you with this interface. It's all just point - click and wait. Normally after the install, all should work properly. 

Good luck. And come back if any other problems pop up.

---

### Post by seshomaru samma on 2006-11-03
Welcome to Linux
To play MP3 files you need to install some codecs.

The best way would be using easyubuntu or automatix as the post above me suggested

another way is to
paste this command into a terminal (application>accessories>terminal):
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```

you will need to log out and log in again 


This would only work if you enabled the 'extra repositories'
If you don't know how to do that I can help you but first please tell us what version of Ubuntu did you install ? Dapper or Edgy?

---

### Post by SunnyRabbiera on 2006-11-03
and for the total newbie there is always automatix:
[here]("http://www.getautomatix.com/")

and there is synaptic too.

---

### Post by Janoubie on 2006-11-03
thanks ...
but Problem Is Begger ? as i think ..
let me explain :
mouse index very heavy and no sound .. I tried to solve it by my self but i can't .. I'm use now xp OS to write this topic
.. thank you agine and nice somebody help you in short time and I'm sure linux better than all os's but more time to understand ..
---
XP now updating itself .. 1h30m to complete hhhhhhh bad OS .. GO hell MR XP OS

---

### Post by Janoubie on 2006-11-03
Finally .............................>> Solved
I'm going To Automatix website and Doing a small steps and finally works .. really very easy .. thnk you all .. ..

---

