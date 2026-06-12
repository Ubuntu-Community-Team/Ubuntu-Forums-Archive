---
title: "Messed  up wife's computer need help fast"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-08-08
Since I love Ubuntu so much I decided to put it on my wife's pc. I backed up all her files on a DVD and then decided to use copywipe to format her HD, that is what I did to my pc and I had no problems getting rid of Vista Beta, however on hers I got a BSOD and restarting the computer only got me a selection of F1 and F2, F1 did nothing. So at this point I do not think copy wipe had a chance to format as this happened in a split second the BSOD.

I could load the Ubuntu cd that I used to install my copy but it took forever and a day just to get to the desktop with the install icon, clicking on that took another hour and did nothing except access the cd drive continuously without doing anything. She has a Dell 2.19 processor with 256 of ram so I figured I would swap out the stick for a 512 from my pc and in the meantime I did try installing in safe mode, nothing was legible so I added the more memory and I have absolutely nothing, I can not boot the Ubuntu cd not can I even get f1 or f2 so I am not sure if safe mode somehow turned the monitor off because her monitor said it was in safe mode and to let the os change it. Well there is no OS so I am screwed royally.

I tried my monitor and nothing with her pc connected, at this point I am thinking of popping the HD from my wife's pc into another pc but think this problem would just replicate itself there.

Any ideas how I can get out of the dog house?

Help TIA

---

### Post by overdrank on 2007-08-08
> **yogo said:**
> Since I love Ubuntu so much I decided to put it on my wife's pc. I backed up all her files on a DVD and then decided to use copywipe to format her HD, that is what I did to my pc and I had no problems getting rid of Vista Beta, however on hers I got a BSOD and restarting the computer only got me a selection of F1 and F2, F1 did nothing. So at this point I do not think copy wipe had a chance to format as this happened in a split second the BSOD.

I could load the Ubuntu cd that I used to install my copy but it took forever and a day just to get to the desktop with the install icon, clicking on that took another hour and did nothing except access the cd drive continuously without doing anything. She has a Dell 2.19 processor with 256 of ram so I figured I would swap out the stick for a 512 from my pc and in the meantime I did try installing in safe mode, nothing was legible so I added the more memory and I have absolutely nothing, I can not boot the Ubuntu cd not can I even get f1 or f2 so I am not sure if safe mode somehow turned the monitor off because her monitor said it was in safe mode and to let the os change it. Well there is no OS so I am screwed royally.

I tried my monitor and nothing with her pc connected, at this point I am thinking of popping the HD from my wife's pc into another pc but think this problem would just replicate itself there.

Any ideas how I can get out of the dog house?

Help TIA

HI are you sure your ram from the other system is compatible with her system? There are many types of memory and it may not be compatible. :(

---

### Post by Rocket2DMn on 2007-08-08
Having problems with the LiveCD is pretty common.  If all you're going to do is install, you don't need the LiveCD, you can use the Alternate CD instead.  Get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box at the bottom for Alternate CD.
This will give you a text based install that does not require loading a live session with all the graphics and whatnot.
Don't forget to check the md5sum
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then burn at a slow speed, like 4x, to help prevent write errors

Just use the RAM she has, it will make life easier later.

---

### Post by Jerry N on 2007-08-08
> **yogo said:**
> 

Any ideas how I can get out of the dog house?

Help TIA

Have you tried 4 dozen long stemmed red roses and a diamond bracelet?\\:D/

---

### Post by gn2 on 2007-08-08
Easiest and quickest way to get it up and running would be to fit a brand new hard drive put the RAM back the way it was originally and install Ubuntu.

---

### Post by Al3xK3aton on 2007-08-08
This should have been your wife's decision, not yours. "I like it so I forced it on somebody else" is not generally considered a good excuse for this type of behavior. Perhaps you should see a marriage counselor.

---

### Post by Rocket2DMn on 2007-08-08
> **Al3xK3aton said:**
> This should have been your wife's decision, not yours. "I like it so I forced it on somebody else" is not generally considered a good excuse for this type of behavior. Perhaps you should see a marriage counselor.

I don't think that's really our judgement to make on him, let's just help him with his technical problems, he can deal with the repercussions of his actions later (without our relationship advice).

---

### Post by duydaniel on 2007-08-08
sometime, bad CD reader or defected install CD can be the case...
you should put back her ram, secure all the cable connections inside the computer case.

---

### Post by yogo on 2007-08-08
I put back her ram and I now have her HD out, I was going to boot windows and see if her HD would register, however Lilo grub loader will not allow me to disconnect the Ubuntu HD, I am wondering if I can hotswap when I take start windows and replace the hd's quickly?

BTW, I did have her permission and she wanted to:)

