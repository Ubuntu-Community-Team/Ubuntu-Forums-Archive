---
title: "Link - packaging problem.."
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-05-10
I've been getting this error-report in terminal when trying to install various apps. Last one was gftp.. I got this message..

Setting up gftp (2.0.18-10) ...
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

Actually now I was able to install gftp, and it works perfectly.. But I still get the message above sometimes when trying to install other apps.

I have automatix 5.8.2 installed, but everytime I try to install something from Automatix it just doesn't get installed, så I'm wondering if I installed it correctly. And I'm having problems getting codecs to work.. DVD's are hopping, and I'm unable to play any music-cds. I can play mp3's in Beep, but the pc doesn't recognise mp3's in general.
.

HelP?

lodravah

---

### Post by adam.tropics on 2006-05-10
Looks like the theli server is down, it happens! Try again a bit later!



Edit:Automatix has been very good for me in the past, and has a pretty huge thread with many problems/solutions to flick through...([3rd Party projects,Automatix]("http://www.ubuntuforums.org/forumdisplay.php?f=77"))

---

### Post by lodravah on 2006-05-10
[QUOTE=adam.tropics]Looks like the theli server is down, it happens! Try again a bit later!



Edit:Automatix has been very good for me in the past, and has a pretty huge thread with many problems/solutions to flick through...([3rd Party projects,Automatix]("http://www.ubuntuforums.org/forumdisplay.php?f=77"))[/QUOTE]


I've been getting this message ever since I installed Automatix 5.8.2, which was yesterday.. Really think the server is down still or is it outdated..

lodravag

---

### Post by adam.tropics on 2006-05-10
As far as I can tell, it uses theli to get Listen Music manager (pretty nice program incedentally). What I don't get is that I can't see a Breezy deb there, just a Dapper one, so why Automatix is using it I don't know! See waht happens if you opt not to install Listen, it should fix it, then if you would like to try Listen you can use a nob-dapper specific package from [Sourceforge.]("http://sourceforge.net/project/showfiles.php?group_id=161415&package_id=181822")

---

### Post by lodravah on 2006-05-10
[QUOTE=adam.tropics]As far as I can tell, it uses theli to get Listen Music manager (pretty nice program incedentally). What I don't get is that I can't see a Breezy deb there, just a Dapper one, so why Automatix is using it I don't know! See waht happens if you opt not to install Listen, it should fix it, then if you would like to try Listen you can use a nob-dapper specific package from [Sourceforge.]("http://sourceforge.net/project/showfiles.php?group_id=161415&package_id=181822")[/QUOTE]


Hm..
So its only this "Listen Music" - program that it is trying to get? 'cause I keep getting this message all the time when I try to install something in terminal. And incidentially, I don't know how to not opt to install "listen." I'm very new at Ubuntu and sometimes it is quite a steep learning curve.. Appreciate your help..

---

### Post by adam.tropics on 2006-05-10
try in terminal:

$ sudo gedit /etc/apt/sources.list

then change the line that says something like

deb [http://theli.free.fr](http://theli.free.fr) breezy 

to

# deb [http://theli.free.fr](http://theli.free.fr) breezy 

ie. add the #, then save the file, do

$apt-get update

 and try installing something again...

---

### Post by lodravah on 2006-05-10
Seems to be working now. The error message is gone, and apt-get update runs as it is supposed to, methinks.. I think that did it. Thank YOU!!

lodravah

---

### Post by adam.tropics on 2006-05-10
No worries, it might be worth just checking your sources list against someone else who is running Breezy, the one in post 1 [here]("http://www.ubuntuforums.org/showthread.php?t=92672") seems all good. (even though things semm ok, just to be sure) Other than that, have fun!

---

