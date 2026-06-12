---
title: "HELP-Trying to stream 1040 am off the web"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Eriks_Knor on 2008-01-08
Hi, folks.
I've tried looking in the forums, but haven't been able to find anything to help me just yet.
I'm trying to stream [Team 1040 am]("http://www.team1040.ca/") (Vancouver, BC) with Firefox, but can't get it to work. This is on my laptop. I have installed the medibuntu repositories\codecs, gstreamer, and even mplayer to see if that would work, but nothing.
Any suggestions?

I GOTTA be able to stream my Canucks games!

Thanks!

---

### Post by ubuntu-freak on 2008-01-09
Have you got mozilla-mplayer installed? If so try my guide here [http://ubuntuforums.org/showthread.php?t=658970&page=3](http://ubuntuforums.org/showthread.php?t=658970&page=3)

---

### Post by yaknowwat on 2008-01-09
or you can try vlc player its made for this type of stuff.

it should be in the synaptic possibly add/remove

---

### Post by ubuntu-freak on 2008-01-09
> **yaknowwat said:**
> or you can try vlc player its made for this type of stuff.

it should be in the synaptic possibly add/remove

MPlayer is made for it too and with the settings I posted it will stream just about everything. More than vlc anyway. Even bbc.co.uk rm streams.
 
Plus you can save the streams to your home folder with mplayer.

Nathan

---

### Post by philinux on 2008-01-09
I've got the mplayer plugin but It might need the helix dna plugin that comes with realplayer.

The version of realplay in gutsy has a flaw, in that it fails to install the helix plugin correctly. I used the feisty version and it installs it correctly. It's been reported at launchpad.

Anyway here's the link for realplayer. The bottom one on the list is the .deb file.

[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

---

### Post by Casual Fan on 2008-01-09
NO NO NO! Get XM Satellite Radio!

Every NHL game and 169 other channels of music, talk, sports, and entertainment!

:):):):):):)

Seriously.

---

### Post by ubuntu-freak on 2008-01-09
> **philinux said:**
> I've got the mplayer plugin but It might need the helix dna plugin that comes with realplayer.

The version of realplay in gutsy has a flaw, in that it fails to install the helix plugin correctly. I used the feisty version and it installs it correctly. It's been reported at launchpad.

Anyway here's the link for realplayer. The bottom one on the list is the .deb file.

[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

Nah, I play rm streams with just the mplayer plugin. You just need to have win32codecs and enable it in the plugin conf like my guide says.

Nathan

---

### Post by philinux on 2008-01-09
> **reassuringlyoffensive said:**
> Nah, I play rm streams with just the mplayer plugin. You just need to have win32codecs and enable it in the plugin conf like my guide says.

Nathan


For the bbc website radio streams firefox needs the helix plugin.

---

### Post by ubuntu-freak on 2008-01-09
> **philinux said:**
> For the bbc website radio streams firefox needs the helix plugin.

Radio and not video you mean? That would make sense.

Nathan

Edit: Helix doesn't play proprietary formats. MPlayer or RealPlayer work well.

---

### Post by Matt Yun on 2008-02-19
> **Eriks_Knor said:**
> Hi, folks.
I've tried looking in the forums, but haven't been able to find anything to help me just yet.
I'm trying to stream [Team 1040 am]("http://www.team1040.ca/") (Vancouver, BC) with Firefox, but can't get it to work. This is on my laptop. I have installed the medibuntu repositories\codecs, gstreamer, and even mplayer to see if that would work, but nothing.
Any suggestions?

I GOTTA be able to stream my Canucks games!

Thanks!

I can't believe no one else on this thread even came close to understanding your question!  You weren't asking about streaming the BBC, you were asking how to tune into Vancouver Canucks hockey games on the [TEAM1040 AM]("http://www.team1040.ca/player/") radio station webcasts!

Fellow Canucks fan; I'm currently on the road, trying to catch tonight's Canucks v Wild game.  I always used to tune into TEAM1040 with the following mplayer command:

```
mplayer -playlist http://www4.insinc.com/ibc/mp/md/play/u/356/1408/wa56en.asx
```

However, tonight, with just 2:00 left to go in the third period (score 2-2), I find to my chagrin that the above no longer works.  Thanks to the [UnPlug]("https://addons.mozilla.org/en-US/firefox/addon/2254") plug-in for Firefox, I see that Insinc (the web developer for TEAM1040) has changed the stream urls.

Mplayer doesn't seem to work anymore, but VLC does:

```
vlc mms://a1873.l858721510.c8587.g.lm.akamaistream.net/D/1873/8587/v0001/reflector:21510
```

Arghh.... just missed the game... we won 3-2! Yay!

---

### Post by ubuntu-freak on 2008-02-20
The OP didn't reply once and it's been over a month. Was a lame thread though, had to edit one of my posts as it was just plain wrong.
 
Did MPlayer only stream that station with the command line then? Did you try the settings from my how-to? They haven't really let me down. 
 
Nathan

---

### Post by Matt Yun on 2008-02-21
> **reassuringlyoffensive said:**
> The OP didn't reply once and it's been over a month. Was a lame thread though, had to edit one of my posts as it was just plain wrong.
 
Did MPlayer only stream that station with the command line then? Did you try the settings from my how-to? They haven't really let me down. 
 
Nathan

I normally just use the console to listen to streaming audio; I have a bunch of bash scripts for my favourite Internet radio stations.  It's quicker that way.

This thread came up because the radio station had changed its stream url, and I was googling whether other people had the same experience.  I posted here simply to let other Ubuntu-using Vancouver Canucks fans know how to access the TEAM1040 stream without having to use a browser.

---

### Post by Matt Yun on 2008-02-27
Just an update, for Vancouver Canucks fans who stumble upon this thread:  the TEAM1040 stream url has changed to mms://cac1.insinc.com/team1040-live-wa56en.  Both mplayer and vlc work.

---

### Post by ubuntu-freak on 2008-02-27
> **Matt Yun said:**
> Just an update, for Vancouver Canucks fans who stumble upon this thread:  the TEAM1040 stream url has changed to mms://cac1.insinc.com/team1040-live-wa56en.  Both mplayer and vlc work.

 
Excellent. I'm guessing they received some emails concerning the problem. The BBC are changing their stream domains, and it's improving compatibiliy. 
 
Feedback works people. Email the troublesome sites.
 
Nathan

---

