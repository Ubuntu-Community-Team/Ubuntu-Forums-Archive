---
title: "MP3 and other helps!"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by tunbakyu on 2005-09-12
I just started using Ubuntu yeterday night. I am completely new in this environment, so if I ask any stupid questions, please do forgive me.

1. I would like to know how to listen to mp3 files from my XP partition or via LAN connecting to my cousin's FC4 and XP!

2. I would also like to watch some movies with extension of ".avi" or any other sorts of file extensions.

3. How to configure dial-up connection?? what is dial-prefix??

Please help me..and i m really sorry to disturb! :(

---

### Post by Perfect Storm on 2005-09-12
I can answer on question number 2, I run pure linux on cable so I can't help you there, perhaps another user(s) can.

First: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
second: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)
third: [http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

Perhaps you should look for dial here: [http://ubuntuguide.org/#configuredialupconnections](http://ubuntuguide.org/#configuredialupconnections)

---

### Post by tunbakyu on 2005-09-12
Thank you for your help, i will try what u have suggested as soon as i go back home.  I have downloaded that page to try it at home! thanx!  :razz:

---

### Post by tunbakyu on 2005-09-12
I did as u have told AI, but there are alot of errors. I just cannot do it! i tried running as u have asked me to do it! but still i cannot do it! HELP!! If i still cannot do it i m going to change to FC4!! :( but i like Ubuntu and i do not want to change! so help!

---

### Post by tunbakyu on 2005-10-01
I am having alot of trouble with Ubuntu! But it all ended up to one thing, i cannot get access to Internet via my dial-up! Does Ubuntu supports Internal Modem? If so How must I configure it?

---

### Post by gw90se on 2005-10-01
[QUOTE=tunbakyu]I am having alot of trouble with Ubuntu! But it all ended up to one thing, i cannot get access to Internet via my dial-up! Does Ubuntu supports Internal Modem? If so How must I configure it?[/QUOTE]

There's another thread going in this section of the forum about this. If it's a winmodem, chances are slim to none. Even then, the ones who have done it say it's a hassle. Can you get your hands on an external modem? When I started checking out Linux a few years back, I was on dial up so I went and found a USR 56K external modem and it worked great.

---

### Post by tunbakyu on 2005-10-01
Umm..It is D-Link. When I opened my Device manager (in XP) it says "Generic SoftK56". Is that a good sign or not?

---

### Post by tunbakyu on 2005-10-02
noone can help me??

---

### Post by Perfect Storm on 2005-10-02
Those link I provided are now invalid, it was before I've noticed that the non-gpl files was removed.

---

### Post by tunbakyu on 2005-10-07
So which means, I really have no hope for that?? :( sad!! Why cant Ubuntu supports Internal Modems?? I mean, most of the other Unix based platforms supports right?
*sigh* I guess I will have to stick with Microsoft then! :(

---

### Post by tseliot on 2005-10-07
[QUOTE=tunbakyu]So which means, I really have no hope for that?? :( sad!! Why cant Ubuntu supports Internal Modems?? I mean, most of the other Unix based platforms supports right?
*sigh* I guess I will have to stick with Microsoft then! :([/QUOTE]
About mp3s you can install (as soon as you get your connection to work) "gstreamer0.8-mad".

If you need to play videos you can follow my guide to get the codecs

[http://ubuntuforums.org/showthread.php?t=70227]("http://ubuntuforums.org/showthread.php?t=70227")

I can't help you with your modem (I have a DSL through Lan connection)

---

### Post by tunbakyu on 2005-10-07
Thanx, I can already play MP3. Had to download from Cyber Cafe. But the problem right now is that, UBUNTU doesn't support my Internal Modem Card. That is why! *sigh* :(

---

### Post by tunbakyu on 2005-10-07
tseliot,

I have read all your howtos! Do u have anything abt Internal Modem??:confused:

---

### Post by Master Shake on 2005-10-07
Here's the problem with internal modems:

Most of them anymmore have most of their functionality being done in windows, and not the firmware of the modem itself.  Therefore, non-windows operating systems have to somehow mimc that funtionality, and that's easier said than done.

In the long run, External modems, even in windows environments, are usually, -- in my experience, because supporting modems is part of my real life job, -- more stable, more user friendly, more  standard.  Plus if you ever have to replace one, it easier than with an internal.

---

### Post by tunbakyu on 2005-10-07
Just curious, I want to know why Fedora Core 4 supports my Internal Modem but why not Ubuntu? Is it because Ubuntu is still beta version? I am sorry...i can be sometime so dumb! Just wants to know!! ;)

---

### Post by chakra_dude on 2005-11-15
i also have these problems. might as well check out these guides... thanks!!!

---

### Post by kruz on 2005-11-15
the beauty of ubuntu is taking time
and configuring it to ur needs
this is basic command line interface
and will help you to do things in the future

error messages?
exact problems? did you get ur mp3's?

btw to mount ur windows check this

i need to make a shells script for all the people that ask me this
but

sudo mkdir /windows
sudo mount /dev/hda1 /windows
cd /windows
dir


im guessings ur windows xp is PROBABLY on partition 1

---

