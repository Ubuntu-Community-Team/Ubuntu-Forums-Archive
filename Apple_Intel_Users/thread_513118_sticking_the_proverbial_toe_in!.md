---
title: "sticking the proverbial toe in!"
date: 2007-07-30
forum: Apple Intel Users
---

### Post by niteblind on 2007-07-30
Mornin' all.

I am looking for some advice (surprising that really), I am extremely tempted by a Macbook 13" laptop and thought I would have a quick look through the forum here to see whats going on with it so I have a couple of questions.

1. I doubt I will be running Mac OS at all so is it as straight forward as formatting the drive and installing ubuntu onto it or is there something else that I will need to do?

2. I notice the post about compiling a kernal... never had to do this on my current laptop so is it completely necessary/ if not what are the advantages of it?

3. The macbook comes with 802.11n and bluetooth built in how does this work on ubuntu (dapper/feisty) and do you get fully speeds etc for them?

Cheers in advance
niteblind

---

### Post by cyberdork33 on 2007-07-30
> **niteblind said:**
>  1. I doubt I will be running Mac OS at all so is it as straight forward as formatting the drive and installing ubuntu onto it or is there something else that I will need to do?

Pretty much, although you may not want to wipe the entire drive, and want to keep a small OSX partition for firmware updates.

> 2. I notice the post about compiling a kernal... never had to do this on my current laptop so is it completely necessary/ if not what are the advantages of it?

Not necessary, the precompiled kernels installed by default are fine. Compiling your own can help you reduce the size of your kernel, activate / deactivate features of the kernel, add patches / modifications to the code that are not included in the default kernels, etc.

> 3. The Macbook comes with 802.11n and bluetooth built in how does this work on ubuntu (dapper/feisty) and do you get fully speeds etc for them?

Don't have a whole lot of experience on this one as I am not currently using these (nor do I have a Macbook). WiFi will work with some help, and I am unsure if you can achieve n connections yet. Bluetooth works fine, but is not as easy to configure as in OSX (IMO). I have used it before (keyboard/mouse), but I cannot attest to the speed as I have not benchmarked it.

---

### Post by niteblind on 2007-07-30
thanks for the reply.

What sort of firmware would be necessary? surely BIOS updates etc would not need a partition so I am a little confused there. Also i notice a few mentions about a thing call Parallels what is this some sort of emulator???

Finally for those of you out there using OS X how easy is it to install linux apps to this or is it not possible?

cheers

---

### Post by benanzo on 2007-07-30
Unfortunately it seems that Apple uses the blank 200MB EFI partition at the front of the disk to install firmware updates (in some cases.)

See [this]("http://ubuntuforums.org/showthread.php?t=509525") post.  I do not have OS X installed on my first-gen MacBook and have had no problems.  You can't install firmware updates except through OS X though, so keep that in mind.

Parallels is a virtual machine environment for OS X.  You can install Ubuntu or Windows etc. in it and run them simultaneously with OS X.  I have absolutely no need for OS X or Windows, so I don't use it.  I always install Ubuntu directly on the hardware.

---

### Post by ronocdh on 2007-07-30
> **niteblind said:**
> Finally for those of you out there using OS X how easy is it to install linux apps to this or is it not possible?

cheers
I completely agree with Benanzo's responses. Don't expect any method of installing OS X apps in Linux; there was recently [talk on Slashdot]("http://rss.slashdot.org/~r/Slashdot/slashdot/~3/138847012/article.pl") about such a monster, and I don't believe the discussion was particularly fruitful. Perhaps you're already familiar with it, but [Fink]("http://www.finkproject.org/") would let you run Unix apps in OS X.

---

### Post by niteblind on 2007-07-30
okay guys thanks for that one last thing that I am curious about....

Mac books are running the Intel on board shared memory graphics chipset, how does this fly with ubuntu when it comes to things like cloning the desktop/extending the desktop onto a second display (I am thinking mainly of Svideo out to a TV)?