I definately will get the alternate cd as the live cd is a pain.

Hopefully I do not have to remain locked in my room much longer.

---

### Post by Rocket2DMn on 2007-08-08
To my knowledge, you cannot hotswap internal hard drives, though if you were able to unmount them that might work...  However, you cannot swap during a boot sequence for sure.  Things will explode.

---

### Post by bwtranch on 2007-08-08
I see everyone is having some fun at your expense. Well, it's been a hot day slaving over a cool computer and I guess everyone needs some comic relief.
I think you had the right idea, thinking the RAM was the problem. I think really the min now should be 512 and I use a Gig just to be safe. (Need more, actually) I think the problem might be that the new RAM is not being recognized, for whatever reason. My rescue CD of choice is a Knoppix iso. Run that baby live ('bout the only way, really, yeah I know you CAN install it) and look at the log files. It will run and she just might like the desktop so much that she might just want to keep it:popcorn:

---

### Post by medley on 2007-08-08
> **yogo said:**
> I put back her ram and I now have her HD out, I was going to boot windows and see if her HD would register, however Lilo grub loader will not allow me to disconnect the Ubuntu HD, I am wondering if I can hotswap when I take start windows and replace the hd's quickly?

BTW, I did have her permission and she wanted to:)

I definately will get the alternate cd as the live cd is a pain.

Hopefully I do not have to remain locked in my room much longer.

I had kind of a nasty situation last night, and downloaded the super grub disk. I made a bootable floppy and eventually it got me to a place where I could salvage the hard drive and start the Ubuntu re-imaging. 

I used the technique described here:
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

The system I was working on had no cd drive, and couldn't boot from USB. Eventually got things fixed up. The SGD may help you get to at least being able to boot the HD.

Good luck.

---

### Post by yogo on 2007-08-08
> **bwtranch said:**
> I see everyone is having some fun at your expense. Well, it's been a hot day slaving over a cool computer and I guess everyone needs some comic relief.
I think you had the right idea, thinking the RAM was the problem. I think really the min now should be 512 and I use a Gig just to be safe. (Need more, actually) I think the problem might be that the new RAM is not being recognized, for whatever reason. My rescue CD of choice is a Knoppix iso. Run that baby live ('bout the only way, really, yeah I know you CAN install it) and look at the log files. It will run and she just might like the desktop so much that she might just want to keep it:popcorn:



I am now downloading the alternate cd but I had an old celeron around that had 364mb or ram, so I decided to give the live cd a go in that. If that hangs up I will definately use the alternative cd.

I am almost positive the two Dells are compatible as hers is a 2.19 and mine is a 2.53 so I am pretty sure I did not muck the memory up although hers was the hardest pc I have ever put memory in, maybe because my two year old son was jumping on my back while I was trying to do so.

---

### Post by yogo on 2007-08-08
What is the command to check the hard drive? the install is not detecting it. I do not think it is fried, but I did get the BSOD and was not able to format it.

---

### Post by bwtranch on 2007-08-08
Yeah, sometimes if those pins aren't seated FIRM, it doesn't work. I remember one time, I thought I had it, even called the company. I did it again as they asked and sure enough, they weren't seated properly. After that, no prob. I'm not willing to say that's absolutely the problem, but that's the place to start (that's where I would start, anyway). 

I have been pitzin' around on the forums today, something I don't do normally. But, people do have problems with Feisty. I never really did, that much. But, I am testing this Gutsy on my main machine (I have a backup machine with Mandriva if things get dicey), but I have had NO PROBLEMS with this one and I have tried everything to crash it. This is going to be the best Ubuntu ever. I bet you could try the 7.10 Tribe 4 (gets a freeze tomorrow) and I wouldn't be surprised if it worked like a charm. Really, I would, what have you got to lose? I'll bet cha a nickel:)

---

### Post by bwtranch on 2007-08-08
Let's see the output for lsmod

---

### Post by bwtranch on 2007-08-08
Need somebody to help. I don't know all this off the top of my head. Hello World?:lolflag:

---

### Post by duydaniel on 2007-08-08
> Live like you will die tomorrow -- learn like you will live forever - Mahatma Ghandi

If I would die tomorrow, I would then do whatever I want today. If I would live forever, I probably don't want to learn since I believe I still have .... time. :lolflag:

---

### Post by bwtranch on 2007-08-08
Very clever. But I was trying to help this guy with his problem.:)

