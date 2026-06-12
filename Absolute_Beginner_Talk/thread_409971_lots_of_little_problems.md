---
title: "lots of little problems"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by mad chey on 2007-04-15
i seem to have gotten lots of problems of late

1.  firefox randomly shuts down, it can be when pressing enter after typing in googles search bar, or when you click on a link anytime with no warning it just totally closes and no error message at all, opens straight back up but will continue to randomly shut down

2.  I have utorrent running with wine and everything seemed to go smoothly until i leave it running for long periods, it locks the whole pc up and a hard shut down is the only solution, and it seems to be constantly rechecking my torrents like its forgotten they are there and sometimes locks up whilst doing that.  I did try Azureus but i was having problems with that as the scheduler reactivates all not just the paused ones, and you can choose to focus on one but only one, with utorrent i can seed all and d/l one and stop the rest and the scheduler doesnt change their stopped status as it only pauses/unpauses.

3.  randomly when booting up ubuntu (dapper drake) it gets to the hardware abstraction layer hald, it just hang, if you leave it, eventually it will continue on and show you the login screen but after you have logged in all you get is a brown background and the top and bottom bars but naf all on them.  there is no shutdown icon in the top right and ctrl+alt+backspace restarts gnome but the same result as before, so had to do a hard shut down, now heres the thing maybe coincidence but if i shut i down and leave it for say count of 20 then fire back up all loads up good, but if i do a restart so their is no break its hit and miss if it loads up ok or not sometimes it does sometimes it dont.

4.  I cant get frostwire to load past the startup logo screen it gets to that and disappears

this is probably now the 3rd time ive installed ubuntu on this pc, it installed perfectly on our other machines which all have similar but different specs, this is the only one im having problems with, but it also is the only one using wine/azureus/utorrent/frostwire 

ive googled and googled till im at the point of going back to windows for this machine, you guys are the last chance for this machine and ubuntu.

i have toyed with the idea of maybe trying one of the newer ubuntus like 6.10 or the new 7 one (sorry forget the numbers), but i dont know what makes them better or even if they would help or make things worse, originally i was told to only go for the long term support one

I am desperately hoping that someone out there can advise me on a solution to this, cos i really dont want to go back to xp pro, my computer is soooooo much faster now and i love ubuntu just not these dam inconvienient problems

oh and before i forget, yesterday for some unknown reason, one of my massive storage drives would not mount, had bad superblock, used fsck and fixed it and its all mounted lurvely now, just thought i would mention that case it had any relevance

my machine

