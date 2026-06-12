---
title: "xubuntu advise pls: helping my mum out with an old computer"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by marquee moon on 2008-01-22
My 67 yr old mum has an old Pentium II Compaq, presently running Win98. She hates it, becuase it runs so slowly. 

Her computing is very simple: she does some basic household acounts in excel, writes letters and produces church cleaning rotas in word, sends the occasional e-mail to relatives & friends, and manages her digital photos. Oh yes, she also loves playing sudoku, which win98 doesnt have. 

She's been advised that the computer is out of date and that she needs to replace it. That drives me crazy! I cant cope with Vistas, let alone my old mum! 

So I'm hatching a plan to install Xubuntu on her machine. I want it go as smoothly as possible, so she gets no sudden surprises. Before I go any further, I need a little advice:

1) She presently has an in-built 56k win-modem. I understand this probably this won't work, so I've sourced a second hand external 56k modem (for free!). Are there some external modems that also dont work? What is the proccess for setting up the modem? (is this explained in the xubuntu guide?) will I need to know the details in advance to find the correct drivers? 

2) Her internet connection is slow, so I'm intendinig that she will not need to update via the internet. What I would like to do is setup up xubuntu to not look for internet updates, then everytime I visit, re-install the latest updated xubuntu via CD. Can I download the latest CD and re-install without effecting her profile? If not, is there a way of having the latest xubuntu release and updating her system via this CD so she doesnt loose her settings? 

3) To start with, I'm hoping to squeeze xubuntu onto her hard drive without deleting windows, so that if she doesnt like it, she can go back to the bad old days. I'd imagine her hardrive isnt that big (maybe  20 Gb max), so how much can I get away with on the Linux partition just until she's happy to get rid of windows? 

4) With Ubuntu Gutsy Gibon, the user can save to windows partitions. Is this the same with the latest xubuntu? 

Thank you very much for you help. If all goes well, my mum will have a healthy new computer shortly! 

MM

---

### Post by hahahan on 2008-01-22
Xubuntu Gutsy Gibbon might be to havy for such an oldtimer, It could be better to use a gentoo distro or damn small linux one  [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by Kilz on 2008-01-22
> **marquee moon said:**
> My 67 yr old mum has an old Pentium II Compaq, presently running Win98. She hates it, becuase it runs so slowly. 

Her computing is very simple: she does some basic household acounts in excel, writes letters and produces church cleaning rotas in word, sends the occasional e-mail to relatives & friends, and manages her digital photos. Oh yes, she also loves playing sudoku, which win98 doesnt have. 

She's been advised that the computer is out of date and that she needs to replace it. That drives me crazy! I cant cope with Vistas, let alone my old mum! 

So I'm hatching a plan to install Xubuntu on her machine. I want it go as smoothly as possible, so she gets no sudden surprises. Before I go any further, I need a little advice:

1) She presently has an in-built 56k win-modem. I understand this probably this won't work, so I've sourced a second hand external 56k modem (for free!). Are there some external modems that also dont work? What is the proccess for setting up the modem? (is this explained in the xubuntu guide?) will I need to know the details in advance to find the correct drivers? 

2) Her internet connection is slow, so I'm intendinig that she will not need to update via the internet. What I would like to do is setup up xubuntu to not look for internet updates, then everytime I visit, re-install the latest updated xubuntu via CD. Can I download the latest CD and re-install without effecting her profile? If not, is there a way of having the latest xubuntu release and updating her system via this CD so she doesnt loose her settings? 

3) To start with, I'm hoping to squeeze xubuntu onto her hard drive without deleting windows, so that if she doesnt like it, she can go back to the bad old days. I'd imagine her hardrive isnt that big (maybe  20 Gb max), so how much can I get away with on the Linux partition just until she's happy to get rid of windows? 

4) With Ubuntu Gutsy Gibon, the user can save to windows partitions. Is this the same with the latest xubuntu? 

Thank you very much for you help. If all goes well, my mum will have a healthy new computer shortly! 

MM

This page will help you because that old of a computer may have real low ram. Xubuntu may not be able to run with less that 128, and tat real slow. Icewm is a good solution for those low memory systems. The distro [dam small linux ]("http://damnsmalllinux.org/")is also good from what I have read.
1. You may be surprised, that old of a modem may work.
2. You should be able to disable updates in software settings and use an install cd as a repository.
3. A few gigs are needed. This where you will run into problems.
4. Xubuntu has a Gutsy version. The only difference is the desktop to my knowledge.