---

### Post by yogo on 2007-08-08
Ok with all the multiple pc's changing rooms and hd's etc, the hard drive not being detected was simple, I was explaining to my wife what I needed to do and low and behold, the hd was not connected to the motherboard. I did connect it but from cattying it from one end of the house to the other it pulled out.

Another dilemma is my monitor goes into power save mode and you have to activate using pc, so once I got the hd plugged back in, my monitor is in power save mode and I can not get anything one the monitor. 

So close but yet so far!

---

### Post by bwtranch on 2007-08-08
LOL Power saving mode. That's a good one. Hope they don't have that on the space shuttle today. "But we have a new kernal, captain." "I don't care if you call me a colonel or captain!, just get the f@#king computer running." "But, sir, I have to download it from microslop." "We're dead, just try to put it down in China."

---

### Post by yogo on 2007-08-08
I think I may have a solution, I take my Hd with Ubuntu installed on and put that in my wife's pc. Will my Windows bootloader work for mine to boot Windows in my pc without the Ubuntu install....I think yes even though the grub loader loads first. If so she will have her pc running and I can deal with formatting her hd if recoverable. 


I still am not sure how to wake up her monitor if the new os is installed?

---

### Post by dhtseany on 2007-08-08
> **Al3xK3aton said:**
> This should have been your wife's decision, not yours. "I like it so I forced it on somebody else" is not generally considered a good excuse for this type of behavior. Perhaps you should see a marriage counselor.

HAHAHA me and my ol' lady got a good laugh out of that :)

---

### Post by bwtranch on 2007-08-08
Sounds like a plan. Might have to go into recovery mode. Gonna be some issues. Let me know.

---

### Post by yogo on 2007-08-08
> **bwtranch said:**
> Sounds like a plan. Might have to go into recovery mode. Gonna be some issues. Let me know.

Before I do, is there any way I can set the Ubuntu drive to not let the monitor go into save mode or is this in the cmos? if the latter I am really ********* 

TIA

---

### Post by dhtseany on 2007-08-08
So you can boot into Vista, right? If so, pop in the Ubuntu alternate CD, run the setup and just whipe the HDD w/ Ubuntu on it and do a full, clean reinstall of it. If it's not recognizing the HDD, grab an old school Windows98SE bootdisk and put WDCLEAR.exe on it.

[Boot Disk Images]("http://www.bootdisk.com")
[WDCLEAR (In a ZIP File)]("http://www.ufaa2.com/NewTechSite/Downloads/Files/wdclear/WDClear.ZIP")

WDCLEAR's sole purpose is to write 0's to your HDD and whipe it completely. If WDCLEAR can see the drive, then whipe the mofo, reboot with the alternate CD and try reinstalling Ubuntu. The setup should pick up the other HDD and setup the partition tables on it's own. It will also reinstall GRUB.

Let me know how that turned out (if you tried it.)

Just giving you another method to try,

Sean

---

### Post by bwtranch on 2007-08-08
I do nominate yogo as the best (funniest thread of the day). You should get a small, and very cheap penguin that was made in France for your lack of effort. :) It will be filled with cheese not has spoiled by the time it gets to you, BUT, we appreciate your fortitude none the less. I think that this illistrates a point that all children should take heed: do not let drunk penguins ride in the back seat. They should be restrained and in certain states, held in a car seat, since they are below the normal height limit. 

I would also like to ask the moderators of this fine forum (the Gods) to give us latitude on what has been a total and complete breach of the rules which are allowed. Thank YOU. And I promise to never do it again. Unless it turns out to be this funny.:KS

---

### Post by bwtranch on 2007-08-08
If it has an input, like scrolling, mouse whatever. It shouldn't go into that mode. Geez,  I'm not really sure. I've had 'em go to sleep on an install. I don't know, the mouse always wakes it up though.

---

### Post by xpod on 2007-08-08
> 
I would also like to ask the moderators of this fine forum (the Gods) to give us latitude on what has been a total and complete breach of the rules which are allowed. Thank YOU. And I promise to never do it again. Unless it turns out to be this funny.

Thread seemed quite normal to me...
Certainly sounds a bit like my house at times thats for sure:)

EDIT:...I do feel for you yogo:)

---

### Post by yogo on 2007-08-08
I appreciate all the love.

