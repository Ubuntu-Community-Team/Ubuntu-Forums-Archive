---
title: "Absolutely sick of windows, and other beginners ailments."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Pirate_King on 2007-05-01
Alright ladies and gents, consider this my official entry into the world of Linux. I have a few questions, and if anyone can help me out, id appreciate it.

1. I'm sick and tired of windows. When I make the transition to Ubuntu, would I have to have windows on my system at all?

2. Beryl has absolutely sealed the deal for me, however it seems like it requires an enormous amount of resources... is this true?

3. Will there be very many programs that I can't use? I'm a big time gamer, so I'd be curious to know how my life would be affected upon transition.

I'm sure that there will be more questions, but for now this is all I can come up with.

Thanks in advance.

---

### Post by Sef on 2007-05-01
> I'm sick and tired of windows. When I make the transition to Ubuntu, would I have to have windows on my system at all?

No, you have the option to dual boot though.

> 2. Beryl has absolutely sealed the deal for me, however it seems like it requires an enormous amount of resources... is this true?

From the [Beryl Wiki]("http://en.wikipedia.org/wiki/Beryl_%28software%29"):  > System Requirements

According to the Beryl FAQ, Beryl runs acceptably well on a GeForce 3/i855/Radeon 7500, 256MB of RAM, and a 1.2GHz processor. Version 7.1 of Xorg and a recent version of Mesa is recommended

> 

3. Will there be very many programs that I can't use? I'm a big time gamer, so I'd be curious to know how my life would be affected upon transition.


Some games work on GNU/Linux.  But if you are a big gamer, you probably would want to dual boot.

---

### Post by cotcot on 2007-05-01
I also recommend dual boot untill you experienced that you have what you want under linux. Some hardware (printer, scanner) from suppliers that do not disclose their drivers might be difficult.

---

### Post by starcraft.man on 2007-05-01
1) Nope, if you want no trace of windows when you get to the partitioner just delete it :). If you want to dual boot leave it on your system and grub will install it into the MBR so you can boot into it later. Just some advice for optimal install, you should use 6-8 GB for your root partition (Labeled "/" ) , 2-3 GB Swap (its just labeled swap) and you should probably make a separate partition for home (labeled /home) so that your data is seperate from your install.

2) I use beryl all the time. I don't think its that resource intensive. It is certainly less demanding than vista. I only have 1 gig of sdram and a 6800 GT (admittedly thats still pretty good :) ). As long as you have a farily recent card you should be able to run it.

3) Most of the major games are certified to work with Wine to a good degree. You may wanna look at cedega if you don't want the hassle.

[WIne app database]("http://appdb.winehq.org/")

[Cedega App Database]("http://transgaming.org/gamesdb/")

Edit: *grumble* my typing must be getting slow, people beat me again >.>

---

### Post by Terl on 2007-05-01
> **Pirate_King said:**
> Alright ladies and gents, consider this my official entry into the world of Linux. I have a few questions, and if anyone can help me out, id appreciate it.

> 1. I'm sick and tired of windows. When I make the transition to Ubuntu, would I have to have windows on my system at all?

This depends on what programs you use.  See 3 below.  Not all windows programs will run under wine.  If you have things that require current direct x and are system intensive you may need to keep windows around.  I still have it for games only.

> 2. Beryl has absolutely sealed the deal for me, however it seems like it requires an enormous amount of resources... is this true?

I can't say as I don't care about desktop effects.  

> 3. Will there be very many programs that I can't use? I'm a big time gamer, so I'd be curious to know how my life would be affected upon transition.

Keep your windows share until you are certain you can use the software you need in Linux.  It eases the learning curve knowing you can pop back out into windows until you learn Linux.  I have over 300 gigs of drive space and windows has about a quarter of that.  I left it just enough for some current games.

> I'm sure that there will be more questions, but for now this is all I can come up with.

Thanks in advance.

Give Ubuntu a try.  Keep your windows until you get used to Ubuntu.  In a while you will be like me...I haven't signed into windows in about 3 weeks now :)

---

### Post by ubnewbie2 on 2007-05-01
Don't forget, Windows runs well in a vmware machine.  It's free, and you don't need to reboot.  As soon as you're happy with linux, you can get rid of the Windows partition, and the run the vary occasional up in a virtual machine.

