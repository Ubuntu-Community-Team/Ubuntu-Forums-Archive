---
title: "Can't play MPEG video"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by loopeando on 2007-06-24
I have a weird trouble when trying to play a MPEG video over a network hosted on a Windows PC.

A few weeks ago it did with no problem, with Totem (Xine), but today when I tried to play a Babyshambles MPEG video it loaded the first seconds and after that died.

I have all my codecs installed via Automatix and it's the first codec related problem I have.

I'm using Feisty on a Lenovo 3000 N100 (Laptop)

Any idea how can I solve this?

Thanks in advance.

---

### Post by FleetAdmiral74 on 2007-06-24
The most important piece of advice I can give is do not use AutoMatix. I do not have time to go in depth, but it is very messy, breaks on major upgrades, and is seriously not good for your system maintenance. 

About your problem, try using VLC instead and see if it will play.

---

### Post by loopeando on 2007-06-24
VLC can't play files over a network, don't know why.

I have been doing some Google and found a possible solution:

- Mounting the shared folder

The thing is that I can't seem to find a guide that works.

Any idea about this?

---

### Post by kelvin spratt on 2007-06-24
Thats very strange as i use Automatix all the time and never had a problem

---

### Post by FleetAdmiral74 on 2007-06-24
VLC can play files over a network, its called network stream or something. Maybe you are not configuring it properly, not really sure.

---

### Post by FleetAdmiral74 on 2007-06-24
From the wiki..

Automatix is not recommended by the Ubuntu development team, which has criticised its content.[1] Some individual Ubuntu developers blamed Automatix 1 for breaking updates from Dapper to Edgy.[2][3] On 2 November 2006 Ubuntu CTO Matt Zimmerman said "I cannot recommend the use of this program, and systems where it has been used cannot be supported with a clean and official upgrade path."

---

### Post by loopeando on 2007-06-24
Well, actually I'm ussing Automatix2.

I have used previous Automatix versions on Dapper and Edgy and I've never experienced any kind of problem.

About the VLC streaming I had no idea about that, I'll look into it but since I'm a newbie in the GNU/Linux world I'll need your help.

Thx for the quick response!

---

### Post by loopeando on 2007-06-24
I was able to do streaming with VLC but the thing is that whenever I want to watch an MPEG video I have to setup VLC to stream it and It's annoying to do so.

Isn't there a way to fix MPEG playback over a network in Totem Xine?

I remind you that AVI and others work fine.

---

### Post by kelvin spratt on 2007-06-24
a lot of people talk about Mplayer i can't help on that as i don't use it but there have been a lot of threads recently on the subject might pay to read the multimedia section. i go no further than flash player and the mplayer plugin for FFox my self.

---

### Post by loopeando on 2007-06-24
Doing some research about video over network I've found this project for Mac

[http://www.trystx.com/about.html](http://www.trystx.com/about.html)

It's something like DAAP but for video.

I believe that a software like that might solve my problems once for all, any ideas if there's a simililar project for Linux?

---

### Post by loopeando on 2007-06-24
Well, after an afternoon of testing I've fixed it by deleteing the .xine folder on my home folder and re-installing all Xine related packages.

I can play every format (AVI, MPEG, WMV,etc) but the thing is that now my Totem player uses buffer, in the past it didn't needed it, and the video stops every 5 seconds or less.

Any idea on how can I increase the size of the buffer in Totem Xine?

Thx!

---

