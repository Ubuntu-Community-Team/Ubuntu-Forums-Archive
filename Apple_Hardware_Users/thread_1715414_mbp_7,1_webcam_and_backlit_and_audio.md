---
title: "mbp 7,1 webcam and backlit and audio"
date: 2011-03-26
forum: Apple Hardware Users
---

### Post by aldyguy on 2011-03-26
I have success with everything except my webcam, backlit keyboard and my audio. 

Problems:

webcam-audio and video works in cheese but when I try to cam with someone, my camera freezes within seconds. I can hear and see them though. I've installed codecs to get the video to work but I need help solving this. 

backlit keyboard- help! :p

my audio works great except my rear left speaker, I've installed alsamixer and configured everything in there, I can't get that one speaker to work though. Maybe I just need to install another mixer? Would it be a driver issue?

---

### Post by alexmurray on 2011-03-26
I assume you're using Ubuntu 10.10 (Maverick) right? If so you can enable the keyboard backlight by using the packages in [my ppa]("https://launchpad.net/~alexmurray/+archive/ppa").

I got no idea about your webcam issues, sorry. The audio is probably a driver issue - have you checked the [wiki]("https://help.ubuntu.com/community/MacBookPro7-1/Maverick")?

---

### Post by aldyguy on 2011-03-27
yep, it is 10.10 and I followed that to get my machine where it is. It doesn't address the backlit keyboard. I tried to add your ppa but I got this

> sudo add-apt-repositor ppa:alexmurray/ppa
[sudo] password for mac: 
sudo: add-apt-repositor: command not found


this is my first time adding a ppa source

---

### Post by alexmurray on 2011-03-27
You forgot the '**y**' at the end of add-apt-repositor**y** :)

Once you add my ppa it should be enough to run:

```
sudo apt-get update && sudo apt-get upgrade
```

Then reboot and with any luck keyboard backlight should work.

---

### Post by aldyguy on 2011-03-28
Alright, I got that working...I also have problems with my mousepad which I just recently discovered. I have everything installed from the wiki...it over rides the mouse settings that ubuntu comes with no matter what they are. What I dont like is how I cant disable my trackpad when I am typing and I also hate clicking once and accidently pausing a video or something. I'd like to disable the tap to click function.

---

### Post by alexmurray on 2011-03-28
Sounds like you're running the multitouch xorg driver - in general I still prefer synaptics so you could uninstall it and just use the default I guess if you don't like how you can't disable tap to click and the touchpad whilst typing. Personal preference really.

---

### Post by aldyguy on 2011-03-28
There must be a way to change the settings of the xorg... I wish I knew how to configure a file myself.

---

