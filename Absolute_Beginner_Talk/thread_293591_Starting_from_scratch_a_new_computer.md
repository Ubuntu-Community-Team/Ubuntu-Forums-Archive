---
title: "Starting from scratch: a new computer"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Velotix on 2006-11-05
Hello folks, this is my first time posting. Looking forward to the Ubuntu experience. Unfortunately, I'm going into this blind, as not only am I trying out a new OS, I'm trying it out on a brand new computer as well!
 
Naturally then, this post is concerned with which version of Ubuntu to install. The following list is the specification of my new computer omitting anything irrelevant to this post (motherboard specs, fans, etc. etc.):

[LIST]
[*]*Processor:* **Core 2 Duo E6600**
[*]*RAM:* 2x 1GB DDR2 RAM (2GB Total)
[*]*Optical:* 18x DVD Writer
[*]*Removeable:* 7-in-1 Floppy Drive and Media Card Reader
[*]*Storage*: 400GB 7200rpm SATA HDD
[*]*Graphics*: GeForce 7900GS 512MB (Gainward BLISS)
[*]*Sound Card*: Creative X-Fi Fatal1ty Edition
[*]*Networking*: Buffalo Nfiniti 802.11n 300Mbps Wireless Router/Access Point & Buffalo Nfiniti PCI Network Card[/LIST]The processor is the main problem; I'm not sure whether to use the i386 build or the EM64T build as my investigation into these different builds suggests to me that both versions will have their drawbacks on a Core 2 system.
 
Additionally, I'm wondering which of the desktop environments would be most suitable for my purposes: I'm currently doing a BSc in Games Technology, so the principal uses of the computer will be gaming, programming and research. That makes performance an issue as well, which has made me uncertain as to whether to try out Xubuntu and Xfce or not, and there is also the apparently age-old debate of KDE vs GNOME. I know I can always try all three when I install Ubuntu but it would be helpful to know which one is the best to start off with.
 
Ultimately, then, I come to you guys asking for advice: 32-bit or 64-bit, and Ubuntu, Kubuntu or Xubuntu? Thanks for reading. ^^

---

### Post by rfruth on 2006-11-05
32-bit Ubuntu (6.06 or 6.10?) is your best bet for leading edge (not bleeding  edge)   :rolleyes:

---

### Post by Velotix on 2006-11-05
Thanks: recommendation noted. I should have mentioned that I fully intend to install v6.10 regardless of which build I actually end up using. ^^

---

### Post by bodhi.zazen on 2006-11-05
My advice is along the window manager.

I use fluxbox on a "high end" machine (not all that high end mind you) because I want my system resources to be available for applications and not the window manager.

The big 3, Gnome, KDE, and XFCE, are resource hungry. IceWM, Fluxbox, and Openbox are not necessarily for "older machines" and running a lighter WM may be helpful to you.

Thus you may want to try icewm, fluxbox, or openbox as they are not as resource hungry.

My advice would be to start with XFCE and migrate to fluxbox or openbox when you are ready.

---

### Post by bsussman on 2006-11-05
As you discover how X is built, you will discover that gnome, kde, xfce, fvwm, mwm, fairy, ugga and bugga are all implementations of the same underlying facilities and, therefore, are very much parsonal style preference rather than technologically different.

When a program is said to work with one and not another, the statement merely means that a library or library associated with one or another needs to be present.

I regularly use gvim (gnome) on my kde desktop.  I use konqueror (kde) and nautilus (gnome).

The downside is that you will have to try them to make a decision.

The upside is that you will have to try them to make a decision.

:)

---

### Post by spinflick on 2006-11-05
> **Velotix said:**
> Hello folks, this is my first time posting. Looking forward to the Ubuntu experience. Unfortunately, I'm going into this blind, as not only am I trying out a new OS, I'm trying it out on a brand new computer as well!
 

Great...can I have your old one? ;)

---

### Post by Velotix on 2006-11-05
Thanks a lot - I'll look into it. I notice that the recommendation for the 32-bit version is going uncontested - is the 64-bit version still experimental?
 
**EDIT:**
> Great...can I have your old one? :wink:
 
Heh... actually, this will be my first computer. Period. It's certainly not the first one I've ever used, though!
 
**EDIT THE SECOND:**
Something else I've remembered: which is the ideal file system to format the HDD with? I'm guessing most people will scream "ext3" at me but I know there are alternatives.

---

### Post by blendmaster on 2006-11-05
The 64-bit version doesn't have as good of support for a lot of programs, while the x86 does.

Hmm... Gaming? Is this gaming like commercial games or games that you write yourself? Because Ubuntu doesn't really have a lot of support in the way of games. That's not to say that Ubuntu can't handle games, it's just a lot of developers tend to produce games for Windows rather than Mac or Linux.

Anyway, I do suggest that you get Ubuntu Dapper x86, as it has Long Term Support, and will give you lot less stress when installing certain programs (e.g. Macromedia Flash, Wine, game emulators, and so on...). Also, it looks like your computer will have no problems in the way of power. It's a lot better than mine!

---

### Post by bodhi.zazen on 2006-11-05
> **Velotix said:**
> Thanks a lot - I'll look into it. I notice that the recommendation for the 32-bit version is going uncontested - is the 64-bit version still experimental?

I do not know if I would say "experimental" but the 64 bit version is not as polished. You have such a large HD you could try giving a partiton for each version and try it for yourself.
 
> **EDIT THE SECOND:**
Something else I've remembered: which is the ideal file system to format the HDD with? I'm guessing most people will scream "ext3" at me but I know there are alternatives.

IMO ext3 or jfs.

---

### Post by Velotix on 2006-11-05
> Hmm... Gaming? Is this gaming like commercial games or games that you write yourself?
 