As an example, the wizard/app to configure my linksys PSUS4 print server on my network, only runs under windows. I ran it under a vmware machine from within ubuntu, no problems. It starts up Windows fast too, because you can just restore the virtual machine from a saved machine state - Windows desn't have to boot.

---

### Post by Tomosaur on 2007-05-01
> **Pirate_King said:**
> 
1. I'm sick and tired of windows. When I make the transition to Ubuntu, would I have to have windows on my system at all?

Nope, Linux is an operating system all of its own, no Windows required :) The installer will give you the option to use the entire disk (thus erasing Windows), or you can partition manually and keep Windows if you feel like.

> 
2. Beryl has absolutely sealed the deal for me, however it seems like it requires an enormous amount of resources... is this true?
Nope - Beryl only requires modest resources. Some of the plugins, like the water effects, are quite resource intensive, but the wobbly windows and 3d effects are capable of running on machines with fairly 'old' hardware. Be warned however - the latest version of Ubuntu (Feisty Fawn) comes with 'Desktop Effects', which is basically a 'stripped down' version of Beryl. The reason for this is that Beryl is re-merging with Compiz (which is what Feisty is really using, it's just renamed for usability sake). It has the same effects as Beryl, with the exception of the water effects and some other stuff. You can still choose to install Beryl yourself, but just so you know, much of it is already there. You can enable the Desktop effects by selecting 'Desktop Effects' from the System > Preferences menu. You may also need to enable the restricted graphics driver, depending on your graphics card.

For comparison's sake - Beryl / Compiz require nowhere near the amount of resources as Vista's Aero interface - you really don't need to worry much about upgrading hardware at all.

> 
3. Will there be very many programs that I can't use? I'm a big time gamer, so I'd be curious to know how my life would be affected upon transition.

Windows programs do not work on Linux - they're completely different systems. We do not have .exe files, for example. Many programs have both a Linux and a Windows version, while others only have a Windows version, and others only have a Linux version. There are many thousands of programs available to you, but depending on what you use, you may need to find replacements. Not many commercial games are made for Linux - but they do exist, sure. We have hundreds of free games for you to play, but obviously, most don't have all the graphical might of commercial games. Linux is perfectly capable of the same, or even better, performance and graphics as Windows, it's just that Linux is often overlooked as a platform.

However - you CAN get Windows programs to work on Linux, through the Wine project.Many games will run perfectly well using Wine, other's have performance problems, some don't work at all. You may also like to take a look at Cedega - which is Wine, but optimised for games. You have to pay for Cedega though, whereas Wine is free. There is also a free version of Cedega, but you need to compile it yourself to run it (not exactly brain surgery, there are guides available on the internet, but annoying for many people).

Anyway, welcome to the forums and good luck with Ubuntu :) Don't hesitate to ask if you run into problems.

---

### Post by Talon2 on 2007-05-01
> **Pirate_King said:**
> Alright ladies and gents, consider this my official entry into the world of Linux. I have a few questions, and if anyone can help me out, id appreciate it.

1. I'm sick and tired of windows. When I make the transition to Ubuntu, would I have to have windows on my system at all?



No.  4 of the 5 systems in our home are Ubuntu/Edubuntu only.  File sharing and printer sharing are really easy if all systems are Ubuntu.

> 
2. Beryl has absolutely sealed the deal for me, however it seems like it requires an enormous amount of resources... is this true?



Not in my experience.  Runs very well here on a P4 that uses an Intel integrated chipset (82865).  

> 

3. Will there be very many programs that I can't use? I'm a big time gamer, so I'd be curious to know how my life would be affected upon transition.



I'm not a gamer.  My kids like the games that are available.

My recommendation is that in the beginning individuals install Ubuntu to an older system that they can use to practice on.  Once you are familiar with the os then you can install and use it whereever it meets your needs.

---

### Post by HereInOz on 2007-05-01
Regarding the mention of VMWare above, please note that most games do not work all that well in virtual machines due to the limited graphics capability.  VMWare is getting better all the time, but to my knowledge it still only offers about 16MB graphics memory, and no 3D.

I will be happy for someone to correct me, though.

I use VMWare when I need a Windows system for Access database work, etc, but not for gaming.

---

