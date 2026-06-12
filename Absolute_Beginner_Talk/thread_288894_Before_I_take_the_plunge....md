---
title: "Before I take the plunge..."
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Straight Shooter on 2006-10-30
Hello,

I am going to take a breath tonight and install Ubuntu 6.10 Edgy. I will not totally wipe out Win Xp Pro. I will dual boot install. 
I also have Acronis True Image installed in Win Xp with back ups made just in case I decide I can't deal with it LOL...

I have a couple of questions.. before I REALLY do this.. 
If someone could help me here, I would really appreciate it.

1. I understand there is no registry in Ubuntu or Linux for that matter. If so, then how "clean" are uninstalls? When I uninsatll a program, is it ALL out? Do remnants remain?

2.  I need to make sure I find a replacement for the "Sony Sonicstage" Software. I have a Sony "Bean MP3 Player. I heard there is nothing out there. Is that true?

3. Will I be able to install a Palm Treo 650 Replacement proggie so I can use and sync to my Palm Treo?

4. Are there any contact managers that support syncing for a Palm that rival Act! on Linux?

5.  Anything else I should know?

Thanks
Jim

---

### Post by Perfect Storm on 2006-10-30
2. usually when you uninstall things via synaptic/ap-get/aptitude eveything is removed. But the downloaded packages are still saved if you need them. A quick "sudo apt-get clean" should do it. YOu might also check your home folder for user saved settings for a specific application you don't use anymore.

4. You might get Dapper instead of edgy. Dapper is long time supported and well....edgy is a bit edgy ;)

---

### Post by jkvv_1973 on 2006-10-30
Sounds like you have to dual boot...and wait till they do make programs you use in linux...but it would be good for you to try out Ubuntu for evaluation purposes...I have a dual boot right now and cant seem to find a definite reason why I should wipe xp out just yet...nonetheless Ubuntu rox:mrgreen:

---

### Post by moshuptrail on 2006-10-30
I second that.
Also, install Dapper.  Judging from all the posts I see, there are still a few *issues* with edgy. :-)

---

### Post by MattJ100 on 2006-10-30
I third it.

Though I've had no problems with Edgy, but as a new user, I think Dapper is the wiser choice.

---

### Post by SunnyRabbiera on 2006-10-30
Yeh Dapper might be better for you.
Anyhow with any linux there is no 100% guarentee on hardware compatibility, especially with palms.
Now ubuntu has a palm applet but I am not sure what it covers.
As for program installation and uninstallation well synaptic is the program for you if you want to 100% remove software, synaptic has a pretty good software installer that really kicks butt.
As for MP3's well MP3's will be tricky on linux, as MP3 is proprietary there are issues with it on linux distros, but you can get them to work.
There is a program called automatix that can do the job for you though there is a risk that it might mess up something.
There are several apps in linux that can pretty much replicate most windows apps.
XMMS is like winamp
Rhythmbox and Amarok are like Itunes
Xine is like Win DVD
so on, so on.
Just remember: dont expect linux to have everything windows has, they are different opertating systems with different ideals.
They both have thier flaws and merits, but if you come in here expecting linux to be 100% like windows you are barking up the wrong tree.

---

### Post by MattJ100 on 2006-10-30
> Just remember: dont expect linux to have everything windows has, they are different opertating systems with different ideals.
They both have thier flaws and merits, but if you come in here expecting linux to be 100% like windows you are barking up the wrong tree.

I disagree. That comment would have put me off trying Linux. As it is, I tried it, and now I'm firmly stuck. ALl the apps I thought I'd miss I have found equivalents for (some are even better!). I think the only way to find out is to try it out with the LiveCD and dual-boot. Linux is not just for the elite :) Windows ussers *can* use Linux (especially Ubuntu) fine.

---

### Post by SunnyRabbiera on 2006-10-30
Well the thing is that most new people do go to linux in hopes it will fully replace windows.
In all honesty it wont, but it can be a good alternative.
I always try to promote linux as a windows alternative not replacement.

---

### Post by Paul133 on 2006-10-30
I 5th Dapper. Edgy doesn't have that many advantages for a new user.

---

### Post by Straight Shooter on 2006-10-31
Thank you all for the replies. Would someone post a link for Dapper? I want to make sure I get the right version. I hope I don't get 5 different links LOL..

Jim

---

### Post by mahy on 2006-10-31
> **Straight Shooter said:**
> Thank you all for the replies. Would someone post a link for Dapper? I want to make sure I get the right version. I hope I don't get 5 different links LOL..

Jim

[http://www.ubuntu.com/products/GetUbuntu/download#lts](http://www.ubuntu.com/products/GetUbuntu/download#lts)

---

### Post by pelle.k on 2006-10-31
> As for MP3's well MP3's will be tricky on linux, as MP3 is proprietary there are issues with it on linux distros, but you can get them to work.'
I wouldn't exactly call it tricky. but a bit diffrent than installing codecs in windows.

1. Run "gksudo gedit /etc/apt/sources.list" in a terminal, find the section which says
```
##Uncomment the following lines to add software from the universe repository
``` add "multiverse" beside the two lines that end with "universe". Also make sure theres no hash (#) in front of those lines.
This step will also open up your list of repositories, so you will now have even more applications to chose from in synaptic.

2. Run synaptic (run update) and install libxine-extracodecs (now you have mp3 support in _all_ applications wich use xine as an engine), and gstreamer0.8-mad (mp3 support for most  'dapper' appz that use gstreamer as engine).

Still think this is too much work to install mp3 support? You forget that all apps installed this way will always update themself to a new version (if one is availiable), everytime you update synaptic. No more uninstall, download new version, install procedure like in windows.

Also, i would rather install beep-media-player than xmms, if i wanted an alternative to winamp. Only because xmms is, well... not gtk and thus rather ugly. This is a personal preference though.
If you want a fully featured music player, i highly recommend amarok.

---

### Post by Straight Shooter on 2006-11-03
Thanks to everyone. The only issue I have is that I believe the Sony Sonic Stage software is proprietary, I don't know if all the other stuff from Linux will work.. 
Jim

---