Ok I tried pulling my ubuntu hd and the monitor thing has gor me screwed, I just have a blank monitor, BTW I can not boot into windows and it can not see a link to the boot loader.

Right now I must have disconnected something else as my drives do not open in the other pc. I put ubuntu back into mine and works.

---

### Post by dhtseany on 2007-08-08
> **bwtranch said:**
> I do nominate yogo as the best (funniest thread of the day). You should get a small, and very cheap penguin that was made in France for your lack of effort. :) It will be filled with cheese not has spoiled by the time it gets to you, BUT, we appreciate your fortitude none the less. I think that this illistrates a point that all children should take heed: do not let drunk penguins ride in the back seat. They should be restrained and in certain states, held in a car seat, since they are below the normal height limit. 

I would also like to ask the moderators of this fine forum (the Gods) to give us latitude on what has been a total and complete breach of the rules which are allowed. Thank YOU. And I promise to never do it again. Unless it turns out to be this funny.:KS

I'm attempting to understand the relevance of these posts to helping this guy get his wife's computer back up and running....:confused:

---

### Post by dhtseany on 2007-08-08
> **yogo said:**
> I appreciate all the love.

Ok I tried pulling my ubuntu hd and the monitor thing has gor me screwed, I just have a blank monitor, BTW I can not boot into windows and it can not see a link to the boot loader.

Do you have video during your POST?

> 
Right now I must have disconnected something else as my drives do not open in the other pc. I put ubuntu back into mine and works.

Are both your HDDs detected in the BIOS?

---

### Post by yogo on 2007-08-08
> **dhtseany said:**
> Do you have video during your POST?



Are both your HDDs detected in the BIOS?
Yeah both of my drives are detected and despite taking one of mine out and putting it back in, mine works perfect.

It is my wife's pc that does not work with her hd or my Ubuntu, I also swapped them in a Celeron and they did not work, my problem is the monitor goes into save mode on both the wife's and old celeron, although the first time with the celeron, the HP welcome came up so that must be in the cmos, as the hd was not connected at that time.

---

### Post by FrankBlourtango on 2007-08-08
IF you can download and make a knoppix CD, you can boot the system and use fdisk to return the hard drive to a windows hard drive.  Use the win95 type partition.  Then you can at least get back to windows.

---

### Post by asmoore82 on 2007-08-08
does your Wife's Dell have a Pentium CPU or Celeron?

---

### Post by HermanAB on 2007-08-08
You have a choice - you can carry on fighting the system with Ubuntu, or you can try another distribution.  Each distribution has a different set of wizards to figure out what to do with the hardware.  Give Mandriva, Fedora and Suse a try.  One of them should work.

---

### Post by bwtranch on 2007-08-08
That was one of the options. Knoppix iso. Did everyone read all the posts?:confused:

No, we are not re-inventing the wheel. Don't be obtuse.:)

---

### Post by lucy_liu_lover on 2007-08-08
When you first boot up, do you get a bios screen ? Last time when I couldn't get my monitor to work on a new system that I built, it was the motherboard that was damaged; maybe by static.

---

### Post by bwtranch on 2007-08-08
Thanks HermanAB, that's pretty much what I have been saying all along. I have Mandriva on the AMD 64 in case Gutsy crashes. It hasn't happened, but that is a great backup. It's 100% Linux too. It has no windoze partitions. It takes a little to get me to use it, 'cause I like using Ubuntu, but if I have a problem, it is there. And I like Mandriva, it's good. I like driving Chevy's, but that doesn't mean I forgot how to drive Toyota.

---

### Post by yogo on 2007-08-08
> **lucy_liu_lover said:**
> When you first boot up, do you get a bios screen ? Last time when I couldn't get my monitor to work on a new system that I built, it was the motherboard that was damaged; maybe by static.
   No I do not get any bios my guess is I screwed up everything today as I had three open at once so static could be an issue, it is weird though as bios showed up after it did not show, then reappeared but can not get it back now!

---

### Post by yogo on 2007-08-08
> **asmoore82 said:**
> does your Wife's Dell have a Pentium CPU or Celeron?

Pentium is what my wife has and I have an old spare celeron laying around for parts etc.

---

### Post by steveneddy on 2007-08-08
> **Al3xK3aton said:**
> This should have been your wife's decision, not yours. "I like it so I forced it on somebody else" is not generally considered a good excuse for this type of behavior. Perhaps you should see a marriage counselor.

He's the Man. He doesn't **need** her permission.

