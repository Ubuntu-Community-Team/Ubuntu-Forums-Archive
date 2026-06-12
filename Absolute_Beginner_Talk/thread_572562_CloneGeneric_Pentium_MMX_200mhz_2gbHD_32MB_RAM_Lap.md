---
title: "Clone/Generic Pentium MMX 200mhz 2gbHD 32MB RAM Laptop Questions."
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by wraith1986 on 2007-10-10
I just bought a laptop on eBay for $5. It works well from what the seller said but there are a few things I want to do with it. It has a Pentium MMX 200Mhz Processor, which the seller confirmed I can clock up to 500mhz, and 32MB of RAM. I already ordered a cheap ethernet card for it as it has a PCMCIA slot. It's a generic/clone model with a tiny little 10inch screen. Firstly I know the computer cannot handle anything but DSL at the moment. I am however wanting to put Dreamlinux on it. I was wandering if I buy new RAM for it if it could handle Ubuntu or Dreamlinux, preferably Dreamlinux as it's Debian and XFCE based for the speed, plus I like it just a tad more. Also it native with Windows 95. What sort of RAM would it use? I don't want to wait to get it, check the ram, THEN order the stuff I need to get it to work. It'd be two weeks before I could use it. Anyone have a good guess of what a 10 year old laptop would have as RAM. Also any configuration suggestions would be appreciated. I bought some reference manuals and the Testout Linux+ tutorial. The whole reason I made this purchase is to try and get friendly with Linux and still use my Windows Computer for reference until I am done. I don't like the idea of dual booting or else I would have done that. Thanks in advance.

---

### Post by tgalati4 on 2007-10-10
It's helpful to ask one question at a time in the forums.

We have no idea what your RAM is.  Until you post the make and model of the laptop, it's just a guess.

If you had a 1997 Omnibook, then the memory is only available from HP since it is a proprietary memory module.  There are sources for oddball memory, but we need to know more specifics.

A Pentium I, 200 MHz will really choke on anything other than DSL or similiar light distros.  I put fluxbuntu (Dapper-based) on my Omnibook (166 MHz, 64 MB) and it was painful.  DSL runs fine on it.

You can experiment, but you will probably end up with DSL as that will probably perform the best.

---

### Post by 900donuts on 2007-10-10
i'm trying the same thing in the other os part of the forums 

first i'm going to need to know exactly what model laptop it is even if its a odd ball brand

second xfce will not work on 32mb fluxbox or lighter will work much better

third what do you plan to do with it (for example i plan to use my 32mb laptop to watch movies using the framebuffer) if you want to get friendly with linux get some thing that makes extencive use of the command line or if thats to hard "netinst" install debian and build the system you want from the ground up (software wise)

forth don't overclock it unless you prepared to carry around water cooling equipment laptop cooling systems are not as good as desktops

---

### Post by wraith1986 on 2007-10-11
Like I said it is a clone/generic laptop. I've never seen anything like it. It has no serial numbers to speak of. No markings at all. Nothing. I'll post some pictures of it and see if anyone can determine what it is. I wasn't planning on putting any OS on it until I get some more RAM for it. But I'm having a hard time finding out anything at all about it. Even the serial on the RAM has been scratched off. That is one reason I was wandering if maybe someone could help me out. Since it is not marked in any way I can't order new RAM yet. I don't know what it can hold, but if I can figure it out I have plans of buying between 128MB ad 256MB if it can handle that much. Also, I was only planning of clocking it to around 300mhz so I could run Starcraft. lol Since it is so tiny I am only planning to use it to learn Linux, and maybe as a tiny note taker if I can find a battery or suitable generic replacement that will hold a charge.

The pictures are attached I will upload the rest in a second post.

---

### Post by wraith1986 on 2007-10-11
Here are the other pictures.

---

### Post by Sef on 2007-10-11
You also might want to check out [Deli Linux]("http://delili.lens.hl-users.com/").  