Both, with the focus gradually shifting to my own work as time goes on, but right now commercial software takes priority for research (and leisure!) reasons, even though my preferred method of gaming is via consoles. (I'm a Nintendo fan. ^^)
 
Your responses suggest that a dual-boot system will eventually be necessary here, which is what I initially thought though I was hoping to use Wine especially if it has better support for Win9x software than WinXP does. I've noticed **Cedega** has been recommended on occasion here for gaming but it seems to be a somewhat controversial program due to licensing issues. Worth a look?
 
> Anyway, I do suggest that you get Ubuntu Dapper x86, as it has Long Term Support
 
Noted, but I was expecting that Edgy, being more current, would better support newer hardware and software (Core 2 being quite new) and I'll ultimately have less hassle using 6.10 over 6.06.1. Was I wrong?
 
> I do not know if I would say "experimental" but the 64 bit version is not as polished. You have such a large HD you could try giving a partiton for each version and try it for yourself.
 
That's always an option, yes. Thanks. ^^
 
> IMO ext3 or jfs
 
Not heard of JFS just yet: I'd appreciate it if I could have a comparison of the two file systems. This aspect of a system has never been an issue for me before - I've learnt a lot in the past week!
 
**EDIT:** As for the 64-bit version, is there no 32-bit compatibility layer available as standard? Is this an option?

---

### Post by migla on 2006-11-05
> **Velotix said:**
> Thanks a lot - I'll look into it. I notice that the recommendation for the 32-bit version is going uncontested - is the 64-bit version still experimental?

I think the main drawback with 64-bit is that some (much?) software is lacking 64-bit versions. 

Mainly, flash, Automatix and nvidia beta drivers have been problematic, from what I've read. I'm sure there's much else aswell. I also gather there are various workarounds, but I've switched from 64 to 32 bits for the ease of use. I'm a lazy noob, though. Someone cunning and diligent might find 64 bits a better option.

---

### Post by blendmaster on 2006-11-05
> Both, with the focus gradually shifting to my own work as time goes on, but right now commercial software takes priority for research (and leisure!) reasons, even though my preferred method of gaming is via consoles. (I'm a Nintendo fan. ^^)

Your responses suggest that a dual-boot system will eventually be necessary here, which is what I initially thought though I was hoping to use Wine especially if it has better support for Win9x software than WinXP does. I've noticed Cadega has been recommended on occasion here for gaming but it seems to be a somewhat controversial program due to licensing issues. Worth a look?


Yes, I'm a Nintendo fan myself (Wii comes out so soon)! I'm also looking to get a degree in game design, so I know where you're coming from.

I think a dual-boot is recommended in your situation, though if you want to study games via console, and practice writing games on your computer, emulators (like Mupen64) can work great! 

>  Anyway, I do suggest that you get Ubuntu Dapper x86, as it has Long Term Support


Actually, this came out as I'm used to talking to newcomers to Ubuntu. Edgy would actually probably be better for this kind of stuff, but Dapper might give you less headaches (Edgy isn't tested as well, there's still a few bugs there). I doubt that Edgy will give you that much trouble, but certain situations have proven otherwise.

Anyway, I wish you happiness in your gaming career and your newfound Ubuntu OS!

---

### Post by bodhi.zazen on 2006-11-05
[Benchmarks](http://linuxgazette.net/102/piszcz.html)

Just scroll to the bottom !

---

### Post by Velotix on 2006-11-05
Those benchmarks are very interesting, and seems consistent with other information I have read suggesting that ext3 is badly optimised, being a file system with an emphasis on backwards-compatibility.
 
This still gives me a problem though: is Windows capable of reading JFS partitions (with or without additional software)? If I need to make my PC a dual-boot system in the future this will affect my decision.
 
Also, FAT32 gets a lot of flack it seems, and probably for good reason: is it really that bad?
 
Thanks, folks. ^^

---

### Post by Chayak on 2006-11-05
You won't have to worry about the Core 2 Duo, linux will simply see it as a dual processor system.  As filesystems go I do like ext3 as I've never had a problem with it.  Reiser is good if you have a lot of small files though the whole lead developer arrested for murder thing might hamper it's development a bit. (At least he didn't claim Tux made him do it!)  XFS is a good solid one but to be honest I'd suggest sticking to ext3 which is what the majority of Ubuntu users use hence if you do happen to have a problem you'll have a broader range of people to help you.

---

### Post by bodhi.zazen on 2006-11-05
I would fat32 to share with windows as I am lazy and that seems easier.

Windows will not read jfs. There are applications that will read ext2 and ext3 for windows although I have not used them personally.

---

### Post by Velotix on 2006-11-05
> You won't have to worry about the Core 2 Duo, linux will simply see it as a dual processor system.
 
Fantastic. ^^
 
> I'd suggest sticking to ext3 which is what the majority of Ubuntu users use hence if you do happen to have a problem you'll have a broader range of people to help you.
 
Well, as I was reminded earlier, my HDD is so huge I could just try both! I might do that. ^^
 
> There are applications that will read ext2 and ext3 for windows although I have not used them personally.
 
I hear they're reasonably effective though there are some functionality issues.
 
 
Also, I'm a little worried about my wireless router, for the following reason:

Buffalo Nfiniti 802.11***n*** 300Mbps Wireless Router

Although I know it's backwards compatible, 802.11n is a very new wireless standard and probably isn't well supported yet, if at all. I should note that I'm using a wireless connection for the simple reason that it will enable Internet functions on my Nintendo DS and also the Wii when I get the latter later on as they are wireless-only, in which case if the router supports both wired and wireless connections then this issue is moot as I can just use a wired Internet connection for the PC.

Come to think of it, how *do* you configure a wireless router in the first place?

---