And at the OP - just go out and buy her a new PC and be done with it. This will give you an extra PC to mess around with and give her a reason to "thank" you.

:popcorn:

---

### Post by yogo on 2007-08-09
> **steveneddy said:**
> He's the Man. He doesn't **need** her permission.

And at the OP - just go out and buy her a new PC and be done with it. This will give you an extra PC to mess around with and give her a reason to "thank" you.

:popcorn:


You said it right I am the man, that is why the new pc would go to me and she would get mine.

All kidding aside, I am the one who uses heavy apps and programs, she just surfs so she really does not need much more than Internet.

As of now I have Ubuntu installing in the Celeron and is about 70%.

---

### Post by kozy6871 on 2007-08-09
Don't feel bad about wrecking a computer.  I just did the same thing on the house computer.  The difference is that I bought her a laptop for her birthday.  12 hours later, I'm still installing Windows Updates.  Ubuntu took 15 minutes, and I was able to everything except play games.  Windows might still be good for something.

---

### Post by tashmooclam on 2007-08-09
I searched the hardware requirements for Ubuntu 7.04 

Minimum requirements

      300 MHz x86 processor
   
      64 MB of system memory (RAM)

      At least 2 GB of disk space (for full installation and swap space)

      VGA graphics card capable of 640x480 resolution

      CD-ROM drive

*If your system has less than 192 MB of system memory, use the Alternate Installation CD.*
Recommended minimum requirements

      500 MHz x86 processor

      192 MB of system memory (RAM)

      8 GB of disk space

      Graphics card capable of 1024x768 resolution

      Sound card

      A network or Internet connection

Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation.

If all else fails, Circuit City has Acer laptops for $369. :)

---

### Post by yogo on 2007-08-09
The old Celeron has 760 ...above 700, not sure the exact specs anymore, it has 364 mb of ram and 40 gigs of hd so it should be ok, I was actually looking for the command for how much ram the os sees. Just wanna make sure the 256 stick is seen or that would explain it being somewhat slow. It use to fly with Millennium on it.

I had to take the memory out as it somehow locked the monitor in save mode, putting the memory back in, well I am not sure Ubuntu sees it and I have to get my wi-fi card out of the Dell yet so I can not get installs like hardinfo to tell my specs.

---

### Post by yogo on 2007-08-09
Ok ,system monitor says it has over 300 so it sees all memory figuring it uses some for swap.

Man it has a super slow shut down, other that that it seems like it may be ok.


More like it hangs at shut down, here it is a couple of minutes sine I shut it down and it is hanging on.

---

### Post by bwtranch on 2007-08-09
Geez, you are the man today. Wait 'til the women come along and kick our ***. 
Well i guess I'm really not ok because I had to sell my ranch :sad:

It's otay and I will get a lot of money anyway:(
Just not as much:)

But, I do have some really fine cheesecake recipes.

Would you like some?

---

### Post by bwtranch on 2007-08-09
Sounds like it is doing better, hey? Could you possibly open up a terminal and get some stats? Were're all green over here. lsmod, ifconfig

Really we're not going to find out where you live (actually, we already know)

---

### Post by bwtranch on 2007-08-09
I have been hanging with this thread for so long. I can't remember. You don't have a dual boot on your wife's computer, do you?

---

### Post by Trab on 2007-08-09
hey there, hoping to help...while i've been using ubuntu for 3 years or so now, i'm certainally not the most detailed on the workings of linux, but fixing computers, that i can do...heck i'm in the process of fixing my own, my brothers, my mom's, and the neighbor's hard drive all at the same time! (oh how i loath computers at the moment).


anyways, lemme see if i can clairify/try to understand you so i can help fix it.


you believe you borked your wife's hard drive, so you're trying to fix it. in fixing it, the disc hangs, so you tried swapping the memory. now you're not sure if the hard-drive itself is dead, so you're testing that on your own system, which has some problem with the monitor going to sleep?


my advice: if possible, grab another cable, and plug all 3 hard-drives into YOUR computer, booting into linux. then, use gparted (or the gnome-partion editor) to wipe your wife's hard-drive clean.

grab a copy of a liveCD, and try using that in her system. i've noticed something strange: sometimes using an old copy of liveCD works better (IE try a dapper or edgy disc as well...sometimes they dont hang when the others do! noticed this while working on a professor's PC...)

if her computer is borked, its borked. call dell, have them replace the broken parts...heck, order her a new preinstalled Ubuntu Dell :-).


(borked = broken/messed up).


