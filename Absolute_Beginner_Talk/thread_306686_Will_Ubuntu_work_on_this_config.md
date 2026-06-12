---
title: "Will Ubuntu work on this config ???"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by ervyxx on 2006-11-25
Hi!

Years after my last try at linux, Ubuntu has got me excited and am going to try at it again. An all together a Fresh attempt. Wish me luck! Last time one thing or the other always got wrong and so I decided to call it off.

Well, my current config is as follows:

AMD Athlon64 3000+ [939-pin]
MSI RS482M4-ILD Motherboard (with onboard ATI Graphics & sound)
Transcend 512 MB DDR-400 SDRAM
LG Flatron L1730S LCD Flat Panel (@ 1280x1024 - 32 bit)
Hitachi 160 GB SATA-II HDD (currently in SATA I Mode)
Canon Pixma IP 3000 Printer
Canon LiDE 25 Scanner
Acer/BenQ S2W 3300U Scanner

I would like to know from you guys n gals, whether the above config is compatible with Ubuntu 6.06 LTS OR Ubuntu 6.10.

Also, please let me know the caveats.

I know people have faced problem especially with the motherboard.

But, has someone finally able to get their system working 100% with Ubuntu?

Also, would you guys recommend installing the 64-bit version or the 32-bit version?

---

### Post by taurus on 2006-11-25
The best way to test is to download the desktop CD (LiveCD) and boot from it.  See if your network, sound, etc. are working.  And if everything is working fine, the click the install icon to install it.

---

### Post by halitech on 2006-11-25
Like Taurus says, grab the live cd and try it and see if everything works. Only thing that might be tricky is going to be the scanners but everything else should be fine.

---

### Post by ervyxx on 2006-11-25
Thanks taurus & halitech for your quick responses.

You mean my ATI mobo (with onboard graphics & sound) won't be a problem. I've read around the forums that there are problems.

Anyway, I'll surely give it a try?

Which version do you guys suggest - 6.06 LTS or 6.10?

You mean everything apart from the scanner should work?

---

### Post by taurus on 2006-11-25
I would go with Dapper Drake, 6.06, for now since its a long term support...  However, there is nothing wrong with Edgy Eft, 6.10, if you want to try the latest version.

---

### Post by ervyxx on 2006-11-25
Hmm.. you are right.

Anything imp that i'll miss if I install 6.06 LTS instead of 6.10?

---

### Post by crispy_420 on 2006-11-25
According to [this]("http://www.sane-project.org/man/sane-plustek.5.html") your scanner, the Canon, should work too.

The Acer/Benq, not even a mention yes or no. I may be wrong and just didn't see it on the list [here]("http://www.sane-project.org/").

---

### Post by ervyxx on 2006-11-25
Thanks for the link dude. Canon is what am using regularly now.

Acer/BenQ is giving signals of dieing. But, I remember vaguely that my Acer/BenQ was supported by linux. This was many years back when I was trying linux.

---

### Post by AgenT on 2006-11-25
> **ervyxx said:**
> Canon Pixma IP 3000 Printer
Canon LiDE 25 Scanner
Acer/BenQ S2W 3000U Scanner
Canon is as bad as it gets. Canon is almost the worst company to use for a few reasons. The most important being: they refuse to have anyone add Linux support to their product and make it as hard as it can be for them to do so.

Taken from LinuxPrinting (see below for links):
> Canon provides essentially           no documentation without annoying NDAs; free software developers have           done everything by reverse engineering. The latest models use newer           protocols that are simply not understood.You will need to do some research on how to get your printer/scanner to work. You may be lucky and your Canon product may be supported.

I believe that Acer/BenQ do not make printers. If your printer has the Acer/BenQ logo, it is a re-badged printer. You will need to find out what the real manufacturer of the scanner is before you use it.

