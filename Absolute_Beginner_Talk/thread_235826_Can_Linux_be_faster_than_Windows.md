---
title: "Can Linux be faster than Windows?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by FariAzz on 2006-08-13
Hi, I installed Kubuntu some weeks ago and in my computer is much slower than Windows XP. I have both OS installed and when I turn my PC on, it takes like 3 times longer to get to Linux than to get to XP. The programs in Kubuntu are also slower than in Windows, like Open Office takes an eternity to open.

Anyone knows how to speed it up?

I have a +2600 Semprom with 256 RAM.

---

### Post by aysiu on 2006-08-13
> **FariAzz said:**
> 
Anyone knows how to speed it up? Yeah. Use Xubuntu (*xubuntu-desktop*) and BUM (*bum*).

1. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

2. ```
sudo aptitude update
sudo aptitude install xubuntu-desktop bum
gksudo bum
```

3. Log out. Select **Session** > **XFCE**. Log in.

---

### Post by FariAzz on 2006-08-13
would that unistall Kubuntu and KDE??

---

### Post by Frostmourne on 2006-08-13
Nope, you would just reselect KDE from the Session menu to get back to it.

---

### Post by westep23 on 2006-08-13
no It will install beside it.

---

### Post by FariAzz on 2006-08-13
Can I run the same KDE applications in Xfce?

---

### Post by bhoughton on 2006-08-13
You can also try Gnome.  In my experience, KDE seems to be more memory intensive.  I believe that 

sudo aptitude update
sudo aptitude install ubuntu-desktop

will give it to you

---

### Post by louistan3 on 2006-08-13
you could update your kernel to "linux-k7"

its for amd cpu's.. a bit of optimizations.. theres a post somewhere in the forums.. i thnk its on the howto section.. il try to find it and post here the link.. :)

---

### Post by Kilz on 2006-08-13
> **FariAzz said:**
> Can I run the same KDE applications in Xfce?
For the most part KDE and gnome applications will run on the Xfce
desktop. Xfce is a lightweight environment. Its super fast on modern processors. The applications may not look as good in some cases, but they will run.
But let me address your original post while I'm at it. You compare a Linux desktop (KDE) to Windows XP. While its true that XP appears to boot into the desktop faster. It is usually a bit longer before you can actually use the applications. The taskbar and things are loading in the background and you cant do anything. On a Linux desktop when you see it you can use it. Also OpenOffice is the absolutely slowest thing to load, either on Linux or Windows. If you are comparing OpenOffice on Linux to MS office on Windows you are comparing apples to oranges.

---

### Post by noynac on 2006-08-13
> **Kilz said:**
> ...If you are comparing OpenOffice on Linux to MS office on Windows you are comparing apples to oranges.

I used Firefox and OpenOffice in Windows, and I'm now running the same programs in Ubuntu. I find that these programs loaded a smidgeon faster in Windows than in Ubuntu, but the difference is not sufficient to be a factor in deciding on an OS. Once the programs are loaded, I notice no difference.

I do agree that Ubuntu Linux takes a bit longer to start-up and shut-down but I do that once or twice a day.  

noynac

---

### Post by Kilz on 2006-08-14
> **noynac said:**
> I used Firefox and OpenOffice in Windows, and I'm now running the same programs in Ubuntu. I find that these programs loaded a smidgeon faster in Windows than in Ubuntu, but the difference is not sufficient to be a factor in deciding on an OS. Once the programs are loaded, I notice no difference.

I do agree that Ubuntu Linux takes a bit longer to start-up and shut-down but I do that once or twice a day.  

noynac

IMHO The startup/shutdown depends on what you are looking at. Are you looking at when the desktop shows or when you can do something. 
My wife refuses to use Linux, She has her own computer that is simalr to mine. While the startup screen may take a little longer in Ubuntu. Once Im loged in I can open an application.
My wife on the other hand gets to log in faster. But then must wait as anti virus, anti spyware, the firewall, ect to start. Clicking on an application doesnt start it. She has to wait. 
Her system is a clean one to. I could imagine if I didnt clean out all the garbage that creeps in no matter what anti things are installed. 
If we start our computers at the same time, Im actualy doing somthing as she waits. Granted the shutdown is longer. But from what I have read Edgy will be addressing that. The Teardown feature they are working on will speed up turning Ubuntu off.

---

### Post by PaulFXH on 2006-08-14
In response to the original question "Can Linux be faster than Windows?", I can boot to either Ubuntu Dapper, SimplyMEPIS 6.0 or WinXP on my machine.
Although I've only been using Linux for less than one month, I am very impressed with many of its features (especially the absence of frequent virus and spyware checks) and rarely use WinXP nowadays.

I particularly find that both Linux versions appear much more nimble than does WinXP.
In terms of start-up (from "flick the switch" to "ready to use" including logins) WinXP requires 135 seconds and 25 seconds to shutdown.
OTOH, Dapper starts up in 55 seconds and also takes 25 to shutdown.
MEPIS starts up in 100 seconds and needs 27 to shutdown (although do note that I boot MEPIS from a usb hd through a boot cd).
All-in-all, therefore, in respect of the original question, in my case the response is a resounding "Yes".

My machine is a Dell 4550 with a 2.53GHz CPU and 1GB of RAM.

Paul

---