I had a couple of stabs on Dapper with Kubuntu and once cloned the laptop monitor would not come on anymore only the TV!

Any ideas anyone?
niteblind

---

### Post by benanzo on 2007-07-31
I have no specific experience with the GMA950 chips on the MacBooks, but I used to clone/extend my screen onto an external moniter with an integrated Mobility Radeon 7500 on a Dell Inspiron 5100 (which I think is much less capable than the Intel chips) and never had a problem with performance.

---

### Post by niteblind on 2007-07-31
the intel graphics chipset does not have the best support on ubuntu as opposed to ATI who make linux specific graphics drivers.

Ok onto the next few thoughts I have had...

1. i suooise I am asking a dtupid question when i say does the included remote control work onn ubuntu?
2. Does the inbuilt isight cam work at all?
3. What sort of battery lige are ppl actually getting with this laptop?

thanks once again in advance :)

niteblind

---

### Post by cyberdork33 on 2007-07-31
There is a section of the Macbook wiki about extended desktop
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

> **niteblind said:**
> the intel graphics chipset does not have the best support on ubuntu as opposed to ATI who make linux specific graphics drivers.

Ok onto the next few thoughts I have had...

1. i suooise I am asking a dtupid question when i say does the included remote control work onn ubuntu?
2. Does the inbuilt isight cam work at all?
3. What sort of battery lige are ppl actually getting with this laptop?

Wow you have it backwards, Intel has better drivers than ATI (of course ATI drivers suck on all OSs)

