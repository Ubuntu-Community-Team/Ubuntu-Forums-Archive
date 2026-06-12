---
title: "Rebuilding ibook G3 for girlfriend. Help picking a Linux distro"
date: 2007-11-07
forum: Apple PPC Users
---

### Post by employeeno5 on 2007-11-07
My girlfriend wants a laptop that is very compact, white(ish) and will be used pretty much solely for web browsing (wirelessly) and occasional word processing. She/I do not want to spend much money on this as it would really require very little.
Her needs make the new ASUS eee PC ideal for her with one exception; she really requires a cd drive. 

I have an opportunity to buy, very inexpensively, an old G3 ibook in which everything works, but it has no hard drive and the keyboard is a little smashed-up. She loves the design of those computers.
I'm thinking about buying this ibook, replacing the keyboard, installing a hard drive and loading in "user-friendly" gui distro of Linux for her. 
I'm wondering if there is a version Ubuntu ideal for this sort of project. Would Xubuntu run better, or an entirely different distro run better? Any OS would of course need PPC architecture support, and I'd have to get AirPort running on it for wireless. 
I'm using Gutsy 7.10 on my dell right now (love it), but I'm relatively inexperienced with Linux. I'm willing to do the leg work, but I am hoping someone can point me in the right direction  before I decide if I should pick-up this old ibook or if this just isn't a practical project.

Any advice is hugely appreciated  
Thanks!

EDIT:
I forgot the mention, this is only a 500mhz G3. Its only got 128MB of RAM but I intend to upgrade that to 512MB.

---

### Post by catawalks on 2007-11-07
My 900mhz 256mb G3 ibook runs 7.04 very nicely even with the desktop effects enabled. The only problem I have with mine is the lack of WPA support for the non-extreme airport cards.

So if you don't even plan on using WPA encryption then I would say go for it and use regular ubuntu. If you wish Xubuntu will run even better but that is up to you.

The other thing is I'm not sure if you can upgrade the regular airport card to an extreme and get away with that too.

---

### Post by employeeno5 on 2007-11-07
WPA would not typically be an issue for us so that sounds good. I checked out Wikipedia's entry on AirPort cards and from what I took from that G3s won't accept airport extremes. That certainly isn't anything like official documentation though so perhaps one can. Also, I've never owned an Apple myself, so though I'm pretty familiar with (and found of) the various incarnations of OSX, I've got no real personal history or knowledge about their hardware. 
That's pretty much my only worry. Not having much experience with Apple's hardware, I just want to make sure I can get a decent desktop environment and wireless running reasonably on a machine that old.

Your report of things running well though has me feeling cheery about this idea. It will make a fantastic Christmas gift if I can pull this off. Thanks for the input!

---

### Post by Auria on 2007-11-07
Ubuntu can work well on PPC, but you need to be aware of its limitations first, so that you don't get disappointer later. Mainly, only the open-source 3D drivers and no adobe flash.

apart from that it works rather well here, of course it needed more tweaking than OS X. PS Gutsy generaly has many PPC bugs so i'd keep a feisty CD around too

---

### Post by smackswell on 2007-11-09
the whole poor flash support for PPC thing is prolly gonna be a major turn off for her. something to keep in mind...

---

### Post by meretricis on 2007-11-14
There's Gnash for 6.10 and 7.04. It's why I upgraded from dapper 6.06

---

### Post by lavaramano on 2007-11-17
my advice is to look for other computers, i have a ibook g3 and this problem: 
[http://geektechnique.org/projectlab/726/diy-obsolete-ibook-logic-board-repair](http://geektechnique.org/projectlab/726/diy-obsolete-ibook-logic-board-repair)
the logic board (mother board) has a problem with the video chip.

i managed to fix this problem but i dont know if it's worth to spend money on a broken computer that works just for one month and then you have to use it as a leg for you sofa. ;P

---

### Post by employeeno5 on 2007-11-23
> my advice is to look for other computers, i have a ibook g3 and this problem:
[http://geektechnique.org/projectlab/...c-board-repair](http://geektechnique.org/projectlab/...c-board-repair)
the logic board (mother board) has a problem with the video chip.

i managed to fix this problem but i dont know if it's worth to spend money on a broken computer that works just for one month and then you have to use it as a leg for you sofa. ;P

Yes, I'm aware of this issue and I actually ran into the same blog post about the tea candle fix (pretty inventive). My primary reason for going with this computer is because my girlfriend really wants one that looks just like this. She's wants something very small (not widescreen) and all white. Picky I know, and like I said earlier I would have gotten her one of the new Asus eeePCs if she didn't insist on an optical drive. She said she doesn't want me to buy anything expensive or newer like Macbook either because she really has zero interest in a computer outside of casual web browsing and her Rosetta Stone language program. Pretty much she just wants a toy to use when I'm working on my computer (which is what she currently uses). She also hasn't requested a computer and isn't expecting one for Christmas, I'm just going with what I know of her preferences from prior conversations about maybe buying her a computer of her own. The G4's have their own set of defects too so I figured if I'm going to attempt to put something together myself cheaply, knowing I might completely fail, I may as well  start off with the cheap stuff. So, if this whole project goes completely to crap I've only spent less than $300 and have had a fun learning experience. I'll just have to suck it up and buy her something shiny and new.  

Actually as an update, I currently have currently assembled a 500MGHz G3 12" iBook running beautifully with 512MB RAM and 30GB hardrive. I scavenged all of the parts from 3 different broken iBooks I got extremely cheaply (under $300 for the whole project; huzzah for craigslist & ebay). 
The final build has a case and screen look great. I've got an airport card in it and a battery in it with about 1-1/2 of life when fully charged.
I've installed OS X 10.3.9 (Panther) on it because of the flash issues and also because of the fact that the one thing other than web browsing that my girlfriend uses a computer for is her "Rosetta Stone" language program, which after much playing around and research, it didn't look like I was going to be able to get running properly in Linux (her version is rather new and though I read reports of much earlier Rosetta Stone programs running with WINE, I was having no luck with the latest). Panther actually runs great with the minimal specs. My biggest reason for wanting Linux was to conserve resources on a computer she doesn't need to do much, save a little extra money, and well because I'm just tickled pink with the open source movement. 
This is a gift for her though so based on her needs OS X was the way to go. 
All and all I'm very pleased with myself given the amount of money I put into it, and how much enjoyed doing this, especially having never worked with computer hardware before. The guides on ifixit.com were essential.

Also, 
from the three computers I cannibalized I've been able put together and entire second running computer from the left-over parts. This one's case is very beat-up, and the screen has a small white-ish smudge near one bottom corner (barely  noticeable when running) and it still needs a hard drive and a battery (The thing also smells like burnt hair). It boots onto a live disk just fine though. I'm looking forward to eventually tinkering with Linux on this one and seeing if I can't make it a bit of a road-warrior for myself. I've got a Dell Inspiron E1505 with a nice big screen that's a fantastic computer I use regularly  at home, but for a laptop it's so heavy and cumbersome I never want to tote this around to a coffee shop or pull it out on an airplane or train. If I take it anywhere at all it stays nice and well packed into it's case until I'm well settled at my destination. The iBook being so compact and old seems like a something great to just toss into a bag on the go. This second ibook also might come in handy with some spare parts if any in the one I built for the gf starts to fail.

Thanks for all the advice, I definitely wasn't aware of the flash problems when I first posted this project. 
I'm intending right now, once I get the second junkier computer running for myself, to try out Xubuntu on it, but if anyone else knows any other Linux distros particularly well suited for a slow PowerPC drop me a line, I'll be interested.

---

