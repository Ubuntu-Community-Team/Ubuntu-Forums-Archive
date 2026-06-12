---
title: "[SOLVED] Ubuntu crashes and memory questions?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mhrpinca on 2008-01-03
Hello folks I'm new to Ubuntu and installed it because i want to learn programing, and am tired of looking at the boring XP desk top, not to mention how disappointed i am with Vista,
I'm currently running XP, Vista and Ubuntu on my machine. Vista and XP share a drive, (Vistas broken..... oh darn.) this all started out with me trying to install three operating systems on a gateway machine and ended in my building a new system. The set up i have now is Vista and XP sharing a 250 GB drive Ubuntu on an 80 GB drive and a 500 GB drive for storage.
the larger drives are SATA the 80 GB Ubuntu drive is IDE? does this matter? my processor is an Intel core two quad q6600 2.40 GHZ and I'm running 4 GB's of ram on a Gigabyte brand motherboard. oh yea and Nvidia graphics card.
This is the issue. when i look at system resources I'm consistently using only  610 MB to 710 MB of my ram and 0 of 3.1 GB of swap is this the way it is supposed to be? My version of Ubuntu is the7.10 (gutsy) release with Ubuntu studio and Compiz cube and effects (omfg u guys did good i love this OS.....Weeeeeeee) so far i like what i see and am very impressed. But!!!!!!!!!!!!? if i have Audacious open and am listening to music i see allot of load on my processor and not much of a change in the amount of ram being used swap never gets used? and i have periodic system crashes...... OK here's the set up i like one: desk top for fire starter, system monitor, network tools and system log. one desktop for music and video, one for the gimp and one for the web. all this stuff running and only 7.10 of ram used  with periodic screen freeze and system lockup requiring a reboot. is it just that Linux is ultra efficient and requires very little memory or swap? or is it broke? the crashes are they software issues or memory? is there a way to allocate resources? also I'm no good with the terminal but i found the tutorials for it so I'm willing to follow that path if need be.  
Linux  brings new meaning to Microsoft  bills poor wife having to deal with his Microsoft issue they have surgery for that now he should get that fixed...... lol  Linux looks and feels like the $#!^!..... thanks folks.

---

### Post by ByteJuggler on 2008-01-03
Your system not using much memory is the correct way.  Linux will in fact use the RAM if it needs it and can make useful use of it (e.g. for disk cache or whatever), but it won't unneccesarily swap out stuff needlessly.   This tends to result in a very snappy system as things tend to be in physical RAM all the time.   You can however make Linux more like Windows by altering the kernel's "swappiness" parameter.  For details about how to set this, see [here]("http://kerneltrap.org/node/3000")

IMO, especially with multi-gigabyte machines of today, there's very little reason to swap to disk, and a machine should really only ever start doing that if you're running an app that actually uses multiple gigabytes of RAM (which is actually pretty rare, even today, in most instances.  There are of course exceptions.)  The more RAM you have, the less inclined the kernel should IMO be to swap to disk. This generally makes for a snappy system that's not continuously hammering the disk, which is what I like. :-)

Your crashes are more worrying.  You should not be having those types of crashes, and what you describe sounds like some sort of hardware issue, possibly RAM issues.  I would suggest you run the "Memtest" option on your Linux GRUB boot menu and see what that reports.  Did you build the rig yourself?  If so, have you checked that the RAM voltage is correct?  A not uncommon problem on new rig's these days is that some motherboards default RAM voltage to 1.8V while some RAM DIMM's sometimes require more, and so what happens is the machine isn't quite stable at stock defaults, due to the RAM making errors.  In such cases the fix is usually to adjust the RAM voltage to the correct level (e.g. +0.3V if your mobo defaults to 1.8V and your RAM wants 2.1V etc.)  

Other relevant questions: What exact motherboard model have you got and what make/model of RAM?  What's your CPU voltage set at?  What's your CPU temperature like?  What PSU are you using?

---

### Post by mhrpinca on 2008-01-03
Yes this is the first computer i built i wanted to know how it all works ive been a user for years, mostly using graphics software my issue with my old machine was that gateways driver install disk only installed drivers to C: a pain when you want to run multiple operating systems if i had known what i was doing at the time i could have worked around that by installing xp to C: and left vista get its own drivers. but i wanted a faster computer anyway so i built one, as soon as i figure out how to check the ram voltage? i will do that.
 mother board: Gigabyte S series GA-P35-DS3L
ram: 4 1GB Crucial DDR2 PC6400 dual CR speed 800 MHz
Do i set the CPU speed within Linux or in BIOS like with XP? its set to whatever the board defaults to as far as the temp it was fine, ill check that again
PSU? the power supply? it was 500 watts i think the case is an ultra
like i said I've been a user for many years  so any suggestions or help is appreciated, theres a bit of a learning curve with the switch to Linux, I'm also trying to learn as much about hardware and theory  (how the box do its thing) i want to be able to render 3d faster than on my old system and work with huge multiple layer files in gimp ( cs 3 user )............ thanks

---

