---
title: "Problems viewing videos - Ubuntu 7.10"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Bandarra on 2007-11-21
Hi everyone,

This is my first post and although I'm a noob I don't consider myself a total utter noob... lol

Anyway, the problem history:
- One month ago I installed ubuntu 7.04, after some familiarization everything was fine, mp3, and all kinds video formats played brilliantly on totem.
- After finding the Wine concept very nice I installed it and explored it and managed to install and run starcraft and counter strike 1.6.
- They sort of worked but very limited performance (10-15fps) and I noticed that the cpu was working quite hard so I supposed the problem was the graphics card not being properly recognized.
- Digged some info out of forums and others an got to the conclusion that had to "install" X.org, (I know very little about all this stuff but I managed to get it running and performance in the games was improved... a bit.)
- At the same time of the previous point the 7.10 update came on and so I updated it.
- Only after this I noticed that I couldn't play any video file with any player (and I tried loads) sound is fine, image is always the same dark green color.
- The only video that works is internet streaming such as youtube, and I think thats due to using java instead of whatever the rest uses.
- If I had to guess I would say that it's X.org that is badly configured and that is why the poor performance in the games and no video.
- Also when I installed it I did the manual configuration and it was a mess because that lead to not having gnome and when I started the computer I had only a terminal prompt. (I proper freaked out on that one but it was solved "easily" by the advice of people on forums to input some line in the terminal (which I think is autodetect/autoconfigure) x.org and with a reboot the problem was solved. But left me with this other one.

I hope the discription is not too much but I just tried to explain as much as i can/know in order to help people help me.
My problem can be summarizes in not being able to play videos and have poor performance in any graphic-card-required application.

These is the laptop model:
Compaq Presario X1010
ATI Mobility Radeon 9200 (64Mb dedicated) (yes, i've heard that ati's are dodgy on linux... but what can you do)
1.3GHz Centrino
512MB Ram

Thank you very much to who had the trouble to read all this and THANKS even more to who can tell me a possible solution.
Andre

---

### Post by jken146 on 2007-11-21
> - The only video that works is internet streaming such as youtube, and I think thats due to using java instead of whatever the rest uses.
FYI youtube uses Flash.

>  it was solved "easily" by the advice of people on forums to input some line in the terminal (which I think is autodetect/autoconfigure) x.org and with a reboot the problem was solved. But left me with this other one.
I guess you mean
```
sudo dpkg-reconfigure xserver-xorg
```

As for video playback, the first thing I would check is that you have all the right codecs installed.  Things like the ubuntu-restricted-extras package will help you play certain formats.  Go into Applications > Add/Remove and type in 'codec' and you'll probably find something.

I can't really help you with your graphic card problem, I'm afraid.

For wine apps, check out [www.winehq.org](www.winehq.org) to see how well things should work.

Hope this helps and good luck!

---

### Post by Bandarra on 2007-11-21
> **jken146 said:**
> 

I guess you mean
```
sudo dpkg-reconfigure xserver-xorg
```

No, i mean ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` or something of a similar sintax that auto configures x.org.

> **jken146 said:**
> As for video playback, the first thing I would check is that you have all the right codecs installed.  Things like the ubuntu-restricted-extras package will help you play certain formats.  Go into Applications > Add/Remove and type in 'codec' and you'll probably find something.

I can't really help you with your graphic card problem, I'm afraid.

For wine apps, check out [www.winehq.org](www.winehq.org) to see how well things should work.

Hope this helps and good luck!

Of course I know winehq and read much of the help, and I'm only asking these questions on the forum because I couldn't find it anywhere. 
An yes, i have  ubuntu-restricted-extras for a long time now and already had dis install it a install it again many times.

Still got the problem but, thanks for your help anyway

---

### Post by Bigbird999 on 2007-11-21
Install VLC media player.  It  leaves totem and every other windows player for dead and it is available for all platforms.  It will play almost every media file in existance without screwing around trying to find the right codec (it comes with them all)

sudo apt-get vlc will do it for you or search synaptic for vlc and install from there.

Trust me on this!!!

BB

---

### Post by Bandarra on 2007-11-21
Don't need to trust you on it mate, I already have them "all" installed: gxine, totem, mplayer, vlc. etc...
On all the same outcome, sound ok, green image. I'm almost sure that what is wrong with it is the bare base of the graphics on ubuntu. And it is related with x.org or the 7.04->7.10 upgrade.
Almost sure it is x.org badly configured. something stupid like 24bit resolution or something. But I can only have display if it is automatically configures "-phigh", if I try to do it manually (to go back to 16bit for instance) all of it doesn't work because I have to go through all the configuration properly and I must get some tecnical stuff wrong in the process because other than automatic it doesn't work.

I wrecon that if there was a place were i could change from 24 to 16 bit resolution without having to chose anything else it could be the solution, though, i don't know how to do this, and again, might not be the solution.

---

### Post by monte48lowes on 2007-11-21
What graphics card do you have? Are you running compiz? If the answer is something like: Intel and yes... check around to see if there are issues with the graphics card and compiz. I had issues with my Intel graphics and compiz not playing video.

Mike

---

### Post by Bandarra on 2007-11-21
I have an ATI as I said before and yes I'm running compiz which to be very honest I don't know what it is. (sort of overall desktop manager?)

I found a application that shows me my xorg definitions but is display only, no editing/choosing possible. This is what it shows... (wanted to swap my resolution to 16 bit... anyone know how to do it?)

---

### Post by monte48lowes on 2007-11-21
The issue is related to the 'xv' driver I believe. Try this with VLC.

Start VLC. 

From the menu:

Settings > Preferences > Output modules > (check Advanced Option lower right corner) 

Select 'X11 video output' from drop down menu

Click save.

Try and open video with VLC.

Mike

---

### Post by neotasic1 on 2007-11-22
> **Bandarra said:**
> Hi everyone,

This is my first post and although I'm a noob I don't consider myself a total utter noob... lol

Anyway, the problem history:
- One month ago I installed ubuntu 7.04, after some familiarization everything was fine, mp3, and all kinds video formats played brilliantly on totem.
- After finding the Wine concept very nice I installed it and explored it and managed to install and run starcraft and counter strike 1.6.
- They sort of worked but very limited performance (10-15fps) and I noticed that the cpu was working quite hard so I supposed the problem was the graphics card not being properly recognized.
- Digged some info out of forums and others an got to the conclusion that had to "install" X.org, (I know very little about all this stuff but I managed to get it running and performance in the games was improved... a bit.)
- At the same time of the previous point the 7.10 update came on and so I updated it.
- Only after this I noticed that I couldn't play any video file with any player (and I tried loads) sound is fine, image is always the same dark green color.
- The only video that works is internet streaming such as youtube, and I think thats due to using java instead of whatever the rest uses.
- If I had to guess I would say that it's X.org that is badly configured and that is why the poor performance in the games and no video.
- Also when I installed it I did the manual configuration and it was a mess because that lead to not having gnome and when I started the computer I had only a terminal prompt. (I proper freaked out on that one but it was solved "easily" by the advice of people on forums to input some line in the terminal (which I think is autodetect/autoconfigure) x.org and with a reboot the problem was solved. But left me with this other one.

I hope the discription is not too much but I just tried to explain as much as i can/know in order to help people help me.
My problem can be summarizes in not being able to play videos and have poor performance in any graphic-card-required application.

These is the laptop model:
Compaq Presario X1010
ATI Mobility Radeon 9200 (64Mb dedicated) (yes, i've heard that ati's are dodgy on linux... but what can you do)
1.3GHz Centrino
512MB Ram

Thank you very much to who had the trouble to read all this and THANKS even more to who can tell me a possible solution.
Andre


I have an ATI Radeon card in my desktop - 64bit Athlon.  I have never had any problems with this in either Feisty or in Gusty (Did a fresh install about 4 days ago) Everything worked in Feisty after some configuring and learning, however, after new install of Gutsy and reinstallation of restricted codecs etc (following various bits of advice and instructions from official docs and forum posts) Gxine would no longer play DVD's.  I never solved this but came to this post - [http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

I downloaded the file followed the instructions for installing the script and after looking at the contents ran it.  Totem-xine now works flawlessly and it took seconds.  Thanks again mdpalov for this.  I recommend you give it a try, it may help you.  Hope this helps.

---

### Post by Bandarra on 2007-11-22
I feel so stupid...
I didn't do it with VLC because I couldn't find how to activate X11 but did the same with Mplayer and hey presto, it works. Now I have to sort out some other stuff but this is working. Great advice, thanks mike

---

