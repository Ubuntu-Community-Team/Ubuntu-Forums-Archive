---
title: "gutsy didn't fix my wireless :("
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by jctaft on 2007-10-28
Well I seem to be the only person in the world whose wireless didn't miraculously start working when I upgraded to gutsy.  I followed the prompts to install the firmware and driver, but still nothing (except that the light comes on on the wireless switch).  After following about a hundred how-to's in Fiesty with no results I finally accepted the fact that I would never get it working, and just used windows whenever no ethernet port was available.  I was so happy that gutsy had fixed the problem, but it didn't for me.

As a sidenote, my wireless was working in Dapper, but when I upgraded to Feisty (via edgy), it stopped.  Now that I have gutsy at least the light is coming on.  I suspect it's probably a quick fix, so I'm asking here before I start blindly going through how-to 's that have in the past have had a very low success rate on my machine.

Thanks in advance.

---

### Post by jctaft on 2007-10-28
I'm sorry, I completely forgot to mention that I have the broadcom 4306.

---

### Post by jinnman on 2007-10-28
Did you try enabling it in the Restricted Drivers Manager?

---

### Post by dwhitney67 on 2007-10-28
Using the magic of the keyboard and a google search, I found a link that may help you.  Here it is:  [http://ubuntuforums.org/showthread.php?t=185650](http://ubuntuforums.org/showthread.php?t=185650)

I suggest you start reading from the end, and then work your way back up to the top.

I'm surprised though that 7.10 didn't setup your wireless.  Are you able to determine if your system even detected it?  Run this command to find out:

[FONT="Courier New"]$ lspci | grep Network[/FONT]

P.S.  I will not be able to help you resolve your wireless issues; maybe someone else can.  I am merely posting here to let you know that with a little googling and some effort on your part, that a solution exists.

---

### Post by jctaft on 2007-10-28
As to enabling it in the restricted drivers, it is enabled and in use.  When I type the command:

lspci | grep Network

I get information on my wireless card.  

In response to googling it:

 I am aware that a solution probably exists, but the problem is that there are usually very many how-to's on a given topic, and most often 90% don't work  It seems that a problem can exist for a variety of reasons, and very often the author of a how-to doesn't offer any advice on figuring out whether the cause of your problem is the cause that his or her how-to deals with.  As a result, for a beginner like myself, usually the process goes something like this.

-Try the first five how-to's you find on google or in the forums

-nothing worked but now something else is screwed up.

-reinstall (since we beginners don't possess the ability to know which of the five how-to's messed us up)

-try more how-to's

-possibly reinstall

-(repeat an undetermined number of times)

-finally find the how-to that fixed the problem, but usually have learned nothing in the process, and even less idea what may have been screwed up in the meantime.

You see, the how-to's are more often algorithms than explanations, and as a result teach nothing to the beginner.  Also, usually the how-to's assume that you've tried the simple/obvious solution, but very often we beginners have not, because we don't have enough intuition to know what that obvious solution is.  That's why we are more likely to ask in the "absolute beginner talk" even though the solution is out there.

As an example:  Once my sound didn't work, and all it was was that the volume is divided into subsections, and even though my master volume was turned up,  some other slider was turned down.  None of the how-to's addressed this, because, they obviously assumed there was a deeper issue.  I came on here, and after asking me a few simple questions, a moderator was able to fix my problem in a few minutes.

So you see, it isn't that we beginners are too inconsiderate to care how precious a commodity your (the expert) time is, it's that very often the countless hours of searching google and these forums are a dead end, Whereas five minutes of somebody's time is all that was needed.

In case this doesn't make the point clear.  I am very grateful to any time someone dedicates to helping me get my wireless working.

Sorry this was so long.

---

### Post by immrlizard on 2007-10-28
Not to be smart guy but are you sure that it is a functioning card?   It would be a great disappointment to be pulling out your hair and find out the card was malfunctioning.  I have done that before.   

I had the same problems with a linksys card with the same chipset that may be the same type.   

What all have you tried so that I don't repeat anything that you have tried already?

Also, is everything else working and was it a clean build or upgrade from 7.04?

I had much better luck with clean builds then upgrades.

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) is one that I used to get mine going.   I think that there are several versions of this card so you need to make sure you are using the correct how to instructions. 

One last question, did the wireless card work in 7.04?   I see quite a number of individuals out there posting problems with this build right now but that had it working in 7.04

---

### Post by jctaft on 2007-10-28
It's a valid question about the card, Fortunately I have a dual boot, and can verify that the card works in windows.  My installation was an upgrade from 7.04, and my wireless card never worked in fiesty, although I had it working in dapper (with the firmware cutter, NOT Ndiswrapper).  In Fiesty, I tried absolutely EVERYTHING, including the link you posted(or something similar), and nothing worked.  Since i've upgraded to gutsy, The only thing i've tried is launching wi-fi radar, and hoping that my card would "see" my network automatically, like it did in dapper.  No such luck.  That's all I've done in gutsy, because I'm not "gutsy" enough to screw around with a version that otherwise works perfectly.

Thanks

---

### Post by jctaft on 2007-10-29
any ideas anyone?

---

### Post by esoxLucius4 on 2007-10-30
> **jctaft said:**
> Well I seem to be the only person in the world whose wireless didn't miraculously start working when I upgraded to gutsy. 

Nope. You're not. Unless by FIX you mean Gutsy forcing us to use good ol' cable firmly FIXED into network adapter. My laptop uses broadcom 4311 wlan adapter and with each new ubuntu version things go from bad to worse. 

If you find any solution, let us know.

Cheers, m8.
:popcorn:

---

### Post by amtnbiker16 on 2007-10-30
a buddy of mine has a dell and his wireless wouldnt work either
turns out that the defaults on his(and mine) software sources were set to official ubuntu packages only.  we fixed it by checkmarking all the third party sources.

we then went to restricted drivers manager and enabled them, the drivers were then downloaded automatically

you need a wired connection to do this

well, i hope this helps and good luck

---

### Post by jctaft on 2007-11-05
Ok, I've been trying to work on this problem in what little time I've had.  I really think that the wireless card is running, but for some reason not 'seeing' any networks.  It is listed and is enabled, and the light is on.  For some reason It doesn't have the ability to scan.  Also, typing in the SSID by had doesn't work.

Any ideas?

---

### Post by syga on 2007-11-06
On my broadcom wireless card, gutsy's restricted driver manager did not help. Several suggestions did not help.

The only way i got it to work was to follow the instructions from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by JimmieC on 2007-11-06
The above link should get you going. I'm new at this but I just installed Ubuntu and had to configure my wireless card so I can relate to what you're going through.
I gave my card a static IP address, seems to work better than letting the router assign addresses. I had to  install drivers from a CD, a .sys and an .inf file which Ndiswrapper will use instead of the linux wireless driver. If you use Ndiswrapper you will have to blacklist the default linux wireless driver. I did all this in a couple of hours, so hang in there. I found all the information I needed by searching the forums on this site.

Cheers.

Jim

---

