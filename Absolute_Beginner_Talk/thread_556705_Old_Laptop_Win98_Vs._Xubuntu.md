---
title: "Old Laptop Win98 Vs. Xubuntu"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-21
HI,  I have a very old 1999 laptop that originaly came with Windows 98 Second Edition.
I have installed Xubuntu 6.06 LTS but it runs very very slow.  For instance when
I open up Firefox it take about 20 seconds for it to load up and display google.
When 98se was on it, programs would open right away and not take so much time
to load. Is there a huge difference between Windows 98se and Xubuntu?  I was 
told Xubuntu was for lower end PC's. I want a desktop like win98 so I was assuming 
XFCE would fit the bill but it still seems to over tax the system for smooth running.  
Don't get me wrong, she doesn't crash, she's just very slow. Below I have listed my PC's specs.

Processor
Processor: AMD K6-2 380 MHz
Data Bus Speed: 66 MHz

Cache memory
Type: L2 Cache - Pipeline Burst
Installed Size: 512 KB

Ram
Installed Size: 64 MB ( 64 MB soldered) / **192 MB **(max)
Technology: SDRAM
Form Factor: SO DIMM 144-PIN

Video
Graphics Processor / Vendor: ATI RAGE LT PRO - AGP 2x
Video Memory: SDRAM - 8 MB

---

### Post by crjackson on 2007-09-21
> **Orbital75 said:**
> HI,  I have a very old 1999 laptop that originaly came with Windows 98 Second Edition.
I have installed Xubuntu 6.06 LTS but it runs very very slow.  For instance when
I open up Firefox it take about 20 seconds for it to load up and display google.
When 98se was on it, programs would open right away and not take so much time
to load. Is there a huge difference between Windows 98se and Xubuntu?  I was 
told Xubuntu was for lower end PC's. I want a desktop like win98 so I was assuming 
XFCE would fit the bill but it still seems to over tax the system for smooth running.  
Don't get me wrong, she doesn't crash, she's just very slow. Below I have listed my PC's specs.

Processor
Processor: AMD K6-2 380 MHz
Data Bus Speed: 66 MHz

Cache memory
Type: L2 Cache - Pipeline Burst
Installed Size: 512 KB

Ram
Installed Size: 64 MB ( 64 MB soldered) / **192 MB **(max)
Technology: SDRAM
Form Factor: SO DIMM 144-PIN

Video
Graphics Processor / Vendor: ATI RAGE LT PRO - AGP 2x
Video Memory: SDRAM - 8 MB

If I were you, I'd download the Puppy Linux LiveCD and give it a spin.  It's very fast and should fit your specs. very well.

---

### Post by por100pre1 on 2007-09-21
Try [DSL]("http://www.damnsmalllinux.org/") or [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1"), they should run fine in that PC. You can also try a [bare bones]("http://www.psychocats.net/ubuntu/minimal") Ubuntu installation.

---

### Post by Jeroen Vernooij on 2007-09-21
64 MB just isn't enough for XFCE.
If you can get a 2nd hand 128MB module extra (for like 5$ :) ) xubuntu will run much better.
Your processor is OK though.

I really discourage to use win98, support isn't available and bugs / exploits won't get fixed anymore.

You should try one of these:
[http://www.puppylinux.org/](http://www.puppylinux.org/)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by mlentink on 2007-09-21
While you're at it, you might also want to look at [this]("http://www.delilinux.org/"). Haven't tried it out myself yet, but heard favorable comments about it.

---

### Post by kerry_s on 2007-09-21
the difference is your throwing a new system on a old rig. win98 was built to work in those low specs. xfce4 is made to be low resource, not to function on crap. would you expect to throw xp on and have it run the same as win98? of course it's do-able but don't expect miracles.


Installed Size: 64 MB ( 64 MB soldered) / 192 MB (max)

are you saying you have 192 or you have 64, but it can be upgraded?


anyways you want speed, you have to do a custom install or use a mini distro made to work on low spec systems-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by LowSky on 2007-09-21
> **Orbital75 said:**
>  
Don't get me wrong, she doesn't crash, she's just very slow. Below I have listed my PC's specs.

Processor
Processor: AMD K6-2 380 MHz
Data Bus Speed: 66 MHz

Cache memory
Type: L2 Cache - Pipeline Burst
Installed Size: 512 KB

Ram
Installed Size: 64 MB ( 64 MB soldered) / **192 MB **(max)
Technology: SDRAM
Form Factor: SO DIMM 144-PIN

Video
Graphics Processor / Vendor: ATI RAGE LT PRO - AGP 2x
Video Memory: SDRAM - 8 MB


Damn that is one slow machine. That isn't much faster then an old computer I had running XP (it did it somehow with 196MB of RAM)
But this is also a Laptop, does it have speed stepping, if it does you should turn it off. That thing needs all the processing it can get.
I think you really need more RAM... or a new Computer...sorry if that comment hurts

but try this Firefox fix... it might speed thing up a little bit

 1) Open Firefox
