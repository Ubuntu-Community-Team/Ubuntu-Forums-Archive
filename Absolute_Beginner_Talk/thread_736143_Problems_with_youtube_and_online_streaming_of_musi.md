---
title: "Problems with youtube and online streaming of music/video"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by aachen on 2008-03-26
I am using firefox and opera to view youtube videos and play some music online. but online music doesnt play at all. I tried listening to music from the following site and firefox in windows XP plays it but not ubuntu. the play, stop and other buttons are just grayed out. I cant click on them at all.

[http://www.musicindiaonline.com/music/ut/s/carnatic_instrumental/10/](http://www.musicindiaonline.com/music/ut/s/carnatic_instrumental/10/)

In XP, if I open this link then it first opens a pop-up window and  detects my real player and windows media player and then I can choose one to select but in ubuntu pop-up window doesnt detect them at all. I have all real player, xine, mplayer and VLC installed. Also have w32codecs. I also have all Flash and java plugins installed. 

With youtube, it buffers and plays but I cant see the progress bar on the bottom of youtube video (the bar from where you can enter the full screen mode and increase/decrease sound, etc.). 

no idea what is going on.

---

### Post by (((X))) on 2008-03-26
Ok,I've selected a song, I tryed to play that song, It says: loading please wait status:ok loading, but will not play.
What is the status of you realplayer?I have available.
Could you post screenshot.

---

### Post by aachen on 2008-03-26
Well I am using XP right now so cant post a screenshot but as I said the pop-up window will be opened. But neither will it  detect any player nor will it load and display any songs in the pop-up window. all the buttons to play, stop are grayed out.

---

### Post by (((X))) on 2008-03-26
That window uses javascript, make sure you've it enabled.

---

### Post by aachen on 2008-03-26
Thanks  i will check for that. any idea about youtube ? i think it only uses flash which i already have. and youtube works but progress bar is not visible like in XP.

---

### Post by gandaran on 2008-03-26
> **aachen said:**
> Thanks  i will check for that. any idea about youtube ? i think it only uses flash which i already have. and youtube works but progress bar is not visible like in XP.

are you using adobe flash or gnash for viewing youtube? remove gnash if it's installed, maybe the problem.

as for the videos on this site [http://www.musicindiaonline.com/music/ut/s/carnatic_instrumental/10/](http://www.musicindiaonline.com/music/ut/s/carnatic_instrumental/10/) you'll never get them to play on linux, I think they use microsoft ativex.

---

### Post by aachen on 2008-03-26
I had downloaded adobe flash. havent heard about gnash. i will remove it if its installed by default. but is it really like I cant play some websites in linux which use activeX from MS ? this is a big turn off.

---

### Post by aachen on 2008-03-26
ok i had gnash installed. so i removed it and now it detects my real player and windows media player from XP partition. I selected real player but it gives the error that 'methods are missing'. is it a problem of real or firefox ? javascript is already installed which is required to play this website.

---

### Post by saj0577 on 2008-03-26
Not sure if you have same problem but i know someone with this exact program and we have been trying for months to fix it and nothing works, uncompatible sound card, were just hoping 8.10 wil fix it as its the only thing keeping him from single boot.

Saj

---

### Post by aachen on 2008-03-26
I got the problem solved for youtube. I uninstalled gnash SWF player and installed flash player version 9 and now it plays perfectly. but still looking to solve the problem of opening the above website.

---

### Post by saj0577 on 2008-03-26
Glad to hear it and good luck.

Saj

---

### Post by SunnyRabbiera on 2008-03-26
> **aachen said:**
> I had downloaded adobe flash. havent heard about gnash. i will remove it if its installed by default. but is it really like I cant play some websites in linux which use activeX from MS ? this is a big turn off.

Well active X is a microsoft thing, it will never be ported to linux.
there might be the factor that some sites might not work for you as some sites want MS stuff.
its not our fault, blame the site makers and other people for not making their stuff available to other systems.
Please take in consideration that linux is a windows alternative not a windows replacement.

---

### Post by aachen on 2008-03-26
Thanks all the ppl for replying.. now everything works. I think it was a problem of java script. I opened synaptics and installed something from java script (dont exactly remember) and it works now.

---

### Post by TooRight on 2008-03-26
> Please take in consideration that linux is a windows alternative not a windows replacement.

You're right...Linux is BETTER :p hehehe

---

### Post by sofiankrt on 2008-03-26
Just an idea...
Try getting Windows Media Player or Real Player working under Linux, through WINE, then you might be able to play the videos.

---

