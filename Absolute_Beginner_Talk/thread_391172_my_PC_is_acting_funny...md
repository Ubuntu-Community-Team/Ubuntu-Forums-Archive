---
title: "my PC is acting funny.."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by billdotson on 2007-03-22
I got my replacement motherboard and PSU 2 days ago and put my PC back together.  Everything seems to be working fine in Windows but absolutely horrible in Ubuntu.  

My PC specs are:
Intel Core 2 Duo E6600
2GB Corsair XMS2 PC6400C4 DDR2 800MHz RAM
nVidia 7800GT PCI Express x16
Soundblaster Audigy 4
Asus P5B Deluxe/Wi-fi AP motherboard

In my BIOS my CPU cores are switched so that the second core has the 4096KB of cache and the first one only has 32KB making the second core the dominant core.. weird.  I booted into Ubuntu and guess what? Now my internet isn't working.  I tried booting from the LiveCD and the same thing happened.  The weird thing is that my ethernet device on my install is now listed as eth1 on my install where it used to be eth0, but on the LiveCD it is eth0.

Also, my sound isn't working anymore (I disable the onboard sound because my soundcard has been doing all the sound).  

So I didn't have the internet so I decided I would just do some video editing w/ Avidemux.  I opened up Avidemux and did some video work and then encoded the files.  I shut down avidemux after it was done and dangit if Ubuntu got slower than mud.  I looked and ALL of my RAM AND SWAP was being used.  I looked in the system monitor and Avidemux isn't even open and there weren't any processes eating the memory.

Then today (I turned the PC off last night) I did some more video work with Avidemux.  Then I encoded a file and opened the system monitor while Avidemux was running.  I noticed that since for some reason the 2nd CPU core is the dominant one the corse was @ 100%.. which seems acceptable since it is encoding video.  But my RAM usage was 215-225MB out of 2GB and there was 20MB of my swap being used.  I know those numbers aren't high but why is the swap being used if I still have so much physical memory available??  I never noticed ANY swap being used before I rebuilt my PC.  So then after Avidemux was done I shut it down and guess what this time?! Both CPU cores were running @ 65-75% each with no processes taking up any such resources.  I just restarted Gnome and that fixed it.  Why have so many things started happening in Ubuntu after I put my new MB and PSU in.. I never noticed such annoying/screwed up things before I replaced the MB.  Maybe the BIOS is corrupted or something? 

The odd thing though is that everything seems to be working fine in Windows.. sound, CPU and RAM usage, internet, everything.

BTW, the only thing that is odd that doesn't seem to have anything to do w/ an OS is the fact that my CPU cores are switched to what they used to be in terms of cache and the primary cores.  Why is the BIOS doing this?  Also, according to Ubuntu it seems my ethernet devices are switched too..

What in the world is going on?

Should my BIOS be upgraded or restored or something?

---

### Post by macogw on 2007-03-22
As far as mem usage, can you do
free -m
when it's slow and give the output?

---

### Post by H.E. Pennypacker on 2007-03-22
Though this is not the support forum, the following may help:

A thread that may indicate there is something wrong with your motherboard and Internet connectivity:

[http://www.ubuntuforums.org/showthread.php?t=253249&highlight=Asus+P5B+Deluxe](http://www.ubuntuforums.org/showthread.php?t=253249&highlight=Asus+P5B+Deluxe)

Internet connectivity:

[http://www.ubuntuforums.org/showthread.php?t=238553&highlight=Asus+P5B+Deluxe](http://www.ubuntuforums.org/showthread.php?t=238553&highlight=Asus+P5B+Deluxe)

A possible solution:

[http://ubuntuforums.org/showthread.php?t=250982](http://ubuntuforums.org/showthread.php?t=250982)

A misc. thread:

[http://www.ubuntuforums.org/showthread.php?t=289320&highlight=Asus+P5B+Deluxe](http://www.ubuntuforums.org/showthread.php?t=289320&highlight=Asus+P5B+Deluxe)

---

### Post by billdotson on 2007-03-22
everything worked fine before I got this replacement motherboard.  Didn't have to do anything.  When my PC boots up it always does a system beep once which the manual says it is either: a keyboard controller error, refresh time error, or no master drive detected.

It talks about booting up for the first time and talks about going into the setup menu and setting up the system.  I just did load system defaults the first time I booted the PC.  

This first experience of building my own PC has been a nightmare.  First I thought my mouse had been messing up and I finally think it was a bug in a PC game I was playing, then I could not ever get my DVD drives to burn but then I realized that I had to install a driver for the JMicron to make the IDE drives work correctly (why in the heck do I have to install a driver for something sodlered on the MB?!), 2 weeks ago I sent my motherboard and PSU off because my PC was freezing about half of the time at the BIOS screen regardless of a cold or warm boot.  Finally I get my replacement MB and PSU back, put my PC together and then boot it up.  I get CPU fan error and realize I plugged the CPU fan in the wrong place (my fault, I know).  Then one of my case fans that is mounted inside the 3.5" bay where the hard drive kept rattling.  I tightened up some screws on the hard drive and flicked the fan around a bit and I haven't noticed it since.  

I was so happy to boot into Ubuntu for the first time in 2 weeks to only realize that the internet didn't work.  Then after running avidemux and shutting it Ubuntu freaked out and my RAM was in full usage.  To day the same thing happened except it was the CPU.  The sound isn't been working in Ubuntu either.  Then apart from that I booted up yesterday morning and after I thought I had fixed the problem of my BIOS freezing guess what the BIOS froze after booting up (PC was off all night)  Then the CPU cores are reversed.. what the heck?! and the 2nd core is the primary one with 4096KB of cache while the 1st core only has 32KB.

IMO I think the main issue here is that I just got a terrible model of motherboard.

---