2) Type ```
 about:config 
```into the address bar and hit return. Scroll down and look for the following entries:
         ```
network.http.pipelining network
```
                    ```
http.proxy.pipelining network
```
                           ```
   http.pipelining.maxrequests 
```

3) Alter the entries as follows: 
Set ```
"network.http.pipelining" to "true" 
```(simply double click the entry) 
Set```
 "network.http.proxy.pipelining" to "true"
```  (simply double click the entry) 
Set ```
"network.http.pipelining.maxrequests" to some number like 30
```. This means it will make 30 requests at once. 
Now right-click anywhere and select New-> Integer. Name it "```
nglayout.initialpaint.delay
```" and set its value to "0". 
This value is the amount of time the browser waits before it acts on information it recieves. 
4) Close Firefox
5) Re-open and test for speed



**Try out this site as well [http://www.tweakguides.com/Firefox_1.html]("http://www.tweakguides.com/Firefox_1.html")**

---

### Post by por100pre1 on 2007-09-21
> **LowSky said:**
> Damn that is one slow machine. That isn't much faster then an old computer I had running XP (it did it somehow with 196MB of RAM)
But this is also a Laptop, does it have speed stepping, if it does you should turn it off. That thing needs all the processing it can get.
I think you really need more RAM... or a new Computer...sorry if that comment hurts

but try this Firefox fix... it might speed thing up a little bit...

Firefox is way too heavy for that machine, Kazehakase would be better there.

```
sudo apt-get install kazehakase
```

> **kerry_s said:**
> xfce4 is made to be low resource, not to function on crap.

Is it necessary to refer to the OP's old PC as "crap"? Is it useful in any way?

---

### Post by kerry_s on 2007-09-21
> Is it necessary to refer to the OP's old PC as "crap"? Is it useful in any way?

nope, it's not necessary. i apologize.

to the op, installing a new os on a slow rig will not make it faster.

there, everyone feel better.

---

### Post by Orbital75 on 2007-09-22
Well, this isn't my main machine, but I didn't want to throw away
a perfectly good laptop when I could find some way beath life back
into it. I realize I am putting a new OS on an old Machine but I was
thinking that's what Xubuntu was designed for, at least that's what
it states on the website.

Back when it was my main machine, I maxed out the ram to 192 and
added a new 20 Gig HD to it (It came with 4 GB). This is before you 
could just slide the HD out, I had to take the laptop apart to get to the HD.

I tryed several version of Ubuntu, Xubuntu, Vector linux, and PCLinixOS but 
nothing would run on it, it would either not get through the install or just not 
even boot correctly and lock up. I keep getting messages about my Bio's being
pre 2000 ( I have a 1999 Bios ).  The bios is the most recent one so it can't
be updated.

---

### Post by dptxp on 2007-09-22
Install ICEWM using synaptics first. SYSTEMS>Administrations>Synaptics. Put a search.
Log out, choose sessions in options at bottom left of login screen and choose ICEWM
Use seamonkey as your browser.
Other options

Make a SWAP partition of 512MB to 1 GB with Gparted first and try Puppy. About 93 MB download.
DSL (Damn  Small Linux is another option). 50 MB. I could not mount drives. But iff Puppy runs, it will be great.

It is tough to find a decent Linux with with GUI for such machines.
I run Windows 98 on a P100 with 32 MB ram. No Linux ran on it.

You can also try Deli Linux.
Some Vote for Arch Linux.
I think you will finally stick to W98.

---

### Post by jimrz on 2007-09-22
> **Orbital75 said:**
> 
I tryed several version of Ubuntu, Xubuntu, Vector linux, and PCLinixOS but 
nothing would run on it, it would either not get through the install or just not 
even boot correctly and lock up. I keep getting messages about my Bio's being
pre 2000 ( I have a 1999 Bios ).  The bios is the most recent one so it can't
be updated.

try adding a kernel parameter
```
acpi=force
```
to your menu.lst ... fixed the same issue on an older thinkpad I have, however on mine this alone interfered with pcmia card operation so I have to also add
```
pci=noacpi
```
which eliminates that issue

---

### Post by deserthowler on 2007-09-22
> **dptxp said:**
>  I think you will finally stick to W98.

Win98 works great on "vintage" machines.  I ran 98SE on a 486 with 16 MB memory for a while.  Finally pumped up to 32 MB.

More memory will help but most of the "modern" distros are totally bloated.  You might try Debian Etch using something like FVWM if you want to do some work to customize.  Just click on the screen and you should get a menu.  It is the ultimate customizable WM.  I don't know if FVWM Crystal will fit.  It's a beautiful interface though and works well.  Very intuitive.

Use small apps and it might work.

Earl

---

### Post by Orbital75 on 2007-09-22
I may try that...... I think your correct on the new distros being bloated.
Although very nice in my opinion, they're meant for a higher end machine.
I just need something with a useful GUI to put this old beater back in use. 

So, does Debian offer a Live CD?  I don't think they do.
I've never heard of the FVWM windows manager.  Is it similar to Flux
or blackBox?

As said before I tried a lot of Distros and need something I can try 1st.
It would be terrible to erase Xubuntu to find what I install won't even boot.

---

### Post by RomeReactor on 2007-09-22
Hi. As far as I know, Debian doesn't have a LiveCD, so your only option would be to install it.

However, I would suggest, as others have done, that you try Puppy Linux or Damn Small Linux; they are designed for lower spec machines, yet still offer a lot of the functionality of bigger distros. I've used puppy on an old IBM Aptiva, and it ran very well. So, again, I suggest you try those first.

---

### Post by HermanAB on 2007-09-22
Add more RAM, then it will be OK.  With Puppy Linux it will Zooom like never before, but even for Puppy you would need to add more RAM.

Cheers,

H.

---

### Post by Orbital75 on 2007-09-22
I've already maxed my Ram out.... 192 is as much as I can add.
The motherboard won't take anymore. 

I know that doesn't sound like a lot but remember
back then that was considered over kill.

---

### Post by jimrz on 2007-09-22
> **Orbital75 said:**
> I've already maxed my Ram out.... 192 is as much as I can add.
The motherboard won't take anymore. 

I know that doesn't sound like a lot but remember
back then that was considered over kill.

puppy or dsl will zoom right along with 192 Mb

---

### Post by Orbital75 on 2007-09-22
Thanks.... I'm going to take a look at Puppy and see how that goes.  :KS

---

### Post by Orbital75 on 2007-09-23
I tried Puppy Linux and you were correct, it just zips right along without any hesitation. 
I have notice though thats it's not as user friendly than lets say Gnome, KDE, or Xfce.

A problem that I have is it didn't see my PCIMIA Linksys WPC11 Wireless card.
Since I am unfamiliar with puppy I am not sure how to fix this.
I saw it recognize my card as a Linksys wpc11 while booting up but once
in the GUI didn't work. I have a Static IP address (DHCP is off) along with WEP encryption
so I need something like Network Manager to type all the info in.

Would someone help me get my Internet working?

Just curious, what does it use it seems a little like ICEWM.


Windows Manager?
File Manager?

I think they should slim it down a little as far as programs.
I got overwhelmed and confused by all the icons everywhere.

---

### Post by Orbital75 on 2007-09-23
Any idea what driver the Linksys 802.11B "WPA11"  uses ?
I can't figure out a way to get my Internet up with Puppy Linux.
It saids it loaded my WPA11 card during boot but doesn't show any
active cards. 

I don't have DHCP Activated, I am running a Static IP + WEP
could that be the reason?

---

### Post by RomeReactor on 2007-09-23
Try looking in the [Puppy forums]("http://www.murga-linux.com/puppy/"); here's a thread that [discusses the supported cards]("http://www.murga-linux.com/puppy/viewtopic.php?t=11277"). Perhaps you'll need ndiswrapper to get your card working correctly.

---

### Post by dptxp on 2007-09-24
> **Orbital75 said:**
> Any idea what driver the Linksys 802.11B "WPA11"  uses ?
I can't figure out a way to get my Internet up with Puppy Linux.
It saids it loaded my WPA11 card during boot but doesn't show any
active cards. 

I don't have DHCP Activated, I am running a Static IP + WEP
could that be the reason?

Puppy has two major irritants-

one is configuring the DHCP,  open it try it.
Other is installing to HDD, especially with other OS.

---

