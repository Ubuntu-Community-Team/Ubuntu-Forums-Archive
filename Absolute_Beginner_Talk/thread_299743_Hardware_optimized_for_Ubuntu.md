---
title: "Hardware optimized for Ubuntu"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by arsenik on 2006-11-14
Okay after a month with Ubuntu on my laptop I'm ready to have a dedicated linux server.  I want to build it with parts from newegg and I know (through my experience with my laptop) that some hardware just isn't too linux friendly (ATI comes to mind).  Is there a list of motherboards/sound cars/video cards/etc that play nicely with ubuntu so I don't end up buying something that doesn't work?

---

### Post by arsenik on 2006-11-14
almost forgot to say: I want the monitor to be a TV.. so I'm gonna need a video card that supports output to a HDTV.

---

### Post by David Corrales on 2006-11-14
Get nvidia video cards, they're superb for linux. Just look for one with tv-out.
Processors: right now the Core Duo 2 is the superior option all round.
Mobo's: Hmm, just make sure the SATA controller is supported.
Hard drives: SATA :p
Sound cards: since it's a server, you probably don't need a mega sound card. The integrated one will probably suffice.

---

### Post by turbojugend_gr on 2006-11-14
I 'll agree with nvdia, STRONGLY disagree with Intels, AMD is officially and actively supporting Linux (while Intel does that only with other monopolies like M$) and my 4600+ X2 which I bought 11 months ago still rocks every intel, and is by far cheaper. ASUS Mobos for me work great (I have 2 pc's with asus mobo and all cards are nicely recognized by ubuntu and suse. Sata's of course since it's a server (sata's can be added/removed real time which is handy for servers... anyway if you wish a name go for Seagate's) since it's a server I see no use for a sound card, most nice mobos have a decent one anyhow. Oh definately go for a lan router.

Cheers, TJ

---

### Post by arsenik on 2006-11-14
what is a lan router?

---

### Post by unrealmstr on 2006-11-14
Loacal area network router

---

### Post by That_Geek on 2006-11-14
local area network router

Edit: ahh! you beat me to it

---

### Post by arsenik on 2006-11-14
ur saying use ubuntu as my router?

---

### Post by turbojugend_gr on 2006-11-15
LOL, no i mean you should buy a router that connect to your LAN card, instead of a modem/router that connects to your USB, thus in need of drivers.

In other words a LAN router would keep your PC logged even if your PC is cosed (you only log out when you power off the router) and do not depends on software drivers to do it's job. On the contrary a USB modem/router needs drivers and needs you to log in each time you open your PC.

So go for a LAN router.

Cheers, TJ.

P.S.: If despite my explanation you are confused, ask for a modem/router that connects via LAN, instead of connecting via USB port.

---

### Post by Redache on 2006-11-15
I think what your on about just a Router, there's no USB routers, it's All LAN (Ethernet,BNC Whatever decade your stuck in). USB modems on the other hand are awkward beasts in Linux so a Router is a much more viable option and they aren't *too* expensive compared to a normal ADSL modem.

If you can choose a Wired router as Wireless ones are still pretty dodgy with the whole connection 24/7 thing. Typically they are simple to set up or they come with an auto configure option which asks for your ISP, Username (For the ISP) and Password.

As for Processors, I've read of a few issues with Core 2 Duo's so it's safer to stick with AMD as they are a cheap option and are VERY Good processors (There's the problems with thermal diodes but meh you get what you pay for). Video card wize NVidia, Since ATI are very sketchy on a Linux system (Crap drivers basically). 

Hard Drives are whatever you want them to be, SATA is the better option obviously as it's new tech and has some sexy things involved with it. All of the brands are equal, there really isn't much difference (Price or quality wize) Go for the name you like the most (Western Digital,Seagate/Maxtor). Personally I like Seagate, Because I live by the sea....

Mobo Wize, Asus have always been good fellow AVOID PC Chips and ECS Mobo's like the plauge. Cheap - bad English manuals - Awfull parts - BAD Processor recognition (I've got a PC Chips at the mo and it keeps telling me XP 3000+ is 1.2GHZ :S)

Soundcard wize - Creative blow with Linux support, literally the WORST company for it. (We'll release it in a year, honest). I've got a Audigy 2 Platinum EX with a breakout box and I'm thankfull that someone reversed engineered a driver for it, otherwise I'd have a lovely Black and Grey Box to put my speaker on and nothing else. Usually intergrated soundcards will be fine for a server.

If you want a powerfull server then look into (If you have a large pit of cash)
AMD Opteron as a processor
ECC RAM (error Checking - crazy expensive)
A Few SATA disks set up as RAID (Choose the best level for you).
Tape Drive (For the backing up - again crazy expensive)

But that's if you really want something special in a server, what I said before will suffice for a basic Server.

Just remember ROUTERS ARE YOUR BEST FRIEND!.

---

### Post by arsenik on 2006-11-16
Thanks guys. I have a cable modem -> Router -> network so I should be fine.  I want my linux box so I can do NFS shares on my home network and ssh from work to bypass their proxy :)  ssh -X is a lovely command.  Ubuntu has really changed my outlook on linux, the help provided here is amazing.  I am thinking of buying a shuttle barebone with the parts you guys described so its nice looking.  I haven't turned my windowz machine on since I've installed ubuntu (except for Microsoft Money).

Thanks guys.

---

### Post by turbojugend_gr on 2006-11-17
> ROUTERS ARE YOUR BEST FRIEND!
Couldn't agree more... ;)

---