> **ervyxx said:**
> I would like to know from you guys n gals, whether the above config is compatible with Ubuntu 6.06 LTS OR Ubuntu 6.10.Both. Get both LiveCD's. If both work, use and install 6.10 since it will have newer versions of software. This may come in very handy if you have some trouble getting your scanner and printer to work. However, people report that 6.10 does not work with certain hardware as well as 6.06.

> **ervyxx said:**
> I know people have faced problem especially with the motherboard.This could be due to them trying amd64.

> **ervyxx said:**
>  But, has someone finally able to get their system working 100% with Ubuntu?I think you mean to ask: "has anyone with the EXACT same system as me got their system working 100% with Ubuntu". Doubtful that anyone has your exact system specifications so no one will be able to answer this question.

As for any system, then yes. Especially people that buy quality hardware. For example, just about anything from IBM (now Lenovo) works with Linux out of the box and even better than on Windows. IBM is a big supporter of Linux.

> **ervyxx said:**
> Also, would you guys recommend installing the 64-bit version or the 32-bit version?32-bit, definetly. Once you get your system running, you can always try switching up to 64 later. Do note that certain things, especially related to web browsers (flash, java) have problems in 64-bit because companies suck and they don't want to support 64-bit.

And you will be happy to know that on Linux, scanners and printers are limited only by 1) how well your product is supported and 2) by hardware limitations. You may be surprised down the line what your scanner or printer is actually capable of. Why? Because in Windows, companies purposefully create their drivers to disable certain features or capabilities so that you will buy their higher end versions of products. And also because they need to have their lower-end products be "weaker" than their higher-end ones. On Linux, no one cares for such things. ;)

