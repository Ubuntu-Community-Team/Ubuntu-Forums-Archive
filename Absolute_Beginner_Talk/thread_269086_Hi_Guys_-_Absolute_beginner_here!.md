---
title: "Hi Guys - Absolute beginner here!"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by staib on 2006-10-01
At 50+ I feel like an old dog about to learn some new tricks :cool: but I am being frustrated by one of my PC's ](*,)  

Although I can run the Live (6.06.1) CD on one PC quite happily (which suggests the d/l and burn went fine), it just refuses to be read properly by the other PC, which I was quite happy to completely switch over to Ubuntu...

The "other" PC (Athlon 1Mg) starts to boot from the CD, loads the Ubuntu "Index" page with the various install options, but then stalls for ages at the "mounting root file" second line :evil: 

And then loops back to a black screen with the message "Uncompressing Linux... Ok, booting the kernel" - but then nothing happens...

Suggestions appreciated - even of the go and read _this_ variety! 

Cheers,

Nick

---

### Post by bigken on 2006-10-01
have you tried safe mode ?
also you could try the alternate cd ;)

---

### Post by xpod on 2006-10-01
Not sure about the looping back bit but the usual options with tempromental live cd\sys is to first try "safe graphics" at boot which seems to use less resources and was how i finally got it to install on this pc(it was loading ok for me but freezing during install)..

Next option is usually the alternate install cd which is text based and uses even less resources and is the way a lot of us have to resort to getting the thing on our pc`s to start with...

The loop back thing seems weird though as most usually just freeze at some point if their having trouble.....Not something im sure about....Neither is much else mind you as i too am an old-er dog learning new tricks...Ps`c full stop are all new to me but ubunto made it more fun:mrgreen: 

Good luck

---

### Post by staib on 2006-10-01
Yes - safe mode makes no difference.  I guess I thought the graphical installation would be "easier" (for a beginner). I have removed all USB devices, as I read somwhere else this could be an issue.

If I go down the alternate route, is there an easy step by step guide that people might recommend?

Cheers

---

### Post by bigken on 2006-10-01
yes just follow the prompts

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by wpshooter on 2006-10-01
Have you tried cleaning the CD drive on that machine.

P.S. - Also have you checked to make sure the CD Drive's firmware is the latest and greatest ???

If there is not anything on the machine that you need to keep then get the KILLDISK program from this site and WIPE the hard drive clean and then try the install again.  If that does not work I would suggest you try the ALTERNATE CD version.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck, from another old-timer.

---

### Post by staib on 2006-10-01
:D  - OK - I'll try the alternate - but I may be back...

Thanks for the interest and input...

---