---

### Post by gn2 on 2008-01-22
[Elive]("http://www.elivecd.org/") may also be worth trying, it has very low system requirements, P2 266mhz, 64mb RAM.

---

### Post by DrMega on 2008-01-22
I recently installed Ubuntu Gutsy (7.10) on a machine with the following spec:

* AMD Athlon 800MHz
* 256MB RAM (192 MB available because the on board graphics pinch the other 64MB)
* On board graphics and sound
* 20GB hard disk

I had to switch the desktop to Xfce (the xubuntu-desktop package in synaptic) because Gnome was too slow, but other than that it is fine.

On an even older machine (spec as follows):
* PIII 450MHz
* 384MB RAM
* 4MB graphics
* 20GB hard disk

I installed Ubuntu Dapper as a dual boot with Windows 2000, giving a max of 8GB to Ubuntu. It was fine.

---

### Post by DJiNN on 2008-01-22
I would definitely not install Xubuntu (Gutsy) on such a machine.... it would work, but it would be quite slow & tiresome.

I can recommend the lightweight PCLOS versions, especially TinyMe, which uses OpenBox as a WM but has a lot of functionality.  Also, if you don't mind installing a few extra apps & doing some minor configuration, then PCLOS "MiniMe" is definitely worth a go.  It's KDE based, but is completely stripped down. You won't need a browser because Konqueror already IS a browser, & if you stick to basic KDE apps, it should run pretty well. 

Depends if you like a bit of bling & reasonably easy config or you're after something REALLY lightweight like DSL or Puppy etc. 

I've never tried anything on a PII, but all of the above run superfast on my PIII. :)

---

### Post by sleepingdragon on 2008-01-22
I'm voting for Damn Small Linux on this one. There's a new version - 4.2.2, which has a half-decent interface and can easily be squeezed into a very small hard drive. Processor and memory demands are very low, so an old laptop should get on just fine. I managed with 2GB of hard drive and 32Mb of RAM... oh, those were the days.

I used DSL on dialup with an external modem, just use the "pppconfig" tool to set it up, it's pretty easy. I seem to recall the location of a serial modem is "/dev/ttyS0" in DSL (pppconfig will ask you to specify this location, the rest of pppconfig is in plain english). There's a word processor and spreadsheet in DSL too, so your mum can get into those church rotas nice 'n' easy. I remember seeing a picture viewer for those digital pics, and SudoKu is in there somewhere. I suspect that digital camera will simply show up as a Removable Drive.

The printer config might be a bit scary, it's not the friendliest, but there is good support in the DSL forums. They've helped me a couple of times with printer settings. As long as you're on an HP or Epson printer, you'll be fine - you've only got to do it once...

Internet is handled by FF (but I would install their Opera download), and email is on Sylpheed. You will probably need to do a couple of small downloads initially (like "rc.firewall" to handle you ports), but there's no regular updates in DSL. Like any Linux box, there's no anti-virus updates to worry about.

DSL also has a central download repository like Ubuntu, so any further downloads should be easy to find. All DSL software is designed to be small, so even on dialup they shouldn't take too long to download. There are exceptions, but full specs are given before you commit to anything.

---

### Post by Redptc on 2008-01-22
Dear M/Moon

Adding more ram will not only spark up windows 98, it will make it possible to run ubuntu. If you put in another, inexpensive hard drive, say 80meg, you have a good base for ubuntu 7.10.

I don't know where you are but Ubuntu, 256 or 512 ram and a small hard drive are not really very expensive these days and could work magic on that machine!

---

### Post by marquee moon on 2008-01-22
thanks for all the replies... lots to think about. 

Although I like DSL,( and I'm amazed just how small it is), I'm not sure my mum would get on with the file manager. I've just downloaded the new version, and the file manager is still a little tricky if your used to windows. 

Puppy is good...a nice compromise between functionality, size and appearance.

I'll check out PCLOS also . 

While a little bit of extra RAM and maybe a new hard drive would be easily sorted (I live in UK), this isn't really the point.  I believe that for what my mum needs from her computer, there are operating systems out there that are totally adequate. So I'd prefer to go down this route first. 

thanks once again for the useful advice.

mm

---

### Post by sleepingdragon on 2008-01-24
Puppy is good, but I would be somewhat concerned with 64Mb of RAM, 92Mb is OK, anything else is a bonus. You didn't specify your memory, but yes, Puppy will certainly serve your needs.

---

