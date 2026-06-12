---
title: "my ubuntu-studio studio"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-06-30
I have to upgrade , but can do minimal stuff only 


i have problems with recording realtime in audacity, one track after each other ,

so i need some power, but can't afford duo 2 core at the moment,

so since the company put in a celeron chip , they could have put in a p4, FSB  533 Mhz with L2 cache size of 512 kb cause my board 845GEBV2 supports it and i need power 
there are two pci slots for ram , so i can put up to 2 g ram but that was never tested on these boards according to intel , so i don't know wether i should try it   

this the link to an explanation about building a entry - DAW , i have a similar motherboard and i have 2 * 512 G ram, so it gives me some hope to do what i want still
[http://www.extremetech.com/article2/0,1697,1151427,00.asp](http://www.extremetech.com/article2/0,1697,1151427,00.asp)

will this let me record "sound on sound" up to 4 tracks , so i can mix them down using audacity
also installed the realtime kernel 


i have a problem with ardour    "Ardour could not connect to jack" , even if i start jack first
need help here !

just want some feedback from people recording audio with any linux os  /ubuntu-studio


i'm trying to set-up an affordable linux music homerecording studio :)

---

### Post by angryfirelord on 2007-07-30
Jack fix: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/#more-57]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/#more-57")

---

### Post by Drunky on 2007-07-31
That article is from 2003 and a lot of changes have happened since then.

I'm converting my garage into a music room and have been specifically researching UbuntuStudio and Linux music in general.  After the garage is complete I'm buy a dedicated box and probably going with UbuntuStudio.

I'm looking at getting a P4, approximately 2.8 ghz machine.  Baseline with 512m memory but preferrably 1gig.  Two harddrives (both 7200 rpm, ultra 100 - would prefer SATA but I don't think the machine will handle it); one for OS and only 80gigs, the other 320gigs for data.

The video card will probably be a moderate nVidia card but the audio card will probably be a M-Audio, perhaps the Delta 1010LT or Delta 66.  I've read that ALSA drivers work more frequently that OSS but I haven't really experienced that obviously.

I'm hoping to find the computer with memory for about $250.  The video card around $100.  Audio card $200 and I've already bought the drives for under $150.

After the room is done and the computer is in place I will worry about buying a small mixer (a must if for nothing else than recording drums) and decent studio monitors.

The really sad thing, and I hope someone can correct me, is that I haven't really been able to find any current information practically about UbuntuStudio (like minimum requirements) or Linux music.

Most articles for Linux music are old, really old.  The most current one I found was [this one.]("http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm").  And the ones for UbuntuStudio just talk about it...not using it.

When I get the garage finished I am going to document setting up my machine and UbuntuStudio and how I recorded music.  I'll probably post it somewhere, either here or a wiki or my website.  One caveat:  I don't use synths right now, it's all my band with live people.



[edit] The duo core thingie...I've read here on these boards that right now UbuntuStudio (using Jack) doesn't use the other core to process music...Jackdmp does allow to use both cores but this isn't implemented (or stable, I guess) in the current UbuntuStudio.  Hopefully someone else can verify or clarify this.

Also, for recording music I don't really think you need that much processing power.  The audio card does most of the crunching (converting analog to digital), for the most part I believe the computer only has to keep up writing the information to the computer and read/send sound via full duplex out the card also.  When you start added software effects and mastering will probably be where you will really need the processing power.  Again, I don't know this for a fact and would appreciated someone with real experience giving us their advice.

---

### Post by medley on 2007-07-31
> **Drunky said:**
> That article is from 2003 and a lot of changes have happened since then.

I'm converting my garage into a music room and have been specifically researching UbuntuStudio and Linux music in general.  After the garage is complete I'm buy a dedicated box and probably going with UbuntuStudio.

