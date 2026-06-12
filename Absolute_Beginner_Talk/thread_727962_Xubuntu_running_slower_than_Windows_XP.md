---
title: "Xubuntu running slower than Windows XP?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by SubOne on 2008-03-18
I have a Compaq Presario 5834 with specs listed here: [http://pastebin.com/m401b972b](http://pastebin.com/m401b972b)
It is approximately 500Mhz with 64MB of RAM.

The machine previously had Windows 98 installed and although it ran pretty fast for what it's running on, a lot of the operating system files were missing and problems were arising left and right. I did what I had to do to get it online so that I could download Xubuntu, which meant I needed to install Windows XP. Now Windows XP runs on it just fine with selected services turned off (including Themes), but I prefer *buntu.

I refuse to believe unless otherwise corrected that Xubuntu cannot out perform Windows XP on this machine. However, it would appear that Windows XP runs a little slower than Windows 98 did and Xubuntu is running at least 10 times slower than that.

Also, some other problems have presented themselves:
* When I run Terminal my X session is ended and I am presented with the login screen.
* Update Manager hangs (it would appear)

My initial thought was that the video drivers were not correct as it has been my experience that that is the first thing that causes linux to run slowly. However, as far as my research can tell me, I am using the correct drivers now ("Intel i810 driver" for "Intel(R) 82810-DC100 Graphics Controller") with no visible performance change.

I spent all day boasting to the owner about how much more quickly the computer should run under linux. I hope that I am not made out to be a liar. Any assistance in this matter would be greatly appreciated.

---

### Post by Oldsoldier2003 on 2008-03-18
> **SubOne said:**
> I have a Compaq Presario 5834 with specs listed here: [http://pastebin.com/m401b972b](http://pastebin.com/m401b972b)
It is approximately 500Mhz with 64MB of RAM.

The machine previously had Windows 98 installed and although it ran pretty fast for what it's running on, a lot of the operating system files were missing and problems were arising left and right. I did what I had to do to get it online so that I could download Xubuntu, which meant I needed to install Windows XP. Now Windows XP runs on it just fine with selected services turned off (including Themes), but I prefer *buntu.

I refuse to believe unless otherwise corrected that Xubuntu cannot out perform Windows XP on this machine. However, it would appear that Windows XP runs a little slower than Windows 98 did and Xubuntu is running at least 10 times slower than that.

Also, some other problems have presented themselves:
* When I run Terminal my X session is ended and I am presented with the login screen.
* Update Manager hangs (it would appear)

My initial thought was that the video drivers were not correct as it has been my experience that that is the first thing that causes linux to run slow. However, as far as my experience can tell me, I am using the correct drivers now ("Intel i810 driver" for "Intel(R) 82810-DC100 Graphics Controller") with no visible performance change.

I spent all day boasting to the owner about how much more quickly the computer should run under linux. I hope that I am not made out to be a liar. Any assistance in this matter would be greatly appreciated.

use damn small linux 64 MB ram is not enoough for any current 'buntu flavor imo

---

### Post by NightwishFan on 2008-03-18
Xp should not run well with 64mb of ram. Xubuntu should not run well with any less than 128mb of ram. You need DSL, Puppy, Fluxbuntu?

My Xp on 128mb of ram barely could run IE6. I will boot it up right now just to enjoy the laggy statup menu that takes 15 seconds to appear.

---

### Post by halitech on 2008-03-18
you could run top (or htop if you have it installed) to see what is running, might give you an idea what is using cpu cycles

edit: opps, missed the part about 64meg of RAM, that might do it as Xubuntu wants at least 128

---

### Post by Duck2006 on 2008-03-18
> It is approximately 500Mhz with 64MB of RAM.

More RAM will make all the different in the speed of the system.

---

### Post by SubOne on 2008-03-18
You are not the first people to try to tell me that Windows XP should not run on this machine or that I am embellishing the details, but I assure you Windows XP runs just fine. So, am I to believe that Xubuntu really cannot out perform Windows XP in this case?

---

### Post by halitech on 2008-03-18
true that, I have a 500mhz box with 160 and it runs Gnome okay for what I use it for

---

### Post by NightwishFan on 2008-03-18
I am not saying I don't believe you. I don't, but that isn't my point. Yes Xp runs about the same as Xubuntu. Linux for lighter machine give Puppy a try. My rule is I use puppy unless the machine has over 380mb ram. After that point it becomes possible to have a good speed GNOME/KDE machine since I would rather use JWM than XFCE.

---

### Post by SubOne on 2008-03-18
I'm not saying that Xubuntu is running "about the same" as Windows XP. I am saying that Xubuntu is running extremely poorly and is lightyears away from being as fast as Windows XP in this case.

It would appear I have little choice but to cannibalize another machine for memory. I will update in a moment.

---

### Post by NightwishFan on 2008-03-18
Ahh a good flame/argument. Yes Xubuntu runs about the same as Xp for requirements. Xubuntu should run on 64mb but not well and only with alt installer. Xp has no live cd and is sluggish on x2 that amount of ram. Your bs-ing me.

---

### Post by SubOne on 2008-03-18
I must agree to the point that it will not work off of the live cd. However, please note that I have _already_ completed installation from the alt cd.

I am currently in the process of installing the memory from the afore mentioned machine into another machine of almost identical stats. Then I will install Xubuntu on that and we shall see the result.

---

### Post by Oldsoldier2003 on 2008-03-18
Chuckles... "runs just fine" is a relative term. Some people have a lot lower expectations than others. 64MB in any modern (read bloated) GUI is just unacceptable. that includes xubuntu. So rather than argue over something thats based on ones own opinion of what is acceptable speed lets get to the bottom line.

Xubuntu in 64MB is a "pig" either up the ram, or try a smaller distro like Damn Small linux or puppy linux, you'll be much happier with the results

---

### Post by NightwishFan on 2008-03-18
:popcorn:

I am just messing with ya by the way. Yeah I cannot stand any noticeable delay when I am using an OS. So I try to keep way over the requirements. Ubuntu needs like 380mb of ram, I try to keep over 512. At 128mb Xp is mostly usable but not enjoyable.

---

### Post by SubOne on 2008-03-18
I successfully installed memory into another computer that is better, now it is listed by BIOS as 120MB of RAM (not 128, dunno why). So, should I try Xubuntu again or just do Puppy linux?

---

### Post by NightwishFan on 2008-03-18
I say puppy. Depends on what you need though.

---

### Post by SubOne on 2008-03-18
I am looking for something like Ubuntu. The main purpose of the machine will be to run word processing and firefox I suppose.

---

### Post by Duck2006 on 2008-03-18
> **SubOne said:**
> I successfully installed memory into another computer that is better, now it is listed by BIOS as 120MB of RAM (not 128, dunno why). So, should I try Xubuntu again or just do Puppy linux?

Do you have onboard video? If so thats where the 8Mb is. Give xubuntu a go, if it does not run as good as you want then install puppy.

---

### Post by SubOne on 2008-03-18
ok i am getting ready to try xubuntu again. i will update when complete

---

### Post by SubOne on 2008-03-18
Ok, well this other computer which I put the memory in, now it reboots whenever I try to install Xubuntu. It says loading linux kernel and it gets to the end of the progress bar and then i see the BIOS again and it starts all over.

---

### Post by NightwishFan on 2008-03-18
It must be the ram if you were able to start before.

---

### Post by SubOne on 2008-03-18
Well, it's a different computer now, and Windows 98 boots fine so...

---

### Post by NightwishFan on 2008-03-18
Not enough to use the live cd? Try puppy.

---

### Post by Beto0707 on 2008-03-20
I'm actually having a similar issue as the original poster.  I have a computer with a 500 Mhz K6-2 and 256 MB of RAM.  Windows XP runs better than Xubuntu (menus are faster, I could run multiple programs in XP).  This isn't what I was expecting, especially given that xubuntu is for "older, slower" computers.

I wanted to use a ubuntu derivative because of the hype I've been hearing as well as the wealth of information.  I have been impressed with the ease of installation and setup.  I also like the much smaller amount of disk space xubuntu uses.  The only problem I've had is with my VT6421 raid card I was using to access a SATA drive.

---

### Post by N1N31NCHN41L5 on 2008-03-20
i'm running a dell lattitude c400 1.3g with 256mb of mem - and xubuntu cam get REAL sluggish the cpu will top out and it runs with about 220 of 248mb of memory ALWAYS used. any tips on how to cut down memory usage on xubuntu and speed the dinosaur up

---

### Post by NightwishFan on 2008-03-20
My advice is to install perhaps only the xfce core and build what you want from the ground up. What I did on my test machine is removed the xfce-desktop and installed JWM and only the applications I used but this is very advanced. If you do not know how to use JWM use XFCE. If you do not know what you would need for a useable desktop then I suppose you should try a lighter distro.

As another note I installed kde-core and the mem usage was only 122mb on 64-bit.

---

### Post by N1N31NCHN41L5 on 2008-03-20
im a NEWB to Linux - 3 weeks old - should i start a different os on here than xubuntu and if i do will it still run all the programs xubuntu does

---

### Post by NightwishFan on 2008-03-20
I would say try puppy or damn small linux. Perhaps Debian or an earlier Ubuntu. Xubuntu should run ok on 128-256mb though.

---

### Post by erichvac on 2008-03-20
r u dual booted ? how can u tell it is faster or slower is it login and opening a window or slow to play movies large files etc?  what im saying is did you consider the video card and maybe if win-e is running it is running part of widows??

---

### Post by Beto0707 on 2008-03-20
I am not using a dual-boot.  I was running XP on this older computer since XP has been out.  Last weekend I finally decided to try my hand at an operating system that doesn't require "Geniuine Authentication" (are they really calling me a liar?).

I know it is slower because when I am running a torrent download program, such as Deluge, the computer is damn near unresponsive.  When downloading the exact same torrent with utorrent in XP I could still use the computer.  This was the straw that got me too posting.  I was expecting xubuntu to be more responsive than XP.  As an earlier poster said, I'd like to have near 0 response time opening applications.  I know linux can be fast and have eye candy on a machine like this.  I remember seeing similarly specced computers running linux when this computer was cutting edge.

It sounds like I need to try Puppy linux or damn small linux.  I was hoping to ease the Linux learning curve with an ubuntu distro though.  Will these linux distros be as user friendly? :confused:

My end goal for this PC is to make a headless torrent server as well as an FTP server for friends and family.  I do not desire to manage this server over the internet, just with VNC from my desktop next to it behind my router.

---

### Post by NightwishFan on 2008-03-20
Try the last long term release of Ubuntu. Puppy is fine but a bit confusing for non-linuxers. I would say either get a base system of XFCE, which should run lighter than "xubuntu-desktop", or use an older Ubuntu/Xubuntu. Look up Linux Mint or Fluxbuntu while you are at it.

---

### Post by Redsandro on 2008-05-02
Hi,

In my experience, **Ubuntu** never outperforms **XP**. *Especially* on older computers. I really like **Ubuntu**, but I only use it on **Pentium 4** and above, where speed seems instant anyway. Even **Fluxbuntu** is slower than **XP** on my **P2 266MHz with 96 MB** of Ram. But if you really like the **Ubuntu** way, I suggest you try **Fluxbuntu** because it's faster than Xubuntu. But it uses **Fluxbox**, which I personally dislike, but many people are really positive about it and it is wayy lighter than **XFCE**.

For faster booting, I now use **Zenwalk**. It's not Ubuntu based but if you don't mind that you can give it a try. Still, on older computers it's slower than XP, at least at boot time.

If you ever find a distro faster than XP on older computers [SIZE="1"](and not something way crappier than XP)[/SIZE] please let me know!

[SIZE="4"]-edit-[/SIZE]

I didn't realize this was an older topic.. sorry :(

---

### Post by Bölvaður on 2008-05-02
> **Redsandro said:**
> If you ever find a distro faster than XP on older computers [SIZE="1"](and not something way crappier than XP)[/SIZE] please let me know!

I had a computer (128mb) that booted xp at something about 2:50 - 3:10. (it was longer than the first song on some song I had in my cd player :P)
Because it was so immensely slow I put xubuntu on it which reduced the boot up time to 56 seconds (if I remember correctly, been months...).

The xp was almost never used since it was reformatted so you could say it was a fresh install (it only had the gimp, flash and firefox).
The xubuntu was not tweaked in any way.

So we could say both xp and xubuntu was just normal fresh installs.

I have no idea why the difference is... don't really care. It is just the OS. If it works, it works.

---

### Post by NightwishFan on 2008-05-02
Any linux distro released around the same time as Xp is bound to be faster, trust me. I like how on my friends comp with Ubuntu it does everything instantly and Xp lags to the point where he dislikes using the computer, even though Ubuntu's stated ram requirement is 3x more. The kernel is just superior I assume.

---

