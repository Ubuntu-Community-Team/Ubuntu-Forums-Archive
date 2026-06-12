---
title: "Don't try ubuntu on new Dell Vostros"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by tashmooclam on 2007-08-02
I had no success loading ubuntu 7.04 on a brand new dell vostro 1500 laptop.
I googled the error message and see it is perhaps common. People were posting on the dell ubuntu forum about it, among other places.
I called Canonical service and without buying the service for $250/year, I heard this is not unheard of in brand new systems. It seems to relate to the hard drive.
I WAS able to switch my "service contract" at Dell to be ubuntu not windows xp home. 
If the fix sounds difficult, I'll have to return the laptop.
Too bad, the thing is beautiful to look at. 
Even AFTER doing the "text install", the ubuntu at boot up gives a black screen. 
Moral: Install Ubuntu on systems that have been around a little while.

---

### Post by nichipet on 2007-08-02
Before I bought my laptop a couple of weeks ago, I looked very briefly at the Vostro 1700. Same monitor size, other specs about the same or better than what I bought, and noticably cheaper. But, since it just came out and I had not seen any success stories of Linux/Ubuntu being installed, I held off and went with the laptop that came preinstalled with Ubuntu.

I'm sorry you went through this with the Vostro, but now I'm glad I decided against buying one.

Edit: I just went to Dell's website, customized a Vostro 1700 and priced it. Including tax, it came out to just $9 less than I spent on my Ubuntu laptop.

---

### Post by daveyiv on 2007-08-02
> **tashmooclam said:**
> I had no success loading ubuntu 7.04 on a brand new dell vostro 1500 laptop.
I googled the error message and see it is perhaps common. People were posting on the dell ubuntu forum about it, among other places.
I called Canonical service and without buying the service for $250/year, I heard this is not unheard of in brand new systems. It seems to relate to the hard drive.
I WAS able to switch my "service contract" at Dell to be ubuntu not windows xp home. 
If the fix sounds difficult, I'll have to return the laptop.
Too bad, the thing is beautiful to look at. 
Even AFTER doing the "text install", the ubuntu at boot up gives a black screen. 
Moral: Install Ubuntu on systems that have been around a little while.

it works fine, just have to jump through a few hoops. in your /etc/X11/xorg.conf change your display driver from nv to vesa to start off with and you will be able to boot into X.

---

### Post by tashmooclam on 2007-08-03
It won't install from a DVD except with the text install.
I did the text install, what a pain.
I can start up and choose ubuntu or windows.
Then, when it starts up there is a BLACK SCREEN.
So, I don't know where/how to make any adjustments.
The "word" is that the SATA drives have chips that the core linux can't work with, or something, I really don't know/care.
Thanks for the tip, I'm getting rid of it. I loved it and then after fooling around for 2 days, now I actually **hate** it.

---

### Post by ayu on 2007-08-07
> **tashmooclam said:**
> It won't install from a DVD except with the text install.
I did the text install, what a pain.
I can start up and choose ubuntu or windows.
Then, when it starts up there is a BLACK SCREEN.
So, I don't know where/how to make any adjustments.
The "word" is that the SATA drives have chips that the core linux can't work with, or something, I really don't know/care.
Thanks for the tip, I'm getting rid of it. I loved it and then after fooling around for 2 days, now I actually **hate** it.

> **daveyiv said:**
> it works fine, just have to jump through a few hoops. in your /etc/X11/xorg.conf change your display driver from nv to vesa to start off with and you will be able to boot into X.

Hi daveyiv,

Could you please post a quick guide on how you did the install?  I've played around with Ubuntu a little before, so I'm not totally clueless.  But when I try the regular Feisty install cd on the 1400, it gives a tty error, even with the safe mode graphics.  Did you use the alternative cd or something else?  I would like to avoid downloading another large file if possible.  Also, what partitions did you keep?  I would like to leave vista on there.

Thanks in advance!

---

### Post by ayu on 2007-08-08
> **ayu said:**
> Hi daveyiv,

Could you please post a quick guide on how you did the install?  I've played around with Ubuntu a little before, so I'm not totally clueless.  But when I try the regular Feisty install cd on the 1400, it gives a tty error, even with the safe mode graphics.  Did you use the alternative cd or something else?  I would like to avoid downloading another large file if possible.  Also, what partitions did you keep?  I would like to leave vista on there.

