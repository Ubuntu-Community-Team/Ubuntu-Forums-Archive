---
title: "Real Player xubuntu how?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by xyeovillian on 2008-01-07
I've searched google etc still can't find it I'm trying to install Real Player xubuntu as I would like to listen to BBC Radio 2 in ubuntu but I can't figure how to!!  And the BBC run it through Real Player.

---

### Post by finer recliner on 2008-01-07
if you have the latest version of (x)ubuntu (7.10) then do the following using firefox:

try opening the BBC radio player from their website. you may get a warning from the website that it didnt detect you had real player installed. click cancel to ignore this warning and procede. now you should get a yellow banner at the top of the window saying your missing a plugin to view this page. click the button to install the missing plugin. ubuntu + firefox will give the option to choose Xine or Mplayer as your plugin. both of these codecs support real player files. you probably will have to restart firefox when the plugin installation is complete.

enjoy!

---

### Post by gn2 on 2008-01-07
I have 64-bit Xubuntu 7.10 and the Mplayer plug-in works well, the Xine one didn't give clear sound.

---

### Post by chewit on 2008-01-07
> **finer recliner said:**
> if you have the latest version of (x)ubuntu (7.10) then do the following using firefox:

try opening the BBC radio player from their website. you may get a warning from the website that it didnt detect you had real player installed. click cancel to ignore this warning and procede. now you should get a yellow banner at the top of the window saying your missing a plugin to view this page. click the button to install the missing plugin. ubuntu + firefox will give the option to choose Xine or Mplayer as your plugin. both of these codecs support real player files. you probably will have to restart firefox when the plugin installation is complete.

enjoy!

Far easier method, xyeovillian. I have use this method to listen to Radio 1. 

Go on to the Radio 2 home page. 
Click listen live, then select Windows Media Player.
A Window will open
where is syas 'Listen using stand-alone Windows Media Player', right click and save the link.
You will have downloaded a .asx file, VLC can read this and you will be able to listen to radio 2 on your desktop.

Hope this helps

---

### Post by godfree2 on 2008-01-07
doesn't the VLC player, stream realmedia?
I'm listening right now to RadioParadise

---

### Post by chewit on 2008-01-07
Yeh it does, but u have no control panel on BBC. Since its setup for WMP

---

### Post by por100pre1 on 2008-01-07
Check if this works for you:

[http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

---

### Post by xyeovillian on 2008-01-07
Marvelous you wait for a bus then suddenly they all come along at the same time!  Thanks por100pre1 I tried that download tried to install and it comes up with this = 

(Reading database ... 104171 files and directories currently installed.)
Unpacking realplayer (from ... /realplay_10.00.9-0feisty1_i386.deb ...
dpkg: error processing /tmp/realplayer_10.0.9-0feisty1_i386,deb (--install):
 trying to overwrite '/usr/share/locale/zh_TW/LC_MESSAGE/libgtkhx,mo' ,which is 
 also in package helix-player
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I have also tried the plugins suggested for mplayer still no go!

---

### Post by por100pre1 on 2008-01-23
> **xyeovillian said:**
> Marvelous you wait for a bus then suddenly they all come along at the same time!  Thanks por100pre1 I tried that download tried to install and it comes up with this = 

(Reading database ... 104171 files and directories currently installed.)
Unpacking realplayer (from ... /realplay_10.00.9-0feisty1_i386.deb ...
dpkg: error processing /tmp/realplayer_10.0.9-0feisty1_i386,deb (--install):
 trying to overwrite '/usr/share/locale/zh_TW/LC_MESSAGE/libgtkhx,mo' ,which is 
 also in package helix-player
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I have also tried the plugins suggested for mplayer still no go!

Sorry for the delay! :( **You cannot have Helix Player and Real Player installed together.** Remove Helix Player and then install Real Player.

---

