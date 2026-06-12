---
title: "Problems with :edgy, firefox, real player, cbs.com/innertube"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by turbotuba on 2006-11-15
I'm having problems with cbs.com/innertube and getting the videos to play. I downloaded Real Player. But it still doesn't work properly. Can anyone help me. 
What info do I need to provide?
:confused:

---

### Post by petit.padavoine on 2006-11-15
> **turbotuba said:**
> I downloaded Real Player.

Actually the site requires Flash Player for the videos, not Real...

---

### Post by turbotuba on 2006-11-15
I have flash 9 
I believe you need either windows media player or real player.
Whatever i need, I only get sound and no video.

---

### Post by turbotuba on 2006-11-16
cough cough bump cough

---

### Post by tebbendj on 2006-11-18
I am having simular problems, but I can't even get sound.  Nothing plays on CBS/Innertube for me.  I have Flash 9, I have tried it with MPlayer for WMP and also installed RealPlayer.  I have tried it with Media Wrapper for Firefox activated and deactivated.  Nothing will allow me to play any videos from CBS.com.  I can play from NBC and ABC, and YouTube, etc.  

Please post if you ever get it to work.  

update:
I removed the mplayer pluggins for real media--now I get sound, but still no picture.

---

### Post by turbotuba on 2006-11-21
Still can't get it to work.](*,)

---

### Post by Francis 24/24 on 2006-11-30
Hi,

after upgrading to 6.10 realplayer would not start to play the videos
of the BBC. No error message or any clue.

I removed from the firefox/plugins directory the following files :
libtotem-complex-plugin.so
libtotem-complex-plugin.xpt
and realplayer is now launched and plays fine.

(Really tricky : I was looking for *missing* plugins, not for extra ones.
Although these files likely tried to start totem, there was never any clue 
of this.)

Hope this helps,

Francis

---

### Post by drphilngood on 2006-11-30
> **Francis 24/24 said:**
> ...I removed from the firefox/plugins directory the following files :
libtotem-complex-plugin.so
libtotem-complex-plugin.xpt
and realplayer is now launched and plays fine.

(Really tricky : I was looking for *missing* plugins, not for extra ones.
Although these files likely tried to start totem, there was never any clue 
of this....

I did something very similar except I use Mplayer for everything.

Couldn´t do without my BBC news vids.[-(

---

### Post by tebbendj on 2006-12-04
Can anyone confirm if Innertube works from them with Edgy?  I have seen a few suggestions from different people, but no one indicates it cbs/innertube actually works.

---

### Post by endersshadow on 2006-12-04
All I get whenever I click the "Watch video" buttons spread around the page is either nothing or the slide show progresses to the next one. :-|

---

### Post by ElizaPi on 2006-12-06
I'm having the same problem, I use Mac OSX Tiger, and it tells me I need a Netscape plugin, but netscape says no plug-in exists.  I've gotten it to work on a Windows XP desktop, but I never had problems with that one.  Also I can play videos from all other sites.

---

### Post by tebbendj on 2006-12-07
I have had no problem using Mac OSX Tiger 10.4.8 with Safari and everything updated.  Actually I use my wifes iBook to watch Innertube since it doesn't work with Edgy/Firefox.  

On another note, I was searching other forums and found on the Fedora forum that it works using Flash 9 beta and Mozilla 1.7.3 or above.  I installed Mozilla 1.7.13 and it will play the videos but everything doesn't work.  (i.e. Full Screen didn't work, and trying to restart the video didn't work, but I did get it to work some what.)

---

### Post by rosswmcgee on 2007-04-08
> **tebbendj said:**
> Can anyone confirm if Innertube works from them with Edgy?  I have seen a few suggestions from different people, but no one indicates it cbs/innertube actually works.
No I have not but would ask the same question. I am getting close because I can get VLC to open, in 
Inntertube, but still no picture or audio. Same goes for the Bloomberg.com talking head videos.

---

### Post by tebbendj on 2007-04-09
I can confirm that I watched an entire episode on cbs/innertube about a week ago.  I could not use full screen and it took several minutes to start playing.  The delay in start could be my buffering setting in Realplayer is set very high.  I am running the latest updates of Firefox, Realplayer and Adobe Flash.

---

### Post by FoundmyTux on 2007-04-09
I had the same problem until I uninstalled realplayer and removed the totem plugins. Then install mplayer and mozilla-mplayer if you haven't already. After that I could watch innertube.

To removed totem plugins using terminal:
       
cd /usr/lib/firefox/plugings
sudo rm libtotem*

To install mplayer using terminal:

sudo aptitude install mplayer mozilla-mplayer

---

### Post by mrwilloby on 2007-04-28
> **FoundmyTux said:**
> I had the same problem until I uninstalled realplayer and removed the totem plugins. Then install mplayer and mozilla-mplayer if you haven't already. After that I could watch innertube.

To removed totem plugins using terminal:
       
cd /usr/lib/firefox/plugings
sudo rm libtotem*

To install mplayer using terminal:

sudo aptitude install mplayer mozilla-mplayer

I followed these instructions and now I get a message in the innertube box with an mplayer plug-in logo:

Playing rtsp://a885.v21927d.c21927.g.vr.akamaistream.net/
ondemand/7/885/21927/v04272200/
cbscomstor.download.akamai.com/8605/_!/g2demand/entertainment/
primetime/csi/rebroadcast/ep22/csi719a.rm?
auth=daEbMadbSaLcFbhb7dncpd5b4bPdRbYbNbr-bgmSkf-buy-
M9zNgUqf&amp;aifp=v04272200

The sound plays though. It's progress, but I'm still not there...

Any thoughts?  MIght I possibly have other plug-ins to remove that I don't know about?

---

### Post by toonces on 2007-07-09
I'm not the most plug-in savvy, but this worked for me.  It looks like the adobe flash plug in doesn't work on Intel Macs just yet.  I opened Safari using Rosetta (You can choose this option in the "get info" window for the application).  So far I seem to have audio and video.  Good Luck.

---

### Post by gwenwyn on 2007-07-24
I was having the same problem using Firefox under feisty (sound but no picture on CBS.com).  I "solved" it by going to the site under the Epiphany web browser.  Sound and picture both work just fine.

---

### Post by deodatus on 2007-10-29
*BUMP*   for anyone who is watching this thread,  I got it to work by disabling adblock plus AND noscript.  The Epiphany browser works also.

---

### Post by DoorGunner on 2007-10-30
if firefox is an issue why not try > about:plugins it should read about : plugins all to gether...... not that gay little happy face.....instead of [http://blahblah](http://blahblah)..... 

That way you can see exactly what plugins you have. I could be a simple ln -s of a module your missing.

---

### Post by vbt on 2007-11-27
Innertube works for me in Edgy and Gutsy. Real/Helix plugin and flash plugin plus removing the totem plugins.  

The problem in Gutsy/Firefox is that sometimes the video gets choppy, like slowed down.  I'm trying Epiphany and now Innertube works perfectly.  Why would that be? Is that a firefox issue or a flash issue?

---

### Post by ksujason on 2008-01-12
I had the same problem and solved it by getting the epiphany browser. Once I put it on, CBS innertube videos worked great. 

I still use Firefox for everything else, because I am just more used to it.

---

### Post by ubuntu-freak on 2008-01-13
Try the settings in my how-to. 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Remove realplayer and install helix and mplayer plugins. 
 
All info in my how-to. 
 
Nathan

---

