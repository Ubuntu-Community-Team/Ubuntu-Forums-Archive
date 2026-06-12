---
title: "Need Help Selecting Printer"
date: 2011-10-02
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2011-10-02
I would like some help selecting a new printer. I will be running Ubuntu 10.10 Powerpc on an E-mac G-4. I would like to buy a new wireless, inkjet printer that would be hard-wired to the Mac and allow wireless printing from my laptop. I’d like to spend between $75 and $150 (US), and I’d also like the ink cartridges to be reasonably priced. I’ve been told that *Brother, Canon, *and *H.P.* all have good compatibility with Linux. My problem is that I’ve also been told to make sure a printer has a driver available in CUPS before purchasing. I remember all too well the trouble I had finding a wireless USB dongle that would work with my applications, and that there can be compatibility issues depending on the distro and the specific equipment used. I’ve checked the available drivers for those brands at the CUPS website and their last update was mostly 2008! Very much like Linux distros, these printer manufacturers come out with new models almost every six months and none of the model numbers I see on the shelves even come close to the ones I see in CUPS. My brother bought a brand new *Lexmark *that had a "penguin" on the box and it wouldn’t work with either Xubuntu or Puppy Linux without hours spent on the phone with a service rep. I’d love to be able to understand all of the techno-crap that goes into this, but I’d gladly settle for someone just telling me of a printer that they bought that just flat works. Thanks in advance.

---

### Post by hansdown on 2011-10-02
Hi Javelin Dan.

I can't speak for the other brands, but hp has never let me down.

---

### Post by rsavage on 2011-10-03
Be careful with canon.  Although they release source files, they can be a mix of source code and binary blobs which mean the drivers won't compile on powerpc.
 
It is probably a good idea to look at the support pages for the printer you want before you buy.

---

### Post by Javelin Dan on 2011-10-03
Hansdown,
 
Please clarify - are you saying most any HP printer should work? Or do I need to look for the "penguine" on the box? Do they mostly plug-n-play? If I buy one and it doesn't, what do I do? I spent a lot of time trying to get my brother's Lexmark to work trying virtually every Lexmark driver listed in CUPS with no results. If this happens to me, what next?

---

### Post by Javelin Dan on 2011-10-03
One more question...
 
If a new printer fails to plug-n-play and there is no appropriate driver in CUPS, I know you may be able to access the correct driver from the manufacturer's website. If so, is there a step-by-step tutorial for configuring the driver from the terminal? I'm a raw newb and the command line is not my friend yet (if ever!). Simpler is better for me...

---

### Post by hansdown on 2011-10-03
HP was far sighted enough, to supply drivers for ubuntu.

hplip toolbox, has everything needed.

It comes installed already.

---

### Post by Javelin Dan on 2011-10-04
Thanks hansdown - I just bought an HP Deskjet wireless printer/copier/scanner. I hope to have time to play with it tonight. Succeed or fail, I'll post my results for the benefit of others.

---

### Post by hansdown on 2011-10-04
post back, and let us know, Javelin Dan.

It should work great.

---

### Post by Javelin Dan on 2011-10-05
[FONT=Arial][SIZE=3]Well, I sat down to install my printer last night and got it accomplished – almost! ARRRGGGHH…turns out, HP failed to include the printer cable in the box and after I downloaded the software on the computer and went through the set-up on the printer itself, it wanted me to connect the cable I didn’t have. Target wanted $15, I found one on ebay for $2.99 with free shipping – guess which way I’m gonna go? I already ordered one so I’ll have to wait a few days to finish. But I did want to chronicle my effort while it’s still fresh in my mind for the benefit of other newbies.[/SIZE][/FONT]
 
[SIZE=3][FONT=Arial]First of all, let me make it clear that I originally reported that I had purchased an HP Deskjet when it is actually a Photosmart d-110. This is because 1.) I didn’t have the box in front of me when I wrote that, and 2.) I’m an idiot. I first unpacked the printer and plugged it in and followed the simple set-up wizard that appears on its display screen. Following the prompts, I was able to recognize and configure my wireless net, and it printed a test page showing my wireless configuration settings. As suggested by hansdown (thanks!), I went to [/FONT][/SIZE][[FONT=Arial][SIZE=3]www.hplipopensource.com[/SIZE][/FONT]]("http://www.hplipopensource.com/")[SIZE=3][FONT=Arial] which is HP’s port to Linux based drivers and support. As a total newb, it took me a while to feel my way around the site and get comfortable with what they wanted me to do. I finally decided they wanted me to check and see if this particular printer was supported (it was), and then enter all the appropriate information concerning my printer and OS version. It then revealed the driver I needed which was titled “hplip3.11.10.” I went ahead and downloaded this driver and later stumbled across the fact that it was already supposed to be installed in Ubuntu 10.10 (I later saw it deleted in the set-up process), but I looked in the bin file and several others and couldn’t find it. Maybe someone with more experience could comment? I was then prompted to open a terminal and enter the commands “cd-desktop” then “conf-edit”. I got a brain fart and got hung up here because it took me a while to realize that the driver I downloaded was not in the “desktop”, but rather in my “downloads” file (I kept getting an error “file not found”). They warn you that you may have to amend that, but I couldn’t see the forest for the trees. I finally caught on and changed “cd-desktop” to “cd-downloads” and all was right with the world. An automatic installer was started and all I had to do was wait for my molasses-like wireless (connected to a cheap DSL service) to download all the necessary stuff – about a half hour. Then as it was going through its final configuration, it asked me to connect the cable I didn’t have. All told, with all my miscues and re-tries, I had about two hours in this. Way two much time for a pro, but as things go for me, not bad. I truly believe everything will be fine once I get the cable, but I’ll report for sure once I get everything connected. [/FONT][/SIZE]

---

### Post by hansdown on 2011-10-05
You'll be fine, Javelin Dan.

I must have had a brain fart too.

I should have mentioned, every hp printer I've bought, only required to be plugged in, and turned on.

Ubuntu recognized it, and all was well.

---

### Post by collisionystm on 2011-10-05
I always say HP. The HPLIP toolbox you can install can't be beat.

You can also look here.

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/databasedatabaseintro](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/databasedatabaseintro)

---

### Post by Javelin Dan on 2011-10-09
Well, I received my printer cable Friday, plugged it in and everything just flat worked! No configuring, no more set-up, everything just worked. I had a brief moment of heartburn when I hit the "scan" button on the printer and it displayed and error. But I went into Ubuntu help, clicked on scanning, and it showed me how to activate "simple scan" from the applications/graphics menu. Worked perfectly! I may start a new thread in a few days as I try to get my brother's G4 "Quicksilver" (also running Ubuntu 10.10 Ppc) to work with his Lexmark S-405. If anyone knows anything about that, please stay tuned. Thanks again to all who helped!

---

### Post by hansdown on 2011-10-09
Glad you got it working, Javelin Dan.

No tums required.

:D

---

### Post by kayaqiu on 2011-10-12
I like canon.Canon Printer Drivers v2.6 is right now what i am using. It works well.

---

### Post by rsavage on 2011-10-12
> **kayaqiu said:**
> I like canon.Canon Printer Drivers v2.6 is right now what i am using. It works well.
 
Hi, are your using an intel machine? Thanks

---