### Post by ByteJuggler on 2008-01-03
Re RAM, do you have stock Crucial RAM or Crucial Ballistix?  The latter actually requires 2.2V e.g. see [here]("http://www.crucial.com/uk/store/partspecs.aspx?imodule=BL2KIT12864AA804&cat=RAM"), however if you have "normal" memory that may not be the case.  Also, having 4x 1GB sticks places more demands on the memory controller/subsystems and DIMM's which sometimes neccecitates slightly higher voltage than stock. But for now, we need to determine what your RAM's official required voltage is and ensure your motherboard is set the same.  (Sometimes the voltage is on a sticker on the RAM sticks, is it on yours?)  You set the voltage in the BIOS somewhere.  Given your motherboard model I'd bet the motherboard is defaulting to 1.8V for the RAM, so I'd wager your stability problems is, one way or another due to your RAM not having quite enough voltage.

---

### Post by mhrpinca on 2008-01-04
nope i looked up my stics on the crucial web site 1.8v is the voltage  for the memory sticks will it hurt it if i overclock it?

---

### Post by ByteJuggler on 2008-01-04
> **mhrpinca said:**
> nope i looked up my stics on the crucial web site 1.8v is the voltage  for the memory sticks will it hurt it if i overclock it?

To answer your question, it should be OK to overvolt it slightly, up to about 2.1V (although that's not called overclocking - overclocking is when you run the RAM faster than its rated speed, e.g. say 900Mhz for 800Mhz RAM. You really don't want to even think of that until you've established a stable reliable baseline and proven all the hardware is fundamentally working/sound.)   

So the way I see it you have 2 options, the long road and the short road.  

The Long road:
You need to try and firstly confirm whether your RAM is in fact OK or whether (perhaps) you've got one (or more) dodgy sticks of RAM.  Given that you have 4 sticks of RAM its possible that in itself is causing more stress on the memory subsystem, which may be the cause of you instability.  So to for the time being eliminate that to allow you to test your RAM in relative isolation, I'd suggest removing all but one of the sticks of RAM in turn, and booting with it only, and then seeing if that impoves observed stability.  Also run Memtest on each stick for as long as you can (I'd suggest an hour on each stick at least) and confirm they pass at stock.  If they don't then raise the voltage on the stick by up to 0.3V (so up to 2.1V) and see if matters improve.  But really, if the RAM is rated at 1.8V and it's not stable at 1.8V in isolation I'd be suspicious of the RAM DIMM.  If all the RAM passes in isolation (ideally at stock 1.8V) then the likelihood is that you running 4 sticks is the cause of the problem and a slight raise in voltage when running 4 will cure the problems.  So again test with all 4 and raise by 0.1V (up to  2.1V) and see if the stability improves.  

The Short road:
Make the assumption/guess that the cause is that you're running 4 sticks of RAM, and so that you possibly need slightly more voltage to attain stability at stock timings.  So just try upping the RAM voltageby +0.1V (e.g. 1.9V) first and test that to see if stable.  If not, then +0.2V (e.g. 2.0V) and test again etc.  If this course of action fails then our original premise/assumption might be false and you'd really have to test each stick in isolation to try and establish if in fact you may have a dodgy DIMM.

---

### Post by mhrpinca on 2008-01-05
i took the short road and so far no crash we will see if this does the trick......thanks 
we just had the worst storm ive seen in ten years roll through california so sorry for not responding sooner the power was out....
im still amazed at how efeciant this OS is and how slick it looks. i cant wait to get flash player working....... im diving into python and java. i used a lot of action script with flash and swish what i like is all the suport and all the tools and tutorials on how to program its to hard to get things rolling in windows its like they dont want you to do any thing but use there crap............ so far so good it seems to run fine still not using a lot of resources but ive opend a ton of stuff and no crash cooool thanks again

---

### Post by ByteJuggler on 2008-01-06
Hey if you're diving into Python, then you might find the following interesting:

1.) Python Challenge:
[http://www.pythonchallenge.com/](http://www.pythonchallenge.com/)

I'm up to level 7 now. :-)  I've also got several other python links if you're interested.

2.) Python IDE's:
At least you probably want to install "IDLE", the "default" python IDE.  This can be done via Synaptic (its in the repositories.)  There's also the following IDE I'm looking into wich looks pretty nice (SPE):
[http://pythonide.blogspot.com/2007/10/spe-084b-works-fine-in-ubuntu-gutsy.html](http://pythonide.blogspot.com/2007/10/spe-084b-works-fine-in-ubuntu-gutsy.html)
A slightly outdated one is in the repositories, but I've installed the latest using Subversion, which works fine.  Was a bit of fiddling but not too hard.  If you need a hand let me know.

---

### Post by mhrpinca on 2008-01-08
Problem solved. I was trying to do it all in the idle editor and had not opened a new window and saved the file, so now I'm doing all my editing in the saved file window and hitting run and module and it prints it out in the python shell window, Ok i get it now so i can build, save, and test, and edit what ever i want, cool. the tutorial i was using didn't explain that very clearly. heres the link to the tutorial i found that's more for the beginner. [http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python)
                                                                         thanks

---

