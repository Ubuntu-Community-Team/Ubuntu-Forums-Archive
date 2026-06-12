---
title: "Upgrading Motherboard"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by riptreeper on 2007-08-03
I was considering upgrading my motherboard and needed some help. My system is as follows: 

x86 family 15 model 2 stepping 7 1794MHZ 
60 GB Hard Drive
184 Pin DIMM DDR PC 3200 @ 400 MHZ 
DVD drive 
CD/RW Drive 
Integrated Graphics Card 

I was wondering what possibilities I have for a new motherboard new ram and maybe a new video card. I will be upgrading to dual 120gb Hard drives soon and saw an awesome video of Linux Ubuntu Beryl and was wondering what my options are. Thanks for the help. 

This vid is awesome by the way here's the link 

[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

Maybe you've seen it.

---

### Post by Cypher on 2007-08-03
The possibilities for new hardware is infinite. :) I'd suggest a new Mobo, ram and a new PCI-E video card (preferablly nVidia). You will most likely also want to go with a new Intel Core Duo or AMD CPU based on what you like more. 

The rest of your hardware should work as it is..

---

### Post by riptreeper on 2007-08-03
I kinda wanted to keep the same processor for a while as this processor with a gb or two of ram will run very fast where could I finds a compatible motherboard?

---

### Post by jgrabham on 2007-08-03
> **riptreeper said:**
> I was considering upgrading my motherboard and needed some help. My system is as follows: 

x86 family 15 model 2 stepping 7 1794MHZ 
60 GB Hard Drive
184 Pin DIMM DDR PC 3200 @ 400 MHZ 
DVD drive 
CD/RW Drive 
Integrated Graphics Card 

I was wondering what possibilities I have for a new motherboard new ram and maybe a new video card. I will be upgrading to dual 120gb Hard drives soon and saw an awesome video of Linux Ubuntu Beryl and was wondering what my options are. Thanks for the help. 

This vid is awesome by the way here's the link 

[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

Maybe you've seen it.

Depends on how much money you want to spend

The specs in my sig are quite good, but were very cheap

---

### Post by Cypher on 2007-08-03
> **riptreeper said:**
> I kinda wanted to keep the same processor for a while as this processor with a gb or two of ram will run very fast where could I finds a compatible motherboard?
You will want to get the model number for your CPU. Like Pentium 4 or AMD Duron or whatever. Once you get that info and the PIN for the CPU, go to [http://newegg.com](http://newegg.com) and in the Mobo section you should be able to just search for mobo's that support your CPU.

---

### Post by riptreeper on 2007-08-03
That sounds like a nice setup how much for something like that? Have you seen that video I would like to run something like that as a second OS just because I need win XP for school

---

### Post by riptreeper on 2007-08-03
> **Cypher said:**
> You will want to get the model number for your CPU. Like Pentium 4 or AMD Duron or whatever. Once you get that info and the PIN for the CPU, go to [http://newegg.com](http://newegg.com) and in the Mobo section you should be able to just search for mobo's that support your CPU.

How would I find the model number and all that info Im a little new to this ? Thanks to everyone for the help the community here is awesome

---

### Post by Doberman92 on 2007-08-03
There might be a program for it, but I don't know what it is. To find out in general what processor you have, try System > Preferences > Hardware Information. To find out the specific model number I believe you would have to open up the computer and actually look at the processor. But yeah, if you get the model number, just go to Newegg and you can find any motherboards compatible with your processor. Make sure to find out which RAM it supports, and buy the correct type.

---

### Post by Hospadar on 2007-08-03
The most important part of getting a new mobo (if you are keeping your processor) is to get the right type of socket.  As above, you'll want to find out exactly what type of processor it is.  In windows you could go to control panel/computer and probably find it in there or in the hardware manager.  in linux, you can go to system -> preferences -> hardware info as doberman says, or you could use sysinfo ```
sudo apt-get install sysinfo
sysinfo
```this does basically the same thing but it's a little more full featured and powerful in my opinion.  you should be able to do either of these things off of the live cd as well without installing i believe

Once you know the model you can go to a site like newegg and look it up and find the socket type in the specs.  then browse for mobos with that socket, you'll want to make sure you get a mobo with a pci-express (pcie/pci-e) 16x slot for a new graphics card

you will also want to get 240 pin memory (it's the current standard) probably ddr2 speed, make sure the pin count and memory speeds are the same on the mobo and memory you are buying.

As for video cards, nvidia supports linux a **lot** better so i would recommend getting an nvidia over ati, especially if you are going to be needing acceleration (as you will with beryl)

As for the rest, you might want to look for one that has plenty of support of front panel usb ports, etc.  also, if you are using IDE cd/hdd drives, you will want to make sure it comes with enough ide ports.  a lot of newer mobos only have one or no ide ports since sata is so much nicer.  each ide port will get you two devices.

hope this helps!

---

### Post by riptreeper on 2007-08-03
Ok thanks everyone

---