if you could clarify your specific CURRENT problems, I will try to help you more.

cheers.
Trab

---

### Post by Frak on 2007-08-09
What video card do you have
What type of port is it in (AGP, PCI, PCI-e, etc)
What speed is your processor
What brand of motherboard do you have
Last but not least, bwtranch, take a coffee break :guitar:
**EDIT**
I agree with Trab, I have used a Dellbuntu computer, and they work 100% perfectly :)

---

### Post by yogo on 2007-08-09
> **Trab said:**
> hey there, hoping to help...while i've been using ubuntu for 3 years or so now, i'm certainally not the most detailed on the workings of linux, but fixing computers, that i can do...heck i'm in the process of fixing my own, my brothers, my mom's, and the neighbor's hard drive all at the same time! (oh how i loath computers at the moment).


anyways, lemme see if i can clairify/try to understand you so i can help fix it.


you believe you borked your wife's hard drive, so you're trying to fix it. in fixing it, the disc hangs, so you tried swapping the memory. now you're not sure if the hard-drive itself is dead, so you're testing that on your own system, which has some problem with the monitor going to sleep?


my advice: if possible, grab another cable, and plug all 3 hard-drives into YOUR computer, booting into linux. then, use gparted (or the gnome-partion editor) to wipe your wife's hard-drive clean.

grab a copy of a liveCD, and try using that in her system. i've noticed something strange: sometimes using an old copy of liveCD works better (IE try a dapper or edgy disc as well...sometimes they dont hang when the others do! noticed this while working on a professor's PC...)

if her computer is borked, its borked. call dell, have them replace the broken parts...heck, order her a new preinstalled Ubuntu Dell :-).


(borked = broken/messed up).


if you could clarify your specific CURRENT problems, I will try to help you more.

cheers.
Trab


Thanks for the well laid out post.

Here is where I am at, I think I may have borked my wife's Dell BUT I added her hd to an old Celeron and installed Ubuntu so the HD was fine. The biggest obstacle will be getting her wireless going.

Ironically I was going to ask for help with that in another thread but you seem up to the job.

The Edimax 54 card I took out of her Dell and the Celeron sees the connection and it is 96% or 98% a strong signal, go figure, I moved her pc into my office so they are sitting about two feet apart.

I have been reading all the tutorial on wireless but nothing I have seen will help me out.

Here is the dilemma, Ubuntu sees it, identifies it correctly and I get good output from iwconfig ifconfig. etc so there is no doubt that Ubuntu recognizes my card and the host and I have set it up without encryption for the moment, BUT Firefox can not connect to Google.


Maybe restarting her pc will let them sync, but it should be simple, any ideas would be greatly appreciated.

Thanks

---

### Post by Trab on 2007-08-09
sigh, wireless is one of the few things that can be a pain in ubuntu install.

you are using the network-manager i'm assuming?

there are a few things to try.

if it says connected, great. right click on network-manager and go to connection information. if it has an IP and a default route that look right, great.

then its deff connected to the router. open terminal and type
```

ping (default route IP)

```
if that returns all fine and dandy, type
```

ping www.google.com

```
and copy the error of that.

my guess is that you may need a driver of some kind for the router, i'm looking it up right now (only thing i'm finding is over a year outdated...)

EDIT: a restart would be a good idea regardless. wireless is so picky.

---

### Post by Trab on 2007-08-09
some things i've found, hope they help:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)
list of supported WiFi cards made by  edimax


[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
a howto for what appears the be the chipset used in that card


I dont think you gave me the correct name of the card....it may in fact be best to start a new thread in the general section with as much information as you can give on the wifi situation...
i'll check back soon, hopefully managed to fix my machine now.

---

### Post by yogo on 2007-08-09
Trab from your link I have this on  Edimax EW-7128Ig seems like at least I have the card that has the least issues.

Restarting seemed to make the connection worse, notw it does not connect, it see the router but fails.

Will post what you asked for from terminal.


**[COLOR="Red"]syntax error near unexpected token default[/COLOR]**

From pinging Google....unknown host [www.google.com](www.google.com)

---

### Post by bwtranch on 2007-08-09
Hey Frak or whatever, I was just trying to help. Nice to know the police finally showed up.

---

### Post by yogo on 2007-08-09
Thanks to everyone for the help.

If there are drivers I should add, please let me know where I should drop them. I figure I can download them on my pc and put them on hers via a memory card.


I am turning in as I have been at this way too many hours, again thanks to all.

---