> DeLi Linux stands for "Desktop Light" Linux. It is a Linux Distribution for old computers, from 486 to Pentium II or so. It's focused on desktop usage. It includes email clients, graphical web browser, an office programs with word processor and spreadsheet, and so on. A full install, including XOrg and development tools, needs not more than 350 MB of harddisk space. 

The trick is, that DeLi Linux uses only "lightweight" alternative software. If you are looking for the newest KDE, GNOME or Mozilla, DeLi Linux will not make you happy. The test computer is a 486 laptop with 16 MB RAM, and all apps which comes with DeLi Linux are running smoothly.

---

### Post by 900donuts on 2007-10-11
am i the only one here who thinks over clocking an old laptop with a desktop processor is a bad idea?:confused:? well if you do over clock it be sure to post video of it exploding:popcorn:(unlikely to happen if it will die it will probably die less spectacularly but if it does i don't want to miss it)

heres an idea to identify the manufacturer

what dose it say when it boots up list EVERYTHING up till the point where it starts trying to boot from the hard drive also there should be some source of info in the bios setup menu

---

### Post by Paulmd on 2007-10-12
> **wraith1986 said:**
> I just bought a laptop on eBay for $5. It works well from what the seller said but there are a few things I want to do with it. It has a Pentium MMX 200Mhz Processor, which the seller confirmed I can clock up to 500mhz, and 32MB of RAM. I already ordered a cheap ethernet card for it as it has a PCMCIA slot. It's a generic/clone model with a tiny little 10inch screen. Firstly I know the computer cannot handle anything but DSL at the moment. I am however wanting to put Dreamlinux on it. I was wandering if I buy new RAM for it if it could handle Ubuntu or Dreamlinux, preferably Dreamlinux as it's Debian and XFCE based for the speed, plus I like it just a tad more. Also it native with Windows 95. What sort of RAM would it use? I don't want to wait to get it, check the ram, THEN order the stuff I need to get it to work. It'd be two weeks before I could use it. Anyone have a good guess of what a 10 year old laptop would have as RAM. Also any configuration suggestions would be appreciated. I bought some reference manuals and the Testout Linux+ tutorial. The whole reason I made this purchase is to try and get friendly with Linux and still use my Windows Computer for reference until I am done. I don't like the idea of dual booting or else I would have done that. Thanks in advance.


In this generation, laptops without easy markings are usually made by Sager or Mitac. Think of them as Wal-mart Specials, only less reputable. You've never heard of them, because they're absolute crap. All I saw was thumbnail images, not enough for me to ID the machine for sure. (you can send me the the full sized images to my personal email, if you like, and i'll be able to tell you more. I worked at a computer Recycling center, I know this generation of machines pretty well... my address is [email]paulmd@efn.org[/email].) 

At a guess, the RAM is EDO. And you won't be able to find any large enough to run Ubuntu with, for a reasonable price. If the leads on the ram stick are one solid bar, it's edo. the other possibllty is PC-100, which is has the leads split, so it's in 2 sections.  The Other, other possibility is it's not like that at all, and is a funny shaped module. (this means screwed.)

Unfortunately, in this generation, laptop ram was often very proprietary. So even if you find ram that meets the broad specification, you may not get the exact spec required.

As to clocking to 500MHZ.... boooogus. Maybe if you switched to a k6-2. Maybe. If the machine uses a desktop style processor. Which most laptops don't (some do). IF the bios and motherboard will support it. Which isn't that likely. Even if you got it working, the extra heat generated by the faster processor (with no better cooling, because there's no room for it inside the laptop) would make the machine very unstable. At best. At worst, you'll have a dead processor in short order. If you know what you're doing, you might overclock the P1, a few percent. 

Finding working batteries for that machine, will also run many times what you paid for the machine. Your best bet there is to see if there's a shop that rebuilds laptop batteries. (they crack open the dead battery and replace the cells inside, which isn't trivial)

In short, it was really worth about $5.

Sorry to have to tell you this.

---

