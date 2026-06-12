---
title: "Major Help!!! Confusion!!"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by RetroDemon on 2007-09-18
Ok, while i was installing Ubuntu, i accidently told it to Partition 100% of my drive. I had Windows XP. So now all i have is Ubuntu 7.04 i386. I figured out some stuff already but heres where im stuck. 

Some DVD's play but i can only hear it, when i switch to full screen, i see the video for 1 second then its black again. 

I cant really install anything execpt from the add/remove thing. My Games wont install, things i Download from the internet dont install. 

Those are the two big things right now. Please help.

---

### Post by RetroDemon on 2007-09-18
help anyone!?!?!

---

### Post by arkara on 2007-09-18
linux wont recognise any .exe files
thats why your games dont work although you can use a program called wine

in order to play dvd you must install the appropriate codecs. when you tried to playback the dvd ubuntu promps you to the codecs needed form the add/remove utility. i think there is a problem with locked dvds
they dont play DRM as you can see
for the sound issue.. check the sound level its on the top right. on gnome and on the bottom right for kde see if the sound is muted

the codecs are cstreamer or gsteamer i'm not really sure search for them on the add/remove utility

---

### Post by kelnage on 2007-09-18
Okay, firstly, your two problems:

If you are only getting this problem when you try to watch DVDs and not normal videos, you'll need to install libdvdcss. There is a guide to doing this here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

When it comes to downloading things from the Internet and installing games, you are probably trying to download/install Windows programs. Unfortunately, Ubuntu cannot natively run Windows programs. Now, I would normally recommend trying to install a program called Wine, which can handle Windows programs for Linux, however, if you are trying to play games (especially recently released games), Wine probably won't be able to handle them.

Honestly, I'd recommend reinstalling Windows (your computer supplier should have included a Windows install disk... I hope) and then trying to install Ubuntu again, this time making sure you don't overwrite the whole disk, so you can try it out.

---

### Post by RetroDemon on 2007-09-18
thanks, wine did help, with that problem, now im just trying to find the codec for the dvd player

---

### Post by Mud.Knee.Havoc on 2007-09-18
This link will be very useful: [UbuntuGuide.org]("http://ubuntuguide.org/wiki/Ubuntu_Feisty").  Just take a scan through it and see what interests you. 

For example, there's a little section entitled [How_to_install_DVD_playback_capability]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_DVD_playback_capability")

If you want to install programs, don't forget that "stuff you find on the internet" that is written for the Windows operating system won't work on Linux (unless you use wine, as you're already getting familiar with).  You can go to sites like getdeb.net and see what kinds of software you can download, or take a look through the Synaptic Package Manager (which lets you install thousands of programs with a click or two!!).  It's in your System -> Administration menu (or at least it is for me... but I'm using a modified Ubuntu called Mint).

---

### Post by BLTicklemonster on 2007-09-18
Wow, big oopsy you got going there, but don't worry, you can watch dvds and have fun playing a lot of games, you just need to look at what games you want to play, then see if the program wine will play them. 

Yeah, it will take a little while to figure out which games work, but have fun with the learning experience, and make the best of it.

Getting dvds to play... you have to install certain codecs and all, and I honestly don't remember where you get them and all, but someone will happen by and get all that info for you.

OR, if you really want windows back, can't live without it, etc, you "could" reinstall it and make the partition for it to be only half the space on your hard drive, then once it's installed, go install ubuntu again, and just dual boot.

---

### Post by hamishw on 2007-09-20
The Desktop effects have a major effect on playing DVDs or watching any video i.e. youtube etc. You need to turn them off to make sure that you will be able to see the video. (and, as everyone else has said, install the correct codecs). Install VLC media player using add/remove or synaptic package manager, this app will play EVERYTHING.
I too managed to overwrite windows while messing with Ubuntu. I coped and now would NOT go back. That was about 6 months ago.
Hope this helps,
H2H
Hamish

---

### Post by hyper_ch on 2007-09-20
> **hamishw said:**
> Install VLC media player using add/remove or synaptic package manager, this app will play EVERYTHING.
Not everything but close to it... it has some troubles with rmvb files ;)

---

