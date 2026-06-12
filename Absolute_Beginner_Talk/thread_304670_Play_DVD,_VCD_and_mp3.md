---
title: "Play DVD, VCD and mp3"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by mr_hervin on 2006-11-22
hi I'm damn new for Linux os and this is my fist try on ubuntu.
i successfully install os to my pc. now im encounter some errors when play mp3 or dvd. is there any decorders i need to download ??

---

### Post by rigol on 2006-11-22
Have a look at this: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
For DVD also here: [https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/video.html) if you are using Dapper, for Edgy here: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/codecs.html)

Does this solve your problem?

---

### Post by judgejudy on 2006-11-22
> **mr_hervin said:**
> hi I'm damn new for Linux os and this is my fist try on ubuntu.
i successfully install os to my pc. now im encounter some errors when play mp3 or dvd. is there any decorders i need to download ??

the easy thing to do is use automatix it installs every thing you will need you can get it from  [http://www.getautomatix.com/](http://www.getautomatix.com/) :-D  its a copy and paste and works well

---

### Post by Bachstelze on 2006-11-22
> **judgejudy said:**
> the easy thing to do is use automatix it installs every thing you will need

And will break everything else...

---

### Post by arnieboy on 2006-11-22
> **HymnToLife said:**
> And will break everything else...

just stop spreading this crap in every thread..

---

### Post by judgejudy on 2006-11-22
> **HymnToLife said:**
> And will break everything else...

never has for me it just works, and if it was not for automatix a nube like me would never stick with ubuntu. so if you think its bad why dont you make a better one?:evil: untill then for us newbies automatix is a god send

---

### Post by Dale61 on 2006-11-22
> **HymnToLife said:**
> And will break everything else...

Never had a problem with Automatix.  In fact, I have Automatix on my desktop and Automatix2 on my laptop, both running 6.06.

If it wasn't for Automatix, I wouldn't have kept Dapper installed for as long as I have.

If you have had such a bad experience with Automatix, why not tell everyone EXACTLY what your problems have been.  Maybe you encountered an id 10 t error!

---

### Post by Doug11 on 2006-11-22
I was looking for some mp3 support, clicked on the first link at the top of this thread and had it within a  couple minutes. Can't imagine it being much easier than that.

---

### Post by mr_hervin on 2006-11-23
WEll,,as i told earlier i'm new to this linux platform and totaly blank knowlage on this..
 where to download the codecs ? url plss.... 
how to install it???

---

### Post by Bachstelze on 2006-11-23
> **arnieboy said:**
> just stop spreading this crap in every thread..

I guess the number of Automatix-related problems we get here is pretty self-explanatory...

---

### Post by f76 on 2006-11-23
U need to run some command line to get automatix to install as far as i know. Linux is not just klick and install - and for good reason, its safer this way. 

follow the guide on getautomatix.com. I pasted it below here. if u need any help i am here for a while and can guide u step by step.
*************************************

Edit your sources.list:

sudo gedit /etc/apt/sources.list

Substitute gedit with the text editor of your choice.

Add the following to your sources.list:

NOTE: Xubuntu users will need to uncomment all the additional sources as well as add the automatix repository.

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

Next you must get our GPG key in order to authenticate our repository:

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

To finish off:

sudo apt-get update
sudo apt-get install automatix

Xubuntu users will also need to install Zenity:

sudo apt-get install zenity

Run Automatix either with the command "automatix" or by its launcher in Applications>System Tools>Automatix.

---

### Post by Dondon2d on 2006-11-23
never had problems.. thanks, now it's better..

---

### Post by AndyCooll on 2006-11-23
> **mr_hervin said:**
> WEll,,as i told earlier i'm new to this linux platform and totaly blank knowlage on this..
 where to download the codecs ? url plss.... 
how to install it???

As an earlier post indicated, click on the link about Restricted Formats (it's also in my signature). Follow the instructions, they are pretty self-explanatory and take you through the process of installing the relevent "w32codecs" codecs. It's quite a long document so you'll need to read through quite a bit of it to get to the parts that are relevent to you (though there is a "Contents" list on the right-hand side).

:cool:

---

### Post by EmanuilTolev on 2006-11-28
> **arnieboy said:**
> just stop spreading this crap in every thread..


Well, Automatix isn't an app that complicated. It's not foolproof I mean. I myself WAS able to break it for 30 minutes of playing with multimedia packages and after that even the app itself didn't know what was installed and what wasn't :D. But I did it intentionally, I mean it's not perfect, but it's not stupid too ('crap' is out of question).

---

### Post by arnieboy on 2006-11-28
> **EmanuilTolev said:**
> Well, Automatix isn't an app that complicated. It's not foolproof I mean. I myself WAS able to break it for 30 minutes of playing with multimedia packages and after that even the app itself didn't know what was installed and what wasn't :D. But I did it intentionally, I mean it's not perfect, but it's not stupid too ('crap' is out of question).
nothing is perfect, least of all linux itself.

---

### Post by xpod on 2006-11-28
Automatix has probably prevented many many people giving up and trailing off back to windows with a head full of confusion i reckon.

Usually it`s people who mess up as apose to automatix is it not??...or any other app come to that.:-k

---

