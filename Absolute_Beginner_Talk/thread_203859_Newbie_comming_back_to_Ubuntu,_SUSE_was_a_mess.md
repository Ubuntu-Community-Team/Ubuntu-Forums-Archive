---
title: "Newbie comming back to Ubuntu, SUSE was a mess"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-06-26
I originally set out to install Ubuntu but after doing some research I decided that I wanted the full bloated OS experience to help me migrate from Microsoft. I installed SUSE 10.1 and have spent over 100 hours trying to make it work to my satisfactaion with almost zero  luck. ( I have almost all hardware that Linux hates ) I was able to get my wireless working ( Posting from SUSE now ) using the ndiswrapper for broadcom and it worked great.. but I cannot find a wireless network manager that works. KWiFiManager blows, also I have been having zero luck loading dhcp on boot so every time I boot I must go to the terminal and type dhcpcd wlan0  about 5 times to get my Internet working. I think I will have better luck with Ubuntu because of the exellent support provided here in the forums. I have also seen many posts from previous dedicated SUSE users saying that 10.1 is just plain buggy.. and thats from experainced SUSE users. I dont post in any forum often because I use Google and search forums extensively and can almost always find what I am looking for.  I just wanted to share my SUSE experience and say that I look forward to reading the posts here again. ( freindly environment ) I am very busy right now with my job so I wont be able to start my Ubuntu install until Thursday. I look forward to bugging you people with questions.

Peace
Rich

---

### Post by simone.brunozzi on 2006-06-26
Rich,
unfortunately for you, I confirm that SuSE is very, very buggy.
Dapper Drake, after the stable release, is very decent. Much better than Fedora too. :-)

Cheers,

---

### Post by ajgreeny on 2006-06-26
Hi Rich,  Welcome to ubuntu.

I've tried several distro's over the past 15 months and always come back to Ubuntu (actually Kubuntu in my case) but I can't find anything to touch it in any way.  These forums are second to none, and you will nearly always find an answer to your difficulties here, either by a search, or if that fails by starting a new thread, but do always search carefully first with a few different search terms, as it can be interesting to see where answers eventually come from some times.

I agree Suse is not as user friendly as ubuntu, and I found yast incredibly slow in comparison to apt-get or synaptic for software installation, and not as great as everyone suggested for other configuration tasks.

Good luck with this great distro!

---

### Post by Rich3077 on 2006-06-26
Man what a mess, I experianced lock ups from the GUI and the terminal screen. Once the GUI locked up it corrupted some files and from there on I was pretty much screwed.
All of this was from a standard default install.. no fancy 3D desktop. I thought this kind of behavior was limited to Microsoft? Well anyway I am sure my Ubuntu install will go much better simply because it could not possibly be worse. The last time I tried Linux ( Mandarake 8.0 ) years ago it was better than my SuSe install. 
I cant wait to play Q3A on Linux!!!! If anyone here has a Q3A server and doesnt mind a rusty nOOb I would appreciate an invite.  :mrgreen: 


Peace
Rich

---

### Post by FredB on 2006-06-26
[QUOTE=simone.brunozzi]Rich,
unfortunately for you, I confirm that SuSE is very, very buggy.
Dapper Drake, after the stable release, is very decent. Much better than Fedora too. :-)

Cheers,[/QUOTE]

It seems that RPMs based distros are more dirty in use than debian based ones.

---

### Post by Rich3077 on 2006-06-29
I did it!!  Posting from Ubuntu now.. a day early even!  :D 
I am not trying to anger any SuSE people, but it wasnt for me. I had a lot of problems, and I made a post in the SuSE forums about my last (critical) problem and an admin said their was no easy fix for my problem so I just inserted a Ubuntu CD and started fixing my problems for good. Install went well.. one minor hiccup..
graphic interface would not load.. boot back to Windows to search the Ubuntu forums for a fix.. found one instantly.. back to Ubuntu. Ubuntu is damn fast, much faster than my SuSE install and even boots much faster.. but damn,.. no internet with my Broadcom card.. back to Windows to search the forums for a fix and 20 minutes later I am making this post. :KS  I was not able to get Grub to boot Windows XP in SuSE even after reinstalling it a few times. Ubuntu got it right the FIRST time.
This is important because my wife and kids will want to boot into Windows. I think I am through with Windows myself. To put icing on the cake I LOVE the new hard drive I picked up for my Linux install.. it quite as hell.. no more damn hard drive grinding niose. 

Many thanks to all you fine people in the forums that have helped me and didnt know it. ( because I use the search feature a lot ) 
I am now off to install drivers for my 3D card and reinstall Quake 3!! 

Peace
Rich

---

### Post by rmwarriner on 2006-07-19
I agree Ubuntu (Dapper in my case) is sweet. I have tried various distros in the past over the last 10 years and I have to say I am happiest with this one. The only reason I still have Winbloze is my wife uses it (on her laptop) and I need it to run some of the more graphic-intensive FPS and sims (I suppose that doesn't make me a *true* Linux geek, but I have to face reality).

Right now I have it running a LAN from gateway to router with only a few minor issues (mainly from my own ignorance). I tried Suse before this (and Slackware) and ran into nothing but problems. Yast is certainly much, much slower than apt-get. If you have multiple systems running Ubuntu the definatly install and use a apt caching system (apt-cacher or apt-proxy, both work well although I prefer apt-proxy right now). Caching your packages will help alot when it comes time to upgrade (remember though to set your sources.list to the proxy address even on the machine that serves the proxy, at least that seems to be required for me). 

Even if there isn't a apt package for something, there is at least a deb somewhere that can be installed by dpkg.

Right now I am in the process of connecting it to my Linksys wireless router and a DirecWay DW6000 with a caching nameserver (and squid for web page caching) (dnsmasq seems to work). My initial tests seem to indicate using my box vs the Linksys box for primary resolution is faster (my box that is).

Ok, done rambling...

Robert

Robert

---

### Post by rmwarriner on 2006-07-19
Sorry, can't help but ramble... :)

As a side note, once I was familier with Dapper I was able to install the full system and gain net access within two hours on the server (its a bit slow) and within one hour on my workstation. There is an outstanding guide, search for "Ubuntu ISP Setup" (sorry I can't remember the actual address).

Ok, now I am really done...

---

### Post by Derek Djons on 2006-07-19
Welcome Rich,

I agree with you. There's always something that needs to be fixed. And by fixed I mean spending hours if not days :)

I hope Ubuntu Linux will give you the options and ease as it gives a lot of us here.

---

### Post by Sonic Alpha on 2006-07-19
> **Rich3077 said:**
> I am not trying to anger any SuSE people, but it wasnt for me.

I used SuSe on and off for nearly a year, and got nowhere with it.  It looks great, and runs fine (at least on the machine I installed it on), but that's about it.

I've learnt more with Ubuntu in the past week or so (as that's how long I've been using it), than I have in the past year with SuSe :mrgreen:

---

