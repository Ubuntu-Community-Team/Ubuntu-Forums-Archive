---
title: "Poor Wireless signal strength with Feisty Fauwn"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2007-04-29
Hi again,


I have install Feisty Fawn on my primary desktop as well as an old Compaq deskpro I  plan on turning into a file server.  I have two questions.


First off with my desktop I had no problems with my Wi-Fi card with Dapper and Edgy, but since I installed Feisty Fawn my signal strength for my DLink WDA-1320 has gone down the tubes.  It even cuts out completely with relative frequency.  What gives?  I now can barely get better then  20% signal strength  whereas I was hitting 60 % or higher with the default drivers for Dapper and Edgy.  I am still getting 60% or better with XP so I know my hardware is not dying on me.  Has anyone else run into this problem.  By the way I am running the vanilla i386  32bit version  even thought I have an AMD 64 3800+ X2.  I find 64bit software just is not prevelant enough yet to make it worthwhile.

My second question is possibly simpler.  Should bother making a point of installing the Server version of Ubuntu on my new file server or will the desktop version doe the job just fine?

This is my first attempt at setting up a server of any kind and it is definitely not my area of expertize so please bare with me if this seems like a goofy question.  This box is intended to be a learning tool as much as anything.

Thanks

Dan

---

### Post by DanFromWinterpeg on 2007-04-29
I stumbled upon an answer to my first question.

I added a second USB Wi-Fi Adaptor to my PC and now I am getting above 90% signal strength.  It would appear that after I installed it and rebooted this solved the issue immediately.

I still am not sure about my second question.

Thanks 

Dan

---

### Post by %hMa@?b&lt;C on 2007-04-29
desktop version will do the job fine.  you just need some server daemons like ftpd or apache to serve up the files.

---

### Post by louieb on 2007-04-29
I prefer to use the server version. Just because LAMP works out of the box. I also install a gui but don't use it unless I have to. Doesn't really matter for a home file server. Just look around the forum you'll find lots of good stuff to try. Like [http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core](http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core)
[http://ubuntuforums.org/showthread.php?t=419530](http://ubuntuforums.org/showthread.php?t=419530)

Check out the how to section search for server. Have fun.:lolflag:
rock on:guitar:

---