to answer the other questions.
Remote can work - [http://ubuntuforums.org/showthread.php?t=502924&highlight=remote](http://ubuntuforums.org/showthread.php?t=502924&highlight=remote)
iSight will work - [http://ubuntuforums.org/showthread.php?t=491381](http://ubuntuforums.org/showthread.php?t=491381)
Can't help with battery life as I am not on a portable.

---

### Post by ronocdh on 2007-07-31
> **niteblind said:**
> the intel graphics chipset does not have the best support on ubuntu as opposed to ATI who make linux specific graphics drivers.
As cyberdork33 noted, this is way off-base. Perhaps you could try installing the **915resolution** package, available in Synaptic, to help with the Intel graphics chipset.

---

### Post by benanzo on 2007-07-31
> the intel graphics chipset does not have the best support on ubuntu as opposed to ATI who make linux specific graphics drivers.

I don't want to belabor the point, but this is absolutely false.  ATI's graphics drivers are world-renowned for being miserable.  Intel drivers are fantastic (because they're Free.)  It is a sad state when an integrated Intel X3100 chip can outperform ATI's dedicated graphics cards based purely on the quality of the drivers.

---

### Post by ronocdh on 2007-07-31
> **benanzo said:**
> I don't want to belabor the point, but this is absolutely false.  ATI's graphics drivers are world-renowned for being miserable.  Intel drivers are fantastic (because they're Free.)  It is a sad state when an integrated Intel X3100 chip can outperform ATI's dedicated graphics cards based purely on the quality of the drivers.
I myself didn't realize the actual performance of the fglrx driver was abysmal; I just assumed it was the binary blob nature of it and overall deplorable (or nonexistent) support for it to be the causes for its being decried. As I'm not familiar with 3D benchmarking procedures in Linux, could you give me some commands to run or something? IIRC, "fglrxgears" isn't a very good measure, but I don't fully understand why.

Sorry to drag this post so far OT....

---

### Post by russo.mic on 2007-07-31
First off, I agree with cyberdork and ronocdh.  Off base.

Just wanted to add that I have no trouble with my blue-tooth in ubuntu.  I use my phone and my bluetooth mouse all the time.  It required about 20 min. of config the first time, and my mouse connects great every time I turn it on.

Russo

---

### Post by niteblind on 2007-08-01
sorry to have touched a nerve with some people, I was just posting from experience. The intel chipset on my current laptop (admitted 2yrs old now) had not had anything in the way of the ability to set up multiple displays etc. When i searched these forums there were a lot of people complaining that this had been done for Nvidia and ATI but not the onboard Intel chipsets.

Anyhow this is great news that you all feel so strongly about the Intel chipset... bodes well for me!!!!

Now hopefully this should be the last thing I need to ask about.... Calling anyone with the Macbook to answer this. On my current laptop I am suffering from a problem with the battery not lasting half as long as it is supposed to. The battery is regularly drained and then fully recharged so I do not feel the battery should be the cause of this and feel this MAY be an issue with powermanagement.

I would appreciate knowing if anyone has had this issue with the Macbook at all I notice a few people in the Abs-beginners forums complaining of this but none appear to be using Macs.

Would appreciate knowming as i think that I am pretty set on one of these now :P

niteblind

---

### Post by cyberdork33 on 2007-08-01
> **niteblind said:**
> sorry to have touched a nerve with some people, I was just posting from experience. The intel chipset on my current laptop (admitted 2yrs old now) had not had anything in the way of the ability to set up multiple displays etc. When i searched these forums there were a lot of people complaining that this had been done for Nvidia and ATI but not the onboard Intel chipsets.

Anyhow this is great news that you all feel so strongly about the Intel chipset... bodes well for me!!!!

Sorry, I did not mean to set off a chain, but it is just that Intel has open drivers, ATI/NVidia do not. This means that Intel graphics are supported much greater and easier under linux. I will admit though, that (most) NVidia cards work MUCH better than ATI.

I cannot comment directly on the battery issue, but it would likely be that you have better power management under OSX than Ubuntu simply because OSX is designed specifically for your hardware, whereas Ubuntu is made to work on a very wide variety of hardware. You should get decent performance though as linux has done much better in that department in the last few years.

---

### Post by niteblind on 2007-11-20
Hi again,

still thinking of taking the plubge but as there are no mac stockist in my area this is becoming a little tricky. I would like people's honest opinion on hte quality and appearance of the mac book screen. In my head I know 64mb of shared graphics should be enough but is it really???

I would appreciate honest answers to this one as I am legally blind so the qualit of the screen is a REALLY big deal for me

cheers in advance
niteblind

---

### Post by cyberdork33 on 2007-11-20
> **niteblind said:**
> Hi again,

still thinking of taking the plubge but as there are no mac stockist in my area this is becoming a little tricky. I would like people's honest opinion on hte quality and appearance of the mac book screen. In my head I know 64mb of shared graphics should be enough but is it really???

I would appreciate honest answers to this one as I am legally blind so the qualit of the screen is a REALLY big deal for me

cheers in advance
niteblind

Well, the Macbook hardware has been updated since you last posted... There are still some issues getting everything to work nicely together.

It now has Intel GMA X3100 graphics processor with 144MB of DDR2 SDRAM shared with main memory.

Apple has some of the best displays in the industry.

---

### Post by Threeethan on 2007-11-20
I just bought one of the newly-updated MacBooks and, in general, I'm quite happy with it.  To some of your questions:

1) The battery performance seems OK so far; I spent the day in Linux yesterday, and I think I probably got 3-4 hours of uptime on one charge, probably a bit less than OS X.  There have been some grumblings about the lack of a "tickless" kernel in the 64-bit version, but I think battery performance is reasonable.

2) The display is nice.  I would have probably chosen a matte display if that were an option, (it's only an option for the "Pro" line) but I'm quite happy with the glossy display.  I've seen some glossy screens from Dell and others that greatly reduce the viewing angle, but this display is actually much nicer.  Probably one of the best reasons to go Mac

Unsolicited advice, here, but, if you're only going to run Ubuntu, I might recommend steering clear of the Mac hardware.  So far, I've spent a few hours ironing out compatibility issues, and I have a few hours left in front of me.  I would seriously consider the Dell with Ubuntu pre-installed if you're not going to be using Os X at all -- they might be slightly more expensive, but they are available with a higher-resolution display.  A Thinkpad would probably be easier as well.  But the apple hardware is sexy, and the MacBook is actually a pretty good deal these days.

---

