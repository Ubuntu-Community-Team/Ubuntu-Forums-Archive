---
title: "Ubuntu as Suse Alternative ?"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by djtwok on 2006-04-07
I´ve been using Suse 9.1 for about 2 years. Currently I´ve updated to Suse 10.0 64bit Edition. The problem is - it installs but wont boot. My Mainboard is an Asus Rock Board with an Amd 64bit 3200+ Cpu. I´ve found a lot of people on the web having the same probs with this Board and Suse 10.0 64bit.
So my questions:
Will Ubuntu 64bit Edit run on my system ? Or is it better to load the 32bit Edit ? What are the differences to Suse (only the real big import ones) ? Is an Firewall included in Ubuntu ? Is the Grub Loader included (I also have Win XP on my PC, and want a multiboot system).
Thanks in advance for your answers.

---

### Post by xXx 0wn3d xXx on 2006-04-07
[QUOTE=djtwok]I´ve been using Suse 9.1 for about 2 years. Currently I´ve updated to Suse 10.0 64bit Edition. The problem is - it installs but wont boot. My Mainboard is an Asus Rock Board with an Amd 64bit 3200+ Cpu. I´ve found a lot of people on the web having the same probs with this Board and Suse 10.0 64bit.
So my questions:
Will Ubuntu 64bit Edit run on my system ? Or is it better to load the 32bit Edit ? What are the differences to Suse (only the real big import ones) ? Is an Firewall included in Ubuntu ? Is the Grub Loader included (I also have Win XP on my PC, and want a multiboot system).
Thanks in advance for your answers.[/QUOTE]
I would recommend that you use 32 bit. There is no difference between 64 and 32 bit but you can use most programs with 32 bit. Yes iptables is included, it is a very nice firewall, and yes it uses grub. The differences from Suse it that UBuntu it would most likely run better (Suse is a little graphic intensive) and maybe a little more stable. If you want to check if your hardware works, then use a live cd first. If you have a wifi card, it may not be supported right out of the box but most wifi cards can be configured to work in under 3 minutes.

---

### Post by aysiu on 2006-04-07
[QUOTE=djtwok]
Will Ubuntu 64bit Edit run on my system ?[/quote] Only way to know is to try the Ubuntu live CD > Or is it better to load the 32bit Edit ? I've read that it is. There are certainly a lot more packages compiled for x86 than AMD64. > What are the differences to Suse (only the real big import ones) ? Right now there's no point-and-click installer. YaST is one centralized way to manage your entire system. Ubuntu doesn't have that. Ubuntu's online support (these forums) is amazing.
>  Is an Firewall included in Ubuntu ? No. > Is the Grub Loader included (I also have Win XP on my PC, and want a multiboot system). Yes. You probably want to take a look at this:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Since it sounds as if you already have a dual-boot, just ignore the part about resizing the Windows partition.

---

### Post by nanotube on 2006-04-07
contrary to what aysiu says, a firewall is included with ubuntu (iptables). it's just that the default configuration is to let everything through, so if you want it to block stuff, you have to configure it. but it is, strictly speaking, included. :)

but even if it werent, it would just be a quick "sudo apt-get install iptables" away, wouldn't it?

---

### Post by aysiu on 2006-04-07
[QUOTE=nanotube]contrary to what aysiu says, a firewall is included with ubuntu (iptables).[/QUOTE] I stand corrected. Thanks for explaining that. I didn't know that.

---

### Post by Jimmey on 2006-04-08
Contrary to what nanotube says, the default firewall that's included with Ubuntu ( I think ) is called netfilter. IPTables is the tool used to configure it, and by default, Netfilter doesn't 'let everything through' ( all ports are by default, closed ).

---

### Post by nanotube on 2006-04-08
jimmey correctly points out that technically speaking, iptables is not "the firewall" per se, but just the tool used to configure it, and "the firewall" itself is called "netfilter". [it needs to be pointed out though, that for all intents and purposes, iptables is the firewall, from the users perspective. there is not even anything under "man netfilter" - so it would be a very confusing and counterproductive thing to say that ubuntu includes the "netfilter firewall" because that will leave the user clueless as to how to actually operate it. :) ]

however, he incorrectly points out that by the default the firewall has all the ports closed. if you do a default ubuntu install, and then list your firewall rules with "sudo iptables --list" you will see with your own eyes that all the rules default to "accept". 

it is true, that ubuntu does not have any services listening on any ports, so the ports are "closed" - but they are not closed off by the firewall, merely by the fact of absense of any listening services.

---

### Post by Jimmey on 2006-04-09
I'll let this one slide - Because you got more beans than me. But, mark my words, when I catch up, you'll have trouble on your hands...

I'm kidding.:p

---

### Post by OffHand on 2006-04-09
If you want a nice GUI Firewall use Firestarter.
Super easy to configure and you can download it from the repositories.

---

### Post by BoyOfDestiny on 2006-04-09
[QUOTE=djtwok]I´ve been using Suse 9.1 for about 2 years. Currently I´ve updated to Suse 10.0 64bit Edition. The problem is - it installs but wont boot. My Mainboard is an Asus Rock Board with an Amd 64bit 3200+ Cpu. I´ve found a lot of people on the web having the same probs with this Board and Suse 10.0 64bit.
So my questions:
Will Ubuntu 64bit Edit run on my system ? Or is it better to load the 32bit Edit ? What are the differences to Suse (only the real big import ones) ? Is an Firewall included in Ubuntu ? Is the Grub Loader included (I also have Win XP on my PC, and want a multiboot system).
Thanks in advance for your answers.[/QUOTE]

Try this livecd for 64-bit. I'd recommend since I've been running it (and you have the hardware, might as well give it a try.) There is a difference of course (32-bit difference ;) ). It may not be noticeable since your hardware is plenty fast. The average estimate is that with just a recompile, 64-bit apps are at best about 20% faster. For things like compiling or encoding music etc, you should notice the benefits...

 If there is something you must have that is 32-bit only, chrooting is the way to go.

Working on a script to automate the process, down to 2 steps. :)

---

### Post by nanotube on 2006-04-09
[QUOTE=Jimmey]I'll let this one slide - Because you got more beans than me. But, mark my words, when I catch up, you'll have trouble on your hands...

I'm kidding.:p[/QUOTE]

lol :)

---