### Post by Pawka on 2006-08-14
I'm using Ubuntu, because it works faster than Windows on my laptop. My machine is old enough: 450 Mhz CPU, 256 Mb RAM..., so I was using Windows 2000. Maybe w2k boots a bit faster, but with w2k also I need use antivirus, firewall, antispyware, what makes Windows more and more slower. On Ubuntu (actualy Xubuntu) I can work without all this stuff.

Btw, someone there writes try Gnome instead KDE. I don't think so, that Gnome is faster than KDE. When I've installed Dapper from live cd (remember, my computer is old), I can't finish Ubuntu (with Gnome) installation, because it eats all RAM and my machine hangs-up. When i've tryed install from Kubuntu live CD, everything works fine. So Gnome eats more RAM than KDE, but best choose for maximum performance is XFCE :-)

---

### Post by 3rdalbum on 2006-08-14
If you want to improve your computer's performance, you really must add memory. Ubuntu, being years more advanced than Windows, does prefer more memory.

Having said that, Windows is painfully slow on my similar-spec computer. Try using BUM as suggested to disable some startup services. Also, if you've got Beagle set to index your home directory in the background, disable it for a noticable speed boost.

I used to doubt that Windows was still loading after the desktop appears, but it's definately true. Try double-clicking on My Computer as soon as the desktop appears, and time how long it takes to display the window.

---

### Post by xpod on 2006-08-14
Dual boot Xp and ubuntu..

Xp..is stripped down to run as fast as poss with all the unwanted services killed off and all the bells and whistles dumbed down......

I dont use open office etc (yet) BUT everything i do on ubuntu is a lot faster seeming than XP....

Ive had a couple of moments when Ubuntu has slowed down for some reason but i havent yet learned ALL the tip`s n tricks for this as i had with XP(early days)

My xp is still loading it`s AV and Zonealarm etc BY time this is on & apt-GOTsome other wonder for me to try.
Aint "timed" them as i KNOW this is a lot lot quicker than the XP at doing the basic stuff i do with it...

Will be looking at that BUM you mentioned 3rdalbum and having a closer look at what`s running that dont need to be....(that just dont sound right:-))

---

### Post by Frank Golden on 2006-08-14
> **3rdalbum said:**
> If you want to improve your computer's performance, you really must add memory. Ubuntu, being years more advanced than Windows, does prefer more memory.

Having said that, Windows is painfully slow on my similar-spec computer. Try using BUM as suggested to disable some startup services. Also, if you've got Beagle set to index your home directory in the background, disable it for a noticable speed boost.

I used to doubt that Windows was still loading after the desktop appears, but it's definately true. Try double-clicking on My Computer as soon as the desktop appears, and time how long it takes to display the window.

More memory indeed.
My dual boot laptop boots both Ubuntu and XP in about 70-80 seconds. Programs seem to run pretty quick in Ubuntu. As a matter
of fact copying large files is much quicker in Ubuntu. I do have 2GB of ram however and a Core Duo processor.
I bet a moderate increase in ram would help. Increase to 1GB
maybe. I do have a busy install.

---

### Post by Jeroen Vernooij on 2006-08-14
From powerbutton to GDM loginscreen is 34.3 sec for Ubuntu with 686-kernel on my computer.

With the default kernel this was 37.9 sec.
I'm able to fully login within 50 sec (short username+password). 
This is even without BUM, on a freshly installed 6.06.


You should install a 686 kernel, and maybe try Xubuntu. Also Edgy will be faster than Dapper.

Is your Hard-disk LED flashing? This can be a sign that your RAM is all used.

---

### Post by Lord Illidan on 2006-08-14
Try Zenwalk Linux instead.

[www.zenwalk.org](www.zenwalk.org)

It flies :)

---

### Post by FariAzz on 2006-08-14
> **louistan3 said:**
> you could update your kernel to "linux-k7"

its for amd cpu's.. a bit of optimizations.. theres a post somewhere in the forums.. i thnk its on the howto section.. il try to find it and post here the link.. :)

HELP!! I installed linux-k7 from Adept, now I can't log on into Linux anymore, I type my username and password and it redirects me to the same windows over and over again... I tryed with my old kernel "386" and I still can't log on.

---

### Post by Lord Illidan on 2006-08-14
> **FariAzz said:**
> HELP!! I installed linux-k7 from Adept, now I can't log on into Linux anymore, I type my username and password and it redirects me to the same windows over and over again... I tryed with my old kernel "386" and I still can't log on.

Did you install anything else?

---

### Post by FariAzz on 2006-08-14
No, just the kernel, then I reboot the computer and can't log in anymore..

---

### Post by cvmostert on 2006-12-05
I am installing bum and xubuntu, we will see if it really is faster. Hopefully there is a way to uninstall the xubuntu-desktop without hurting any other apps.... eek! did not think of that... but it should work. :-)

---

### Post by aysiu on 2006-12-05
If you want to uninstall Xubuntu later, make sure you install it this way: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` and then, when you want to uninstall it, use this command: ```
sudo aptitude remove xubuntu-desktop
```

---

### Post by bodhi.zazen on 2006-12-05
Errr....

Linux out performs windows no problem. Not even close....

---

### Post by xpod on 2006-12-05
lol...I can spell Ubuntu now since my last post in this here thread and thankfully the xp that was ...is no more.

Now THAT was the fastest i`d ever seen it go:mrgreen:

---