Links you will find useful:
Scanners (with list of tested scanners):
[http://www.sane-project.org/](http://www.sane-project.org/)

Printers (with list of tested printers & company summary):
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

Good research places (besides these forums):
[http://www.linuxquestions.org/](http://www.linuxquestions.org/)
[http://www.linuxhelp.net/](http://www.linuxhelp.net/)
[http://pciids.sourceforge.net/](http://pciids.sourceforge.net/) (you only need this if you have to figure out what your hardware really is as brand names are usually re-badged)
[http://www.google.com/linux](http://www.google.com/linux) (yes, Google has its own Linux site! Did you know Google uses Ubuntu in their offices? Linux for their servers of course)

---

### Post by Ocxic on 2006-11-25
the generic kernel, is the only thing that coms to mind, with edgy theis kerel supports everything, instead of having to install a new/proper kernel like in breezy. and i think xgl is installed by default.

---

### Post by ervyxx on 2006-11-25
> **crispy_420 said:**
> According to [this]("http://www.sane-project.org/man/sane-plustek.5.html") your scanner, the Canon, should work too.

The Acer/Benq, not even a mention yes or no. I may be wrong and just didn't see it on the list [here]("http://www.sane-project.org/").
Hey, sorry for the typo. My Acer/BenQ model is 3300U and NOT 3000U which i mentioned wrongly. Sorry for the same. I've edited it in my initial post.

As I said, my Acer/BenQ also seems to be supported.

---

### Post by AgenT on 2006-11-25
> **Ocxic said:**
> and i think xgl is installed by default.
That is the plan for Feisty, not Edgy.

See this presentation at Google HQ by Mark Shuttleworth:
[http://video.google.com/videoplay?docid=2728972720932273543](http://video.google.com/videoplay?docid=2728972720932273543)

---

### Post by AgenT on 2006-11-25
> **ervyxx said:**
> As I said, my Acer/BenQ also seems to be supported.Great! You are downloading the LiveCD iso, right? ;) You could be trying Ubuntu very quickly. Remember, using a LiveCD does not change anything on your system. You have to click Install on the desktop for that to happen.

---

### Post by ervyxx on 2006-11-25
> **AgenT said:**
> Canon is as bad as it gets. Canon is almost the worst company to use for a few reasons. The most important being: they refuse to have anyone add Linux support to their product and make it as hard as it can be for them to do so.

Taken from LinuxPrinting (see below for links):
You will need to do some research on how to get your printer/scanner to work. You may be lucky and your Canon product may be supported.

I believe that Acer/BenQ do not make printers. If your printer has the Acer/BenQ logo, it is a re-badged printer. You will need to find out what the real manufacturer of the scanner is before you use it.

Both. Get both LiveCD's. If both work, use and install 6.10 since it will have newer versions of software. This may come in very handy if you have some trouble getting your scanner and printer to work. However, people report that 6.10 does not work with certain hardware as well as 6.06.

This could be due to them trying amd64.

I think you mean to ask: "has anyone with the EXACT same system as me got their system working 100% with Ubuntu". Doubtful that anyone has your exact system specifications so no one will be able to answer this question.

As for any system, then yes. Especially people that buy quality hardware. For example, just about anything from IBM (now Lenovo) works with Linux out of the box and even better than on Windows. IBM is a big supporter of Linux.

32-bit, definetly. Once you get your system running, you can always try switching up to 64 later. Do note that certain things, especially related to web browsers (flash, java) have problems in 64-bit because companies suck and they don't want to support 64-bit.

And you will be happy to know that on Linux, scanners and printers are limited only by 1) how well your product is supported and 2) by hardware limitations. You may be surprised down the line what your scanner or printer is actually capable of. Why? Because in Windows, companies purposefully create their drivers to disable certain features or capabilities so that you will buy their higher end versions of products. And also because they need to have their lower-end products be "weaker" than their higher-end ones. On Linux, no one cares for such things. ;)

Links you will find useful:
Scanners (with list of tested scanners):
[http://www.sane-project.org/](http://www.sane-project.org/)

Printers (with list of tested printers & company summary):
[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

Good research places (besides these forums):
[http://www.linuxquestions.org/](http://www.linuxquestions.org/)
[http://www.linuxhelp.net/](http://www.linuxhelp.net/)
[http://pciids.sourceforge.net/](http://pciids.sourceforge.net/) (you only need this if you have to figure out what your hardware really is as brand names are usually re-badged)
[http://www.google.com/linux](http://www.google.com/linux) (yes, Google has its own Linux site! Did you know Google uses Ubuntu in their offices? Linux for their servers of course)
@AgenT

Whooops! That's a big post. Thanks for sparing the time and posting .

Let me go point by point.

1. It's bad hear about Canon not wanting to support linux. I just got a Canon Digital IXUS 750 Digicam. Now, most of my peripherals are from Canon. Have done some research regarding the printers. Read somewhere that my Canon Pixma IP 3000 is supported in Linux as Canon Japan has published Linux drivers for them.

2. I believe you have been mistakened. I don't have a Acer/BenQ Printer. I too thought Acer/BenQ don't make printers ;)

3. Could you elaborate your comment on AMD64?

4. I know my query - if anyone has got their system 100% working with Ubuntu was vague. I wanted to say that, whether anyone with a similar mobo could setup Ubuntu 100% (with graphics & sound).

5. OK - I'll surely go with 32-bit Version first.

Thanks for the links dude.

But, am a bit nervous about the Canon part :(

---

### Post by ervyxx on 2006-11-25
> **Ocxic said:**
> the generic kernel, is the only thing that coms to mind, with edgy theis kerel supports everything, instead of having to install a new/proper kernel like in breezy. and i think xgl is installed by default.
I could understand about the Generic kernel. But, what's xgl?

---

### Post by ervyxx on 2006-11-25
> **AgenT said:**
> Great! You are downloading the LiveCD iso, right? ;) You could be trying Ubuntu very quickly. Remember, using a LiveCD does not change anything on your system. You have to click Install on the desktop for that to happen.
Wish I could! I've a slow 64 Kbps connection at home. I'll download it from Office on monday. It'll be quick as I have a 640 Kbps DSL connection there.

---

### Post by AgenT on 2006-11-25
> **ervyxx said:**
> 1. It's bad hear about Canon not wanting to support linux. I just got a Canon Digital IXUS 750 Digicam. Now, most of my peripherals are from Canon. Have done some research regarding the printers. Read somewhere that my Canon Pixma IP 3000 is supported in Linux as Canon Japan has published Linux drivers for them.That is good news about your Canon Pixma IP 3000 if it is true. And do not worry about your digital camera. Most cameras have at least two modes and one of those is always compatible with Linux. The other mode may or may not be compatible. If your camera does not work, look in the manual on how to change these access modes (PTP is what I think one of them is called, but I do not remember).

> **ervyxx said:**
>  2. I believe you have been mistakened. I don't have a Acer/BenQ Printer. I too thought Acer/BenQ don't make printers ;)OK.

> **ervyxx said:**
>  3. Could you elaborate your comment on AMD64?Which comment? I do not know much about amd64 except that it is 100% supported in Linux. However, this does not mean that your motherboard is 100% compatible, but it probably is. The biggest problem with amd64 is that a lot of software, especially [non-free software]("http://en.wikipedia.org/wiki/Proprietary_software") (proprietary), is not compatible. This is the fault of those who make the proprietary software. They are not willing to make it compatible right now. A good example with this is Flash support. Not sure, but flash may not be available on amd64.

> **ervyxx said:**
>  4. I know my query - if anyone has got their system 100% working with Ubuntu was vague. I wanted to say that, whether anyone with a similar mobo could setup Ubuntu 100% (with graphics & sound).To test your motherboard, graphics and sound support, use the LiveCD. If it works on the LiveCD it means that it should work without any configuration when you install. If it does not work, it probably means that it will only work with some tweaking.

Also note that people have a hard time with dial-up modems because most modems available now are made to only work on Windows.

> **ervyxx said:**
> But, am a bit nervous about the Canon part :(Do not be so nervous.  Here is some research for you to read:
Canon Pixma IP 3000 Printer is "partially" supported. I do not know what that means exactly. Probably means that it works fine for regular printing. Read that page and it will tell you what printer driver to use (this driver should already be available in Ubuntu).

[Linux Printing Canon Pixma IP 3000]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP3000")
[Google Linux Research Link]("http://www.google.com/linux?num=100&hl=en&lr=&q=canon+pixma+ip+3000+printer&btnG=Search")

---

### Post by AgenT on 2006-11-25
> **ervyxx said:**
> I could understand about the Generic kernel. But, what's xgl?
It is very new desktop technology (started early 2006!). Instead of trying to explain it to you, I will give you a link to a movie that shows you what it is. Watch it and be amazed. More amazing than anything Microsoft or Apple have to offer.
[XGL Demo Video]("http://video.google.com/videoplay?docid=6809307015623593442") [Google.com]

---

### Post by ervyxx on 2006-11-25
@AgenT

1. Thanks for the Digital Camera tip. Does Ubuntu support External USB Memory Card reader? If yes, I'll not waste time searching on how to make my digi cam work with Ubuntu.

2. By Flash, do you mean Flash Drives? Do Transcend USB Flash drives work with Ubuntu the same way as they work on XP i.e., Plug 'n' Play? I use them a lot to carry data from home to office and back.

3. I'll definately see how everything goes with the LiveCD first. Regarding modems, you mean Winmodems right? Well, I have an old external GVC modem. And my internet comes through my router so, I don't think I'll have to do any config.

4. I'll go through that Canon Pixma IP 3000 page.

Thanks for the XGL link.

---

### Post by AgenT on 2006-11-25
> **ervyxx said:**
> 1. Thanks for the Digital Camera tip. Does Ubuntu support External USB Memory Card reader? If yes, I'll not waste time searching on how to make my digi cam work with Ubuntu.This depends on what USB memory card reader. There is no reason to do any research on your camera. It will work one way or another and the chances are it will work without you having to do anything except plugging it in using USB cable.

> **ervyxx said:**
>  2. By Flash, do you mean Flash Drives? Do Transcend USB Flash drives work with Ubuntu the same way as they work on XP i.e., Plug 'n' Play? I use them a lot to carry data from home to office and back.No. Every flash drive that I have used worked fine in Ubuntu. What I mean was [Adobe Flash]("http://en.wikipedia.org/wiki/Macromedia_Flash") that is used on some websites (usually the annoying ones), by website games and by website advertisements.

> **ervyxx said:**
>  3. I'll definately see how everything goes with the LiveCD first. Regarding modems, you mean Winmodems right? Well, I have an old external GVC modem. And my internet comes through my router so, I don't think I'll have to do any config.Yes, I meant winmodems.

> **ervyxx said:**
>  4. I'll go through that Canon Pixma IP 3000 page.Good luck with that.

And remember: once you install Ubuntu and something does not work, search these forums and ask.

> **ervyxx said:**
>  Thanks for the XGL link.Enjoy watching it.

---

### Post by ervyxx on 2006-11-25
Thanks! Dude. I'm going surely give it a try.

I'll be having a lot of questions when I install it ;)

LOL

---

### Post by ervyxx on 2006-12-01
Hi!

Downloading Ubuntu 6.10 - 81% complete.

Am damn excited !!!

I'll however be installing it first on my Second PC as I don't have the time to back up my data on it.

The config is as follows:

Intel Pentium III 800MHz (Coppermine)
Asus CUSL2-C (i815ep) Mobo
128 MB RAM (as the other 128 MB chip died few days back)
nVidia Riva TNT2 M64 - 32 MB AGP 4x
Seagate 10 GB HDD
Lite-ON 48x24x48x CD-RW


I hope there won't be any problems with this config as it is quite old.

Am especially concerned about the low RAM.

---

### Post by Sef on 2006-12-01
> The config is as follows:

Intel Pentium III 800MHz (Coppermine)
Asus CUSL2-C (i815ep) Mobo
128 MB RAM (as the other 128 MB chip died few days back)
nVidia Riva TNT2 M64 - 32 MB AGP 4x
Seagate 10 GB HDD
Lite-ON 48x24x48x CD-RW


I hope there won't be any problems with this config as it is quite old.

Am especially concerned about the low RAM.

Ubuntu really needs 256 ram to work decently.  However, [Xubuntu]("http://xubuntu.org/") will work well on those specs.  I have it on my laptop with 700 MHz and 128 ram and it flies.

---

### Post by ervyxx on 2006-12-01
Thanks. I'll do something about the RAM. Will get a new one most probably. But, even if slow, will it work?

Also, do you see any other problematic hardware?

---

### Post by ervyxx on 2006-12-01
BTW, Download Complete! Booted through the live cd and everything worked flawlessly except the touchpad.

---

### Post by AgenT on 2006-12-01
Desktop CD Install requires a minimum of 192 MB RAM to install. If you have less, there is the Alternate CD. However, Alternate CD is more difficult to install from because it asks a lot more questions that you need the answers to. This is because it is much more flexible and powerful. Alternate Install CD may be called "Advanced Install CD".

You can still try the Desktop CD install.

And if you want to install Xubuntu, just install Ubuntu like normal and just add xubuntu-desktop after you are done.

---

### Post by ervyxx on 2006-12-01
Hi!

There is one problem. My old colour monitor - Samtron SC-428PS cannot go beyond 800x600 resolution.

However, Ubuntu goes directly to 1024*768 and I can see very bad image - (3 small screens with 3 mouse pointers - this is how my monitor reacts when you force it to a resolution beyond 800x600).

I tried the option on the main menu and select everything from 640x48xx16 to 800x600x32 but, it still goes to 1024*768. and at some point it hangs.

How do I boot from the LiveCD at 800x600x32?

---

