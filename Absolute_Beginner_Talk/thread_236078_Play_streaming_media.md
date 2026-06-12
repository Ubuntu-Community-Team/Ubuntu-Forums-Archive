---
title: "Play streaming media"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by d4rk on 2006-08-14
After a long break with M$ Window$, I've finaly made it back to Linux Ubuntu. The first reason for why I went back, is for that when surfing around, I found something named EasyUbuntu. I do believe that innstalled some codecs, drivers for my graphical unit, and some other programs.

Let's take the example [www.dumpalink.com](www.dumpalink.com) , I want to watch the videos they've got on theyr site, but how ? I need some window$ media plugins :( 
Is there any alternative for Linux ?

I'm using FireFox.

---

### Post by Kobalt on 2006-08-14
Yes you can do all that with Ubuntu, you need to install windows codecs (w32codecs) and Mplayer with firefox extension. You will find how to do all this over here : [Wiki Dapper]("http://ubuntuguide.org/wiki/Dapper")

Cheers ! :rolleyes:

---

### Post by d4rk on 2006-08-16
> **Kobalt said:**
> Yes you can do all that with Ubuntu, you need to install windows codecs (w32codecs) and Mplayer with firefox extension. You will find how to do all this over here : [Wiki Dapper]("http://ubuntuguide.org/wiki/Dapper")

Cheers ! :rolleyes:

Ok, thanks ! I'll check that out !

---

### Post by d4rk on 2006-08-16
I manage to get the mPlayer to work with Firefox, but how do I get the windows codecs ?

---

### Post by dannyboy79 on 2006-08-16
He told you to look at the Wiki Dapper, it is there. You obviously missed it so here it is straight from the wiki.

How to install Multimedia Codecs
Stubby All known codecs work except for wmv 

Read #General Notes 
Read #How to add extra repositories 
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad
sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly 
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
sudo apt-get install w32codecs

Read #How to restart GNOME without rebooting computer

---