I'm looking at getting a P4, approximately 2.8 ghz machine.  Baseline with 512m memory but preferrably 1gig.  Two harddrives (both 7200 rpm, ultra 100 - would prefer SATA but I don't think the machine will handle it); one for OS and only 80gigs, the other 320gigs for data.

The video card will probably be a moderate nVidia card but the audio card will probably be a M-Audio, perhaps the Delta 1010LT or Delta 66.  I've read that ALSA drivers work more frequently that OSS but I haven't really experienced that obviously.

I'm hoping to find the computer with memory for about $250.  The video card around $100.  Audio card $200 and I've already bought the drives for under $150.

After the room is done and the computer is in place I will worry about buying a small mixer (a must if for nothing else than recording drums) and decent studio monitors.

The really sad thing, and I hope someone can correct me, is that I haven't really been able to find any current information practically about UbuntuStudio (like minimum requirements) or Linux music.

Most articles for Linux music are old, really old.  The most current one I found was [this one.]("http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm").  And the ones for UbuntuStudio just talk about it...not using it.

When I get the garage finished I am going to document setting up my machine and UbuntuStudio and how I recorded music.  I'll probably post it somewhere, either here or a wiki or my website.  One caveat:  I don't use synths right now, it's all my band with live people.



[edit] The duo core thingie...I've read here on these boards that right now UbuntuStudio (using Jack) doesn't use the other core to process music...Jackdmp does allow to use both cores but this isn't implemented (or stable, I guess) in the current UbuntuStudio.  Hopefully someone else can verify or clarify this.

Also, for recording music I don't really think you need that much processing power.  The audio card does most of the crunching (converting analog to digital), for the most part I believe the computer only has to keep up writing the information to the computer and read/send sound via full duplex out the card also.  When you start added software effects and mastering will probably be where you will really need the processing power.  Again, I don't know this for a fact and would appreciated someone with real experience giving us their advice.

Hi there.

I've set up a DAW in my basement using Kubuntu and Ardour 2.0. It works quite well, although I haven't tried recording multiple tracks at once. I'm not using a realtime kernel, which Ubuntu-studio has, but it hasn't been a problem so far. I am only using a SB live for audio, which is also less than ideal, but serves the purpose at the moment. I'm recording at 44.1khz, 16 bit (CD quality). My system is an AMD 2800+ with a gig of ram. I have an 8 channel mixer, a Presonus compressor, Presonus tube pre and an Alexis nanosynth. I use an M-Audio 61ES for the midi keyboard. I haven't yet isolated my PC from the mic, so that needs to be addressed yet. I'm just fooling around at the moment but the performance of my system seems to be adequate.

I haven't tried multitracking yet, but don't expect any problems. I must say that now that I am familiar with Jack, I like it, and it makes sense. I use Hydrogen for a drum sequencer and because it is patched through Jack to Ardour, it's very convenient.

Once I get serious, I'll probably install Ubuntu Studio and isolate the PC. But for capturing analogue stuff, it works perfectly well as is. I even run Beryl at the same time.

I hope this encourages you. You don't need a dual core in my view. 2ghz and up should be sufficient I would think, unless you want to track a whole bunch of stuff at the same time.

Good luck.

---

### Post by firedancer on 2007-08-01
i've recorded a nice song (it can always be better) yesterday  , with ardour and jack 

i was happy , but i still need the P4 and definitely a hdd with higher rpm , right now i've only one 

and how fast it send /receives info i do not know

yeah if you get to know jack , you'll like it

it would be wonderful if ubuntu / linux studio folks can learn from each others experience
someone actually started a thread hopefully  it will become a long one with lots of info 



tommorow i'll mixdown the song and next week try to master it. 
someone said they do mastering  in audacity 

i wonder what the best appraoch is (in linux) about this 

:guitar::guitar::guitar:

---

### Post by Drunky on 2007-08-01
You might try Jammin' also for mastering.

---

### Post by Sonicgoo on 2007-08-04
so what are the minimum requirements for Ubuntu Studio?

---

