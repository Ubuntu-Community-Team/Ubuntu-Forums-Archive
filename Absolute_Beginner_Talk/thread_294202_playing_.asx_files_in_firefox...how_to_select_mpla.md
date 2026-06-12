---
title: "playing .asx files in firefox...how to select mplayer"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2006-11-06
Hi all,

If I try to play a *.asx file in Firefox and it selects Totem as the player or "other", where do I go to select mplayer to play the file?

---

### Post by Dr. Nick on 2006-11-06
> **mdsmedia said:**
> Hi all,
 
If I try to play a *.asx file in Firefox and it selects Totem as the player or "other", where do I go to select mplayer to play the file?
 
Is it trying to open and download the file, or play it embedded in the webpage?
 
If you have the option under other to type in a program name then try
 
gmplayer
 
if it is embedded then you will need to mess around with the firefox plugin settings

---

### Post by mdsmedia on 2006-11-06
> **Dr. Nick said:**
> Is it trying to open and download the file, or play it embedded in the webpage?
 
If you have the option under other to type in a program name then try
 
gmplayer
 
if it is embedded then you will need to mess around with the firefox plugin settingsWhen I click on the play button it opens up the "open with.." dialog. I guess that means it is embedded?

If I want to select mplayer, is there a place in the filesystem to select mplayer?

Thanks for the response...it almost answers my question, but it's sort of in between if you know what I mean :)

---

### Post by Dr. Nick on 2006-11-06
If it is embedded it may give you a missing plugin icon, Probably not embedded if it pops up a box asking what to open with. If it does give you the oppurtunity to browse the filesystem to select the app try /usr/bin/gmplayer
 
I am pretty sure gmplayer is the executable you want, but forget where its at in the filesystem and am away from my Ubuntu computer at the moment, may have to search for the file.
 
If you cant figure it out then a link to the site, or another with the same behavoir may help.
 
What I did was open synaptic and remove totem-mozilla (or similar) and install mplayer-mozilla to make mplayer play embedded audio and video instead of totem

---

### Post by mdsmedia on 2006-12-03
After not succeeding with mplayer or gmplayer I gave it away for a while. After reading another "unrelated" thread I tried VLC player and IT WORKS :)

So I will change the title of this thread to RESOLVED. Thanks to this wonderful community.

---

