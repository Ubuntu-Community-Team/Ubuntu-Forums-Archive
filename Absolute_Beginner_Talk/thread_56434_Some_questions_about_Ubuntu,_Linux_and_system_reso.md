---
title: "Some questions about Ubuntu, Linux and system resources"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by sls on 2005-08-12
I am not sure if this is the right forum or not.  I am certainly not a computer newby and I have, in fact, sat at a Unix box compling/debugging code.  But I have never successfully set up a Linux or Unix system ... until last night when I put Ubuntu Linux on an old Dell system I had in the basement (PII 233mhz, 128mb of RAM, 8gb HD).

I want to set up this system for my 8 year old son to play games on and get on the internet (he is currently enamored with Yu-Gi-Oh and Pokemon).  I run Win2K on all the computers on my home netwok (currently 6) because I like the relative stability and control I have with it, as well as the ease of use and networking.  I put Linux on this system for two reasons, 1)  because I had the slight misconception that it could handle Linux better that Win2K (I do not want to go back to Win98se) and 2) because I have really wanted to dive in to the Linux pool for a while now and this seemed like a good chance.

Well, it is running pretty slow, my son doesn't mind of course, but it is driving me nuts.  I KNOW that I would have very little recourse if this were Win2K.  There is a lot in the standard install of Ubuntu Linux that I'm sure I don't need for this system since it really won't be used for much other than an Internet appliance.

My question is how can I reduce the system resource needs and, hence, speed up this system?  Windows has a whole bunch of processes running that most users have no idea about, does Linux have anything similar that can be looked at, if so how?

I also read here that the both the GNOME and KDE desktops need a lot of resources to run.  Can I just get a leaner desktop that doesn't have all the bells and whistles?  If that is the case, would I have to give up Ubuntu and use another distro or would I just be able to run that instead?  I really like the ease of installation and the package management with Ubuntu, but I don't know what other distro's are like.

I guess that's enough questions for now...

---

### Post by KingBahamut on 2005-08-12
[QUOTE=sls]I am not sure if this is the right forum or not.  I am certainly not a computer newby and I have, in fact, sat at a Unix box compling/debugging code.  But I have never successfully set up a Linux or Unix system ... until last night when I put Ubuntu Linux on an old Dell system I had in the basement (PII 233mhz, 128mb of RAM, 8gb HD).

I want to set up this system for my 8 year old son to play games on and get on the internet (he is currently enamored with Yu-Gi-Oh and Pokemon).  I run Win2K on all the computers on my home netwok (currently 6) because I like the relative stability and control I have with it, as well as the ease of use and networking.  I put Linux on this system for two reasons, 1)  because I had the slight misconception that it could handle Linux better that Win2K (I do not want to go back to Win98se) and 2) because I have really wanted to dive in to the Linux pool for a while now and this seemed like a good chance.

Well, it is running pretty slow, my son doesn't mind of course, but it is driving me nuts.  I KNOW that I would have very little recourse if this were Win2K.  There is a lot in the standard install of Ubuntu Linux that I'm sure I don't need for this system since it really won't be used for much other than an Internet appliance.

My question is how can I reduce the system resource needs and, hence, speed up this system?  Windows has a whole bunch of processes running that most users have no idea about, does Linux have anything similar that can be looked at, if so how?

I also read here that the both the GNOME and KDE desktops need a lot of resources to run.  Can I just get a leaner desktop that doesn't have all the bells and whistles?  If that is the case, would I have to give up Ubuntu and use another distro or would I just be able to run that instead?  I really like the ease of installation and the package management with Ubuntu, but I don't know what other distro's are like.

I guess that's enough questions for now...[/QUOTE]
 4 letters. 

XFCE. 

I am of course, a fan. 

And if you have ever used a Solaris box, XFCE comes real easy.

---

### Post by sls on 2005-08-12
How would I install that?  What do I download?

---

### Post by sophtpaw on 2005-08-12
[QUOTE=sls]How would I install that?  What do I download?[/QUOTE]


[http://www.xfce.org/](http://www.xfce.org/)

go to download - looks pretty straightforward

---

### Post by aysiu on 2005-08-12
Wouldn't it be easier to do this?

[i]sudo apt-get update
sudo apt-get install xfce4[/i]

---

### Post by sophtpaw on 2005-08-13
[QUOTE=aysiu]Wouldn't it be easier to do this?

[i]sudo apt-get update
sudo apt-get install xfce4[/i][/QUOTE]


Always listen to a brewmaster over a total newbie like myself  :smile:  i was only trying to do my best to be helpful  :???:  sigh...

--
sophtpaw

---

### Post by Lord Illidan on 2005-08-13
> Always listen to a brewmaster over a total newbie like myself i was only trying to do my best to be helpful ??: sigh... 

Aw cheer up, we all make mistakes...

---

### Post by sophtpaw on 2005-08-13
[QUOTE=aysiu]Wouldn't it be easier to do this?

[i]sudo apt-get update
sudo apt-get install xfce4[/i][/QUOTE]

I'm very happy with Gnome as my system has the resources to deal with a Gui of this size, however, having followed the thread i was curious to follow through and see what an alternative like xfce looks like.
Hence i followed your above instructions but am left wondering now how to run it?
And would it affect my Gnome? or can i just get out of xfce and return to Gnome so much as easirly exiting a normal application?

Please advise me,

thank you,

sophtpaw

---

### Post by 23meg on 2005-08-13
in the login screen choose xfce from the session menu, and you'll log in to xfce. log out and choose gnome, and you're back in gnome. all your gnome settings will be kept. 

first time you try to log in to xfce you'll also be asked if you want to make it the default session, so that you won't have to choose it from the sessions menu each time.

---

### Post by sophtpaw on 2005-08-13
[QUOTE=23meg]in the login screen choose xfce from the session menu, and you'll log in to xfce. log out and choose gnome, and you're back in gnome. all your gnome settings will be kept. 

first time you try to log in to xfce you'll also be asked if you want to make it the default session, so that you won't have to choose it from the sessions menu each time.[/QUOTE]


Thank you, thank you, thank you!

XFCE looks real nice!

I might just make this home for a while and explore it further. Do you, or does anyone know if there is a forum or somewhere that supports questions specific to XFCE? For one the mail tab in the panel brings up a web browser instead of evolution. Also, i haven't found Synaptic install manager. (only update). Otherwise, it looks real neat and i would recommend anyone wishing to explore from a different environment, checking this out.

Enjoy,

sophtpaw

---

