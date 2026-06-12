---
title: "DeVeDe problems"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-05-19
Hi guys,

I recently upgraded to Feisty and now I'm having problems with MPlayer and DeVeDe when trying to convert avis to isos for burning to DVD.

The preview option previews ok but there's a constant loud noise over it - like static but really loud. Plus DeVeDe has started crashing at about 99%.

Anyone have any idea what the problem is? I installed all of the gstreamer plugins in case it was a missing audio codec or something. I've also noticed MPlayer is having problems with a "missing video output" when I try and play files.

Thanks in advance,
G

---

### Post by taurus on 2007-05-19
What version of devede do you have on your machine right now?

And for MPlayer, go into Preferences, Video and change the driver from whatever it is to **xv**.  Close it and restart.

---

### Post by deuchar1 on 2007-05-19
Cool. I got it playing in MPlayer. 
I'm using DeVeDe 2.9 - still getting the same problem when I preview the file. Any suggestions?

---

### Post by halitech on 2007-05-19
I'm having the same problem here with some files. Most seem to work fine but others will get to where it creates the dvd structure and then nothing happens when trying to convert the iso. luckily VLC will play the files in the folder and when burning using k3b, it will still play in my dvd player but would like for it to finish. any ideas?

---

### Post by deuchar1 on 2007-05-19
You're lucky you're getting that far! The audio is all messed up here - I tried the MPEG created by DeVeDe before it aborted and it is awful - totally unplayable :(

---

### Post by halitech on 2007-05-19
did you install all the multimedia codecs?

---

### Post by deuchar1 on 2007-05-19
I think so - I have all gstreamer plugins installed and the original avi plays fine in MPlayer/Xine. It's only when I preview it in DeVeDe that it starts going haywire

---

### Post by taurus on 2007-05-19
The version from the repos is a little old so why don't you try the latest version, 2.13, to see if it fixes the problem with audio.

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by halitech on 2007-05-19
I love this program but other then that 1 page, I can't find anything in English on it. If I/we install from there, will it install in the same place and work from the menu or will we need to create a symlink for it?

---

### Post by MrKlean on 2007-05-19
I heard there's a problem with Devede and Feisty.   Supposedly the mplayer is messed up and it makes static when it compiles.

---

### Post by halitech on 2007-05-19
haven't seen that problem myself, when it works (85% of the time) it's great, it's just those few times it doesn't complete that I can't figure out. Maybe others are but I don't.

---

### Post by deuchar1 on 2007-05-20
Ahhh it's a Feisty problem then. That makes sense. The problem only cropped up when I upgraded the other day.

Any fixes on the way? :p

---

### Post by deuchar1 on 2007-05-20
Well, I've done some trawling and found this is a definite problem with the DeVeDe/Feisty combination. Lots of other people are having exactly the same problem. Looks like it's a wait-for-a-fix job!

Anyone know any decent DeVeDe equivalents? I can't burn my movies to DVD any more now :(

---

### Post by deuchar1 on 2007-05-21
Problem (semi) solved....

I downloaded the new CVS MPlayer from the DeVeDe site, extracted the .deb (didn't install it) and found the files mplayer and mencoder. I then replaced my existing versions in usr/bin et voila, DeVeDe works again.

Only problem now is a silly amount of audio lag when I burn movies - every other program plays them fine but in MPlayer the audio is out of sync by a good minute or two. Damn :P

---

### Post by plainjane on 2007-05-21
I have been using Todisc/Tovid to convert avi files to burn onto DVDs.  Slow, but works.  Only thing is I have to use Wine/DvdDecryptor to burn.  When I burn with Kb3 they won't play in my stand alone player.

---

### Post by MrKlean on 2007-05-21
That didn't work for me ; (   And there doesn't appear to be much activity in finding a solution ; ( sadly.. of course, I've been wrong before LOL!!

---

### Post by deuchar1 on 2007-05-23
The copy/paste of mplayer and mencoder definitely didn't fix it?
Try upgrading to v2.13 of DeVeDe from the site - I forgot to mention I did that too. Might not make a different, but worth a try.

Oh, and the audio lag was only with a couple of movies that it turns out have a prob anyway. Plus you can offset the audio in DeVeDe anyway.

---

### Post by Ghost|BTFH on 2007-05-28
The problem is definitely mplayer/mencoder related.

Went to the site, downloaded devede and mplayer (mencoder included). Uninstalled mplayer, mencoder and devede from my system.

Installed mplayer deb package.

sudo ./install.sh the devede program.

Fired up devede and had it convert an xvid .avi file to .mpg with zero issues.

---

### Post by ernstblaauw on 2007-06-20
I want to fix my mplayer and mencdoer too. I'm using Feisty **64-bit**. I can't downgrade using the packages from DeVeDe, because they're 32-bit. Does someone know how I can get fixed package for my system?

---

### Post by Damanther on 2007-06-20
I've had the same static problem with mplayer. I uninstalled it and then installed the command line only version for conversion purposes.

I've been using Vlc for player and Kino for creating the DVDs. Kino is VERY simple and does not have a ton of features, but it works reliably.

---

### Post by svega85 on 2007-08-03
i'm new to script writing but i wrote this one to install mplayer from the svn and compile and replace the old mencoder
script was flawed writhing new one

---