Thanks in advance!

Hmm, that was strange.  I've tried following this guide [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588) twice before making the above comment, yet when I tried it again today it managed to load the live cd!  Installing now yay! :)

---

### Post by cherry316316 on 2007-08-11
> **ayu said:**
> Hmm, that was strange.  I've tried following this guide [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588) twice before making the above comment, yet when I tried it again today it managed to load the live cd!  Installing now yay! :)


hi , I am new baby on linux n i run into same problem, i followed the link , u have given , but didnt get quite which part i am supposed to use, 
i tried that "break=top"
and then my system went into eternal blank and also the cd stopped rotating in the drive,

can u tell me did u also got the same problem , also , i was trying to instal 64 bit ubunto 7 on my vostro 1500

and if possible , can u tell the steps u used to get ride of problem

thanks

---

### Post by pilate on 2007-08-11
I'm having this problem also. Haven't tried the text based install yet, but I have tried the "break=top" solution. I get more errors that say something about xserver not being able to load. 
Any one have some advice?

---

### Post by cherry316316 on 2007-08-11
> **pilate said:**
> I'm having this problem also. Haven't tried the text based install yet, but I have tried the "break=top" solution. I get more errors that say something about xserver not being able to load. 
Any one have some advice?



i tried the text based also , and at 1st , i got the ray of hope , as the installation process went quite good , but after some time , it again gave me errors , 
and now i dont have ubuntu install and also , my mbr is disturbed , so cant boot win also , 
its saying , "error loading operating system"

---

### Post by pilate on 2007-08-11
> **cherry316316 said:**
>  it again gave me errors , 
and now i dont have ubuntu install and also , my mbr is disturbed , so cant boot win also , 
its saying , "error loading operating system"

Thanks. I guess I'll just wait until some one figures out a real fix.
I'll be on windows until then I guess.

---

### Post by cherry316316 on 2007-08-11
> **pilate said:**
> Thanks. I guess I'll just wait until some one figures out a real fix.
I'll be on windows until then I guess.

I was finally able to install debian , i had my lan wire connected and the installation went smooth

current state , at the start up , i can select my win and log into that , so win is working.

debian:  when i try to log into debian  , it again tells me , xserver not found,
i get the command prompt then.

i used this command
[COLOR="Orange"]apt-get update
apt-get install xserver[/COLOR]

after the 2nd command i get this out put
[COLOR="Orange"]
Reading package lists ... Done
Building dependency tree ... Done
Package xserver is a virtual package provided by:
   xserver -xorg-core 2:1.1.1-21
   vncserver 3.3.7-14
   vnc4server 4.1.1+X4.3.0-21
   tightvncserver 1.2.9-21
You should explicitly select one to install
E: Package xserver has no installation candidate[/COLOR]


anyone has idea what to do ,
i also tried the command
apt-get install xserver-xorg 
and combinations like this but no use :(



then i checked the xserver error
and it says

Fatal server error: no screens found

what does this means ?

---

### Post by jmnormand on 2007-08-11
It is definately do able but does take a bit of work on the command line and the alt install cd.  just try the howtos of the 1420/1520 as they have very similar setups.  I can say that they are coming along quickly so it should not be long before they are running from the live cd.

[http://ubuntuforums.org/showthread.php?t=509408&highlight=1420](http://ubuntuforums.org/showthread.php?t=509408&highlight=1420)  should help with alot of the issues.

---

### Post by ayu on 2007-08-12
> **cherry316316 said:**
> hi , I am new baby on linux n i run into same problem, i followed the link , u have given , but didnt get quite which part i am supposed to use, 
i tried that "break=top"
and then my system went into eternal blank and also the cd stopped rotating in the drive,

can u tell me did u also got the same problem , also , i was trying to instal 64 bit ubunto 7 on my vostro 1500

and if possible , can u tell the steps u used to get ride of problem

thanks

Hello,
I'm not sure if this will help and if you're going to give Ubuntu another shot as you've already installed Debian, but I have 32 bit Ubuntu installed on my 1400.  Make sure you type  "break=top" after the " -- " when you hit F6 to enter boot options.  A command prompt should load and then you can follow the rest of the guide.  When you enter "modprobe piix", it shouldd't give any errors, at least it didn't for me when I did it correctly.  I've also heard the text installer on the alternative CD works, but I didn't want to download another iso.

---

