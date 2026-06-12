---
title: "Critique my Ubuntu Box!"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by Stretchman on 2005-09-07
Hello Everyone,

I’ve been bitten by the linux bug before, but each of my prior projects had a tendency to fizzle out.  My planning wasn’t that great, something wasn’t supported here, information wasn’t available there, internet queries would go unanswered, and so without adequate support my past linux projects usually ended up as reformats back to windows.

Ubuntu looks very promising however, so I wanted to present my proposed build project – an Ubuntu box – and outline the steps that I would take on both the hardware and software sides. I’d appreciate any critiques or recommendations that the Ubuntu community could make, which will go a long way in helping me to determine if this project is feasible for a long time windows user. 

Next to some steps I’ve posed questions and sometimes mention specific hardware, which some users may have experience with (e.g. drivers for the HP 3030).

 Thanks again for your assistance. :) 

I. Hardware:

Ubuntu Box

Case: Shuttle Zen XPC ST62 
 [http://www.silentpcreview.com/article139-page1.html](http://www.silentpcreview.com/article139-page1.html)

Cpu: 2.4ghz P4 Celeron (northwood)

CD-Rom: Sony DRU-510a dvd +/-rw

HDD: Western Digital or Seagate 40/60gb 
Question: Would IDE or SATA interface be easier?

Ram: 1gb Corsair pc 3200 DDR (512x 2 DIMMS)

Video: Integrated ATI Radeon 9100 chipset (has both VGA and DVI out)

Monitor: Dell 17” LCD most likely or Apple Cinema Display 
Question: Have any ubuntu users had any luck using Apple Cinema Displays?


II. Software

Installing Ubuntu: Using Ubuntu CD’s.  
Question: Following hardware assembly, I would set BIOS to boot from CD-Rom, using my Ubuntu CD’s.  I’ve never installed a non-gui linux distro before, is there anything I should know about setup, partitions, etc. Is it as simple as answering a few questions? I wouldn’t be dual booting. 


My primary tasks would consist of word processing and using the Internet. 

1.  Internet: Would need to add my Ubuntu box to my home network, currently consisting of two windows based computers using Cox Cable, Microsoft MN 500 router, and MN-510 wireless adapters.  Will Ubuntu be able to detect my MN-510 wireless adapter? What steps would I need to take in order to install drivers, etc. 

2. Wireless Printing: I’m currently using an HP Laserjet 3030 laser printer, which my Ubuntu box would have to connect to wirelessly. What steps would I need to take to get this up and running, assuming my wireless adapter is already functioning. Would I have to install the HP 3030 drivers? 

3.Wireless Peripherals: I may or may not decide to connect a wireless keyboard and mouse. Does Ubuntu have any issues with this, or are there any brands currently favored (i.e. Logitech, Microsoft?)

4.	Saving documents from OpenOffice: Does Ubuntu support multi-session burning? I’m totally peeved that my brand new Powerbook G4 will not let me save multiple documents to CD-RW at different times. I have to delete everything before I’m allowed to burn new data to the same CD-RW. All I’d really like to do with Ubuntu is be able to pop in a CD-RW and drag and drop documents to the same CD-RW, and be able to burn them without the hassle of deleting all the original contents.

---

### Post by earobinson on 2005-09-07
1) using nsdiwrapper you should be able to set this up (will take some work)

3) This should not be a problem at all

sorry i dont know the answer for 2 and 4

---

### Post by mlomker on 2005-09-07
I suspect that your hardware will work fine...integrated chipsets tend to get good support with drivers, etc.

SATA works fine on modern kernels.  If you intend to run older 2.4.x kernels for some reason then IDE would be better.

Wireless can be a pain to get working, I'll tell you that up-front.  You'll want to buy an adapter/card that you know will work with linux.  Anything with an atheros or prism chipset is your best bet.

Printing and windows networking is one of the few things that I've had *no* problems with so far.  Then again, I'm an MCSE,so take that fwiw.

I'd recommend loading up with standard mouse and keyboard and figure out the wireless later.  I've heard that they work fine but I wouldn't push my luck during the install.

To my knowledge, no *nix operating system supports multi-session.  Why don't you use a big flash (pen) drive?  They work great.

Don't worry about the graphical install.  It's easy.  I'd also recommend that you go with Kubuntu instead of Ubuntu (gnome) simply because I like it.   :-P

---