### Post by xpod on 2006-10-01
If you just intend on giving ubunto the whole machine its really straightforward.......
It should load regardless of what or what is`nt on the hd i think but everybody is different i suppose so it`s just a case of persisting till you find the right way or indeed the right cd.
I had to go through 3 cd`s before i eventually got Kubunto alternate to go on our other old banger

---

### Post by bigken on 2006-10-01
another small tip brun the iso's at a slower speed

---

### Post by staib on 2006-10-01
OK - thanks bigken - I did force the burn to a slower (4X) rate, just in case this was the issue, but the disc works fine (in Live mode) on my main PC, so I think the CD itself is OK.

I'll try cleaning the other CD drive in case it's a physical thing - but it always stops at exactly the same point...  Just tried again in safe mode but it just stops dead - and after maybe 10 minutes everything freezes at "Uncompressing Linux... Ok, booting the kernel" - even though earlier it whizzes through that bit.

I'll try the alternate and report back...

---

### Post by SirShaggy on 2006-10-01
Just a thought here, I tried to use the live CD on my old laptop. P3 with 192MB or RAM. It did the same as you just explained and I never was able to get it to work. I was told to download the alternate install cd to use instead. May be worth a shot if nothing else works.
SirShaggy

---

### Post by staib on 2006-10-01
OK - I d/l the alternate CD as many suggested, but the "manual" installer is having a problem detecting and mounting the CD-ROM. I have a Rewritable (MSI) CD, and a newer RW DVD. The installer is suggesting I might want to load a specific module ("if I have an unusual CD-ROM") and gives a drop down list of None, Aztcd, cdrom, cdu31a etc.

What should I do here - is it just none as there is no CD ROM - and it will then move on to look for CD-RW?

Appreciate any guidance here!   Cheers.

---

### Post by wpshooter on 2006-10-01
Did you check the integrity of the CD by running the verification function on the initial Ubuntu boot screen menu ?

---

### Post by staib on 2006-10-01
Yes - thanks, wpshooter - when I try (and I just tried again), it just goes straight into the "Detecting hardware to find cd-rom drives" routine - but never finds the actual drive...

---

### Post by staib on 2006-10-01
I didn't expect this to be easy - but I thought the hard bit would be getting to understand how the OS works, not just installing it ](*,) 

To re-cap, I have a CD with 6.06.1 which works fine on one PC (at least in live mode) but on my target PC just can't get past the Mounting Root file System stage.

Based on good advice here, I have created a new CD with the **alternate** 6.06.1 version - but this one cannot see the CD-ROM drive - at least it fails to mount it.

My wife is now saying what ARE you doing in there all afternoon...

Time for a cup of tea methinks!

---

### Post by podunk on 2006-10-01
By this point I think I would start to wonder if maybe there was something wrong with my CD ROM drive.

You say you have a DVD drive on  that machine – does your BIOS give you an option to change which CD drive boots first? If not – are you comfy with changing jumpers on the back to switch their order?

---

### Post by bigken on 2006-10-01
just try the other drive :rolleyes:

---

### Post by staib on 2006-10-01
Thanks for that suggestion - yes, just changed the master/slave relationship and waiting to see what happens - trying to detect hardware right now..."please wait"...but it's taking ages again...

[-X  - "No common CD-ROM drive was detected" :-|

---

### Post by wpshooter on 2006-10-01
Are you confident that your CD drive does not need cleaning or did you try that.  Also are you confident that your CD drive has the latest firmware ?

Did you try running KILLDISK to WIPE your hard drive before starting the installation attempt ?

Other that that, I know from my experience that MSI is sometimes a bit different, do you have any old just plain CD-drive or a CD-RW drive laying around that you could hookup (even temporiarily - just take side off and see if you can get the wires to reach by setting the drive on a box or something).

How are your hard drives and the CD jumpered and what interfaces are they on ?

---

### Post by bigken on 2006-10-01
do the drives show in the bios ?

---

### Post by staib on 2006-10-01
Both drives show up OK in Bios (Amibios 1.24a) as CD-ROMS...

There are 2 hard-drives (Primary Master and Primary Slave) and the two CD-ROMS are set up as Secondary Master and Slave.

Both CD-ROMS are brand new this year, and worked fine in Windows, so I really don't think they are faulty or dirty...

I tried replacing one with an older CD-ROM drive and also switched the master/slave thing, but it doesn't seem to help.

Sorry - I didn't yet run KillDisk as this sounded rather drastic - at least, at the moment, I have a working PC... 

Please convince me I need to kill Windows completely, so that Ubuntu can rise phoenix like :rolleyes:

---

### Post by bigken on 2006-10-01
its not the hdd its the bloody cds I think why wipe your hdd ?



god I need beer 8)

---

### Post by staib on 2006-10-01
That was more or less my thought - hence the hard-drive has not been wiped - I also suspect it may be a Bios setting but I can't see anything too obvious there...

Sorry Ken, we're out of beers tonight, so here's a little music, played specially for all those who've tried to help me today :-({|=

---

### Post by bigken on 2006-10-01
do you have any differnt media types (cdr's) its worth a try :-k

---

### Post by SirShaggy on 2006-10-01
Please have patience here, the P3 1.0GHz I mentioned earlier took over 2 hours to get to the desktop on. Once there, it installed fine and worked ever since. Yes, that was with the alternate install. Sometimes, some machines need all you can give them.
Do as suggested, check the BIOS, clean the CD/DVD drives insert the CD and start a pot of coffee (maybe a Keg of Beer?!?) I would at least give this a try. I have now had two systems that were super slow to install on, I was told to be very patient and ended up doing so. End result was an old unusable system revived with Ubuntu.
SirShaggy

---

### Post by podunk on 2006-10-01
Will a Windows set up CD run?

I'm a Linux beginner to, and there may be a chance that there is something about your machine that Ubuntu doesn't like.

However! :-) I've installed Ubuntu on several older machines here at the house with no trouble at all. While I'm new to Linux I'm not new to computers, and it sounds like a hardware flaky going on. Either something in the BIOS, a lose or bad stick of RAM, something like that. 

Did you try setting the Plug and Play PCI part of the  BIOS to 
PNP OS=NO

This sounds like one of the early AMD Althons? Thunderbird? What kind of computer is it exactly? How much RAM? Onboard video or a card?

If your computer will load a windows set up disk and not Ubuntu maybe you should try a different version of Linux and see what happens? 

If it fails to load a Windows set up disk then I would definitely suspect a bad memory chip.

---

### Post by staib on 2006-10-02
Am at work sneaking a quick peek at the forum :D 

Thanks podunk - some nice suggestions that I will try when I get home. Yes, it is a T'bird Athlon 1Meg cpu, the gfx card is a GeForce Ti4200. The PC is not starved for ram as I used to used to use it for flight sims 8) - probably 512meg

I'll check if a Windows boot disk gets read later this evening...

Cheers.

---

### Post by abijah on 2006-10-02
I also had this problem on an old Dell machine.

My solution was to switch CD drives.  

It was also driving me a bit insame, b/c the drive loaded a windoz setup disk without any problems.  It was a buffer problem with the drive.  Maybe a driver hiccup.

If you're using boxes and not a laptop, i would try swapping to the drive that did work(or some other).

---

### Post by NordicRX8 on 2006-10-02
Just my $0.02.

In the past few months. I have tried several different Linux distros (Debian, Fedora Core 5, OpenSUSE, PuppyLinux, Ubuntu, Kunbuntu, Xubuntu)  All of them installed without a problem EXCEPT the "ubuntu" based distros.  They all had the same error installing from the live CD (same error as yours: "mounting root file").  The optical drive I was using was an MSI 48/32/48 CDRW, I switched to an older 24x CDROM, no difference.  I gave in and bought a new Lite-On 16x DVD-RW/DL drive.  Tried all of the unbuntu distros and guess what???  They all installed without issue.  New optical drives are fairly inexpensive these days... pick up a new optical drive and see what happens!

Good Luck.

---

### Post by staib on 2006-10-02
Interesting comments guys...

I tried the Windows boot disk - no problem.  Then I fished out an old Knoppix Live CD I had burned some months back - dropped that into the LG DVD-RW unit and it just loaded up with no hesitation. In fact I'm writing this via Konqueror...  what is frustrating is that something, somwhere, is clearly a problem for Ubuntu, but not for other flavours of Linux or for Windows.  Wish I knew what it is! :-?

---

### Post by staib on 2006-10-02
...and I just tried it with a Linux Puppy (Live) CD.  That worked like a peach :-D  - so what is it with Ubuntu :-k - is it just "fussier", is it an Ubuntu specific Bios setting?  Inquiring minds want to know!

---

### Post by podunk on 2006-10-02
Whenever I get a set up floppies or CD I copy it to a hard drive. I've got MS dOs 5 and 6, Windows 3.0, 3.1 95 98 and Xp and I always run setup from them (it's tons faster.)

I bet there is a way to download Ubuntu to a hard drive and set it up from there.....

---