amd64 3800
gigabyte s series mobo GA-M55S-S3
1Gb ram (hoping for more soon)
1 x 80Gb ide hdd (partitioned into 3, root, swap and home
2 x sata drives, 1 x 250Gb and 1 x 400Gb, both mounted /mnt/xxxx
geforce 6600 graphix card, drivers all installed and working a ok

the only other problem i can think of is that occasionally ventrillo will lock up, im running that thru cedega but thats not really of any importance, cedega lets me play my guild wars perfectly so im happy :P

keeping fingers crossed 

chey

---

### Post by freebird54 on 2007-04-15
BEing originally a hardware guy, that's where I would start my looking.  Do you have any temperature monitoring on your motherboard?  Are you sure that all fans are functioning?  Just thought to eliminate that sort of thing first -as there seem to be so many unusual glitches....

---

### Post by mad chey on 2007-04-15
all the fans (4) of them and the processor fan are all working a ok, so im not sure its an overheating issue

also the randomness of this that i can do it just after you fire her up or 10 hours later, there seems to be no continuity

my hubby is very good with hardware but crap with software and hes just scratching his head saying dunno your department love :P


its just so frustrating to have such a lovely system and to have these darn annoying problems that are gonna mean going back to the dreaded windows /sigh

ps. this is a relatively new build pc being only about a month old but its ran fine on windows, and on the initial installation of ubuntu, it just seems that at some point as im installing the software i need, that something gets upset and throws its dummy out the pram so to speak

i suppose i could dual boot and just switch over to windows at night for running utorrent but ideally i would like to solve this and leave windows where it belongs - off my pc

---

### Post by Bartender on 2007-04-15
If it were me I'd toss a Linux LiveCD in and type down to "Memory test" at the first splash screen.  Run it for a few hours.  If you see any errors, unplug the PC, set it on a bench in a room with hardwood or concrete or tile flooring.  No carpet - the goal is to minimize static electricity.  Open the PC up and pop out all the memory modules.  Find the #1 memory slot and plug in one stick.  Plug in a monitor, PS/2 keyboard & mouse, and power cord.  Run memtest again for an hour or so at least.  If no errors, pull that stick and test the next one.  Etc. etc.
If you find a bad stick and you have an old non-dual channel motherboard, you can replace that stick with a similar piece of memory.  If you have a dual-channel board, the most reliable method is to replace both sticks with a new, matched pair.
RAM is very sensitive to static electricity damage, so be careful how you handle them.  Set them down gently on a piece of cardboard or something similar, unplug the PC entirely and ground yourself by using a wrist strap or at least grabbing the PC frame with one hand, etc.

Just a day ago a LinuxLiveCD helped me diagnose RAM problems.  Was helping some friends rejuvenate an old PII running Windows 98SE.  They had 64MB of RAM.  Beefed it up past 500 MB with some old RAM I had lying around.  It seemed to work fine at our house, but when they took it home it would freeze up every time they went online.  Getting an error message from the 3Com application so I assumed the modem or modem software was bad.  

Tried memtest before buying a new modem.  Got errors.  Identified the bad stick by running memtest on one stick at a time.  Replaced that stick.  Now the PC's running fine.

Your prob may not be memory but it won't cost anything to check.

EDIT:  I'd also take a hard look at the power supply.  Is it a good name brand PSU from Antec, Fortron, Seasonic, etc.?  Lots of power supplies on the market are crap and will cause weird problems because their voltage regulation and stability is so loose.  Not sure how you check voltages from within Ubuntu, but you should be able to look in BIOS...

---

### Post by mad chey on 2007-04-15
ta for that i will do that check but there is gonna be one very earbashed supplier if their is a fault with any of it cos as i said earlier only a month tops old

the power supply is a good one and plenty of power for what im running, i am still not convinced that its hardware to be honest because ive managed to post on here several times now and im not running hardly any software atm, im starting to think something appeared to instal properly but in fact didnt and when i run it it upsets other things

---

### Post by jem7v on 2007-04-15
Firefox in Dapper randomly crashed a lot for me too.  It hasn't done so in Edgy at all, so it might be worth upgrading.  Or you could try a different browser, like Opera (which is apparently faster, according to most speed tests... it certainly is on My computer) or Seamonkey.

Running anything through Wine (especially something like a torrent program) is probably going to be buggy.  I still haven't used a program that ran flawlessly in Wine.

---

### Post by freebird54 on 2007-04-15
If the hardware is that new, then faults are less likely overall than on old stuff.  However, RAM is still a possibility - and even the seating of the RAM (or other components) can be at fault.  If you;re in it at all, just wiggle all components and connectors - its free to try!

I'm still hoping its that simple - because tracking it down otherwise is going to be, well, umm, err,....

---

### Post by mad chey on 2007-04-15
well im now one very miffed off person, does my ram have faults, er maybe we should ask does any of it work at all

ran the memory test and the whole lot was coming up red, tried the ram in a different slot on the mobo and the same so that will be going back to the supplier tomorrow, i checked the reciept it was bought on 12th march so im not impressed

does anyone know what can cause this, it was treated with the proper care and attention that it should be and has not been touched since the pc was built on the 12th march

---

### Post by mad chey on 2007-04-15
there is one thought tho

ive been struggling with these problems for about a week, but have been able to play guild wars thru cedega absolutely perfectly no lag or nothing

and if there is anything that demands my ram its that, i can remember playing GW with 512ram and its a massive difference to 1Gb

now tonight can i play GW yup, so how come i can play something that demands lots of ram but not browse the web?

im just hoping that they will replace the ram and i can get back to normality tomorrow

---

### Post by nikkkko on 2007-04-23
Hi,  

I happened to read this thread whilst looking for something else and realised your symptoms were pretty much identical to a problem I had about a year ago.  If your disk is a Maxtor brand, check that it isn't on it's way out by using their diagnostic tool, (somewhere on the web but if you can't find it post here and I'll dig it out).  There are some models that are very poor - mine one - and they replaced it for me without charge.

---

### Post by Bartender on 2007-04-23
My go-to book is "Upgrading and Repairing PC's" by Scott Mueller.  Scott stresses the importance of buying good-quality, lifetime warranty memory.  Did you save a few bucks by buying generic memory?  

Regardless of the supplier, "new" doesn't necessarily mean "works".  Have run across several cases of brand-new broken stuff.

---