### Post by mr_ed on 2005-09-07
4.  From what I remember, it should be no problem to multi-session.  I don't think you can with the Nautilus burner.  Check out k3b.  (apt-get install k3b)

---

### Post by Stretchman on 2005-09-08
Hey guys,

Special thanks for taking the time to read my long post, and for providing me with your input. I found it invaluable - every year you read magazine and tech-pundits pronouncing Linux's "true" arrival on the desktop - and it really pays to do your homework. Thankfully sites like these are here to help get through all the details.  :) 

For now I think i'll shelve this project - the hardware installation would be no problem for me, but I think I might snags during my post-ubuntu install; particularly with the networking and wireless printing, which ironically, I would need resolved the quickest of all.  

In the meantime i'm going to do a bit more research on the different distros available now. Not to commit sacriledge or anything, *grin*, but are there any other distros that are novice friendly and/or that you've had prior experience with?

---

### Post by Nequeo on 2005-09-08
[QUOTE=Stretchman]Hey guys,

Special thanks for taking the time to read my long post, and for providing me with your input. I found it invaluable - every year you read magazine and tech-pundits pronouncing Linux's "true" arrival on the desktop - and it really pays to do your homework. Thankfully sites like these are here to help get through all the details.  :) 

For now I think i'll shelve this project - the hardware installation would be no problem for me, but I think I might snags during my post-ubuntu install; particularly with the networking and wireless printing, which ironically, I would need resolved the quickest of all.  

In the meantime i'm going to do a bit more research on the different distros available now. Not to commit sacriledge or anything, *grin*, but are there any other distros that are novice friendly and/or that you've had prior experience with?[/QUOTE]
 I hear good things about PCLinuxOS and Mepis. 

Mepis is Debian based, KDE by default, and tries to be as 'point and click' as possible. It will play more media than Ubuntu by default (placing it in a sort of grey legal area, as a result...), and comes with NDIS-wrapper installed out of the box. It's not true open source, I have heard it said, as they are not releasing the source-code for a lot of their configuration programs.

Anyway, if you don't care about that, Mepis might be good to try. 

PCLinuxOS also has a lot of fans. It's not Debian based, but if you haven't used Linux much that probably won't matter to you. I'd give both a shot, as they both come as LiveCDs. You can boot off the CDs, see if your hardware works, and do a hard-drive install if it does.

Cheers,

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=Stretchman]
In the meantime i'm going to do a bit more research on the different distros available now. Not to commit sacriledge or anything, *grin*, but are there any other distros that are novice friendly and/or that you've had prior experience with?[/QUOTE]

I can tell you right now....many wireless drivers simply don't exist. No matter waht distro you use, if they aren't made they aren't made. You either have to bite the bullet and use Ndiswrapper (which forces the Windows driver to work) or sell you card on Ebay and use the money to buy one that works a lot easier (thats what I did).

---

### Post by xmastree on 2005-09-08
> Video: Integrated ATI Radeon 9100 chipset (has both VGA and DVI out)I'm surprised no-one picked up on your choice of ATI video. Much better to go with Nvidia if possible, I've seen a lot of people having problems with ATI.

---

### Post by Lux Perpetua on 2005-09-08
Yes...from personal experience, I also do not recommend ATI. I think you'd have a hard time finding anybody in the Linux community recommending ATI, in fact. Unfortunately, I'm locked in :-(

---

### Post by Stretchman on 2005-09-08
Awesome input, much appreciated guys.  

I think i'll continue to read up on some of the basics concerning hardware compatability and driver support, that seems to be my weakest area when it comes to projects like this.  Are there any good web pages out there that detail 'approved' hardware that linux works well with. Conversely, are there any particular pieces of hardware in the video and networking arena that have worked well for you?  Your personal experience would probably help me out the most. 

I have a feeling that matching the right hardware with linux  is the key to smoothing out any snafu's that can arise with software compatability.

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=xmastree]I'm surprised no-one picked up on your choice of ATI video. [/QUOTE]

There is a good reason. That particular chipset has the best open source graphic drivers in existance! The most powerful card (ATI of Nvidia) that can say that.

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=Stretchman]
I have a feeling that matching the right hardware with linux  is the key to smoothing out any snafu's that can arise with software compatability.[/QUOTE]

It is. Use this page as your guide!

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Stretchman on 2005-09-09
Thanks for the link Poofy hair guy. I have a feeling i'll be using Ubuntu sooner than I thought....

---

