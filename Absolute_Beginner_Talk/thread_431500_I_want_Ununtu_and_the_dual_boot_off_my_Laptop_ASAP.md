---
title: "I want Ununtu and the dual boot off my Laptop ASAP!"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Skandall on 2007-05-03
**[EDIT: Please ignore this thread now.  Thanks to everyones help and encouragement I have sorted out the problems with my install and have no intention of removing Ubuntu.  I was just venting my frustration at the thought of being stuck with Windows still.]**

All this talk about how great and easy to use Ubuntu Linux is, I decided to take a chance and install it.  Turns out it's all a bunch of hyperbole.  The installation instructions left out some important information resulting in having to make an educated guess.  What really bakes my noodle is that no matter what I do, it simply will not recognize my built-in wireless modem.  I've tried all of the tutorials.  Still nothing.  It's just not worth the frustration.  I've been through enough thanks to my Sharp Zaurus Linux PDA.  Not to mention that it now takes Windows (which, I should point out, I hate more than you can possibly know; but the laptop was free so I can't complain) forever to load.  So I just want to know what the best way is to safely remove it and the dual boot loader.

Oh, and can someone please explain why does Linux insist on only installing packages from the internet even when you have the package on a local drive?!

I'm just frustrated here because I really want to be rid of Windows and this Linux thing still isn't working for me.  If I had my way, I'd still be using Amiga Workbench.  Oh well.  I appreciate the help.

---

### Post by jkblacker on 2007-05-03
I don't know enough to suggest a definite answer but I can give a vaguely educated guess (I'm still learning but picking a few things up!)- boot into the live cd, delete your linux partitions and resize your xp partition back to the whole size of the disk.

As for uninstalling grub, I'm not sure if that would be deleted along with anything else. Does anyone know if it's anything to do with fixing the mbr?

It's a shame you feel this way. Have you asked on here about your specific wireless problem? Often people posting here will be able to suggest things not necessarily in tutorials anywhere.

---

### Post by sloggerkhan on 2007-05-03
Install from the package on the local drive or add it as a software source.

---

### Post by darren1270 on 2007-05-03
To fix the MBR you need to boot from the windows install cd and go to recovery console and type "fixmbr"  that will let windows boot normally.

---

### Post by jfinkels on 2007-05-03
If you would ever like to try to install Ubuntu again, PLEASE PLEASE PLEASE post on the forums, I guarantee that we can fix 99.99% of all of your problems!

---

### Post by darkrose on 2007-05-03
Of course you could always try asking here how to get your wireless modem going.

---

### Post by xyz on 2007-05-03
Hi,

I can understand the frustation!! One of the things I did ,at the beginning, was to stop trying to "make it all work" right off the bat.

Once I started to use patience instead of emergency "to make it all work", it all began to fall into place.

My suggestion would be you keep Ubuntu and Windows. When, and only when, you feel like it, boot your Ubuntu and work on it a bit, but not too much...that is, not to the frustration point.

And of course, post your pbms here. It is a great community...probably the best you'll ever find.

---

### Post by darren1270 on 2007-05-03
> **xyz said:**
> Hi,

I can understand the frustation!! One of the things I did ,at the beginning, was to stop trying to "make it all work" right off the bat.

Once I started to use patience instead of emergency "to make it all work", it all began to fall into place.




I second your thoughts xyz.... I installed edgy on a toshiba laptop about 2 weeks before the release of feisty and it worked pretty well.   Once in a while it just froze but after a little while looking through this forum I fixed it.  I did however have to put that other OS back on it.... My daughter wasn't getting used to Ubuntu as quickly as I thought she would and she does take the laptop to school once in a while.

However I did setup a dual boot desktop (XP / Feisty Fawn) in our home office so her and I could learn and experiment together.  We are learning something new everyday!!!

And thanks to all the wonderful people in this forum.... !!!

---

### Post by xyz on 2007-05-03
> **darren1270 said:**
> I second your thoughts xyz.... I installed edgy on a toshiba laptop about 2 weeks before the release of feisty and it worked pretty well.   Once in a while it just froze but after a little while looking through this forum I fixed it.  I did however have to put that other OS back on it.... My daughter wasn't getting used to Ubuntu as quickly as I thought she would and she does take the laptop to school once in a while.

However I did setup a dual boot desktop (XP / Feisty Fawn) in our home office so her and I could learn and experiment together.  We are learning something new everyday!!!

And thanks to all the wonderful people in this forum.... !!!

Right on!! Way to go!!
Thanks for posting this.

---

### Post by Docter on 2007-05-03
My friend, if you are an ex-amigan then I am at a loss to understand your problem with ubuntu.

What was Workbench without "MagicMenu", "NewIcons", "MUI" and many more that I've forgotten? 

I feel your pain but I suspect that you are getting rid of the wrong OS. If you spent some time learning it you will notice how similar it is to that operating system which should have shaken the world but got lost among the games.

Maybe it doesn't have any BOING but it does have bounce. A lot of people wont understand but I know that you don't want windoze back.

---

### Post by Gina on 2007-05-03
I agree with what everyone else has said in reply... I can also understand the frustration in trying to get a wireless adapter to work.  It took me what seemed a very long time and many many tries to get my laptop wireless card working.  (As an aside I had to replace my router because the wired connection in it had ceased to work and I have suspicions about the wireless - which was dropping out every few days).  I continued trying to get wireless working whilst connected by cable to the router.  In the end I found it needed the firmware installed - I had to use fwcutter (in Ubuntu) to extract it from the Windoze driver** .sys** file.  When copied top the Ubuntu firmware folder, the system picked it up and the wireless card eventually worked.

OK I have a lot of patience and enjoy fiddling about. but in view of your dislike of Windoze (which I share), Skandall, I too would suggest keeping your dual boot and taking your time to get Ubuntu working.  Which version have you installed?  The latest (7.04 - Feisty Fawn) has better wifi support and better installation instructions - plus the ability to import your Win stuff (Documents, IE, OE settings, favourites etc.).

If you want Win to install by default, you can quite easily alter the boot sequence to make Win the default.

---

### Post by Skandall on 2007-05-03
> **Docter said:**
> My friend, if you are an ex-amigan then I am at a loss to understand your problem with ubuntu.
What was Workbench without "MagicMenu", "NewIcons", "MUI" and many more that I've forgotten? 
I feel your pain but I suspect that you are getting rid of the wrong OS. If you spent some time learning it you will notice how similar it is to that operating system which should have shaken the world but got lost among the games.
Maybe it doesn't have any BOING but it does have bounce. A lot of people wont understand but I know that you don't want windoze back.

Seriously, if I could get Ubuntu to look and function even remotely like Workbench I'd be all too happy to hang in there.  I miss having an OS that does what I want when I want and almost never gives me the finger, er busy pointer.  Is Ubuntu an RTOS?  If I really want to ditch Windows, I'll just fire up my A4000 again.  After all of these years, other OS's still can't touch what Workbench could do 15 years ago.

I have noticed several threads that indicate people are having problems (with 7.0.4 Feisty Fawn, which is what I have) connecting to wireless networks when said network is not broadcasting it's SSID.  What do you know, neither is mine.  When I get home I'll turn on the SSID broadcast and see if Ubuntu will then connect via wireless.

I've already dealt with the learning curve associated with Linux.  I have a Sharp Zaurus, it runs Linux.  I've changed from one ROM to another more times that I care to remember.  The one thing that absolutely drives me mad about Linux is this: Package managers always try to download from the internet even if you have the package locally and there never seems to be a way to tell it to use the local package rather than fishing for it on the net.  It would drive me nuts when I wanted to install something from CF, but my Zaurus would complain that it could connect to the net; it's a PDA with no built in means to connect to the internet so of course it can't download anything, why on Earth would it think that it can?!  GAH!

Sadly, ditching Windows is not really an option for me as there is one single application that I must have Windows for; CCGWorkshop.com GatlingEngine (a program that allows people to play many CCGs online).  Since I'm a developer for it and it only runs on Windows, I'm stuck with it.  I wish they would port it to something cross-platform.  Although, as I understand it, there are Windows emulators for Linux.  Maybe the gEngine will run that way.  Not sure how that would effect the DevKit though.

If turning on SSID broadcast works then I'll keep Ubuntu.  Honestly, I'd rather be using a new Amiga, but that's all mucked up still (even though they did announce new hardware this week).

---

### Post by sailor2001 on 2007-05-03
your laptop probably has a broadcom card in it and you would have to use fcutter(?) for firmware.... also I think tou have to first blacklist your card....... search the forum for your wifi card, there will be many posts for it...also don't forget to install a wifi manager (kwifi or wifi-radar)

---

### Post by lazyart on 2007-05-03
:( Another user who doesn't ask for help with Ubuntu, and whose first post is a complaint about how bad it is.

Anyhow, it's not hard to specify a CD as a source for .debs.  Go to Synaptic Package Manager, then Settings>Repositories. Click the Third Party Tab, then Add CDROM.  You might want to disable the other repositories to be sure it doesn't look outside the box so to speak.  But it's doable.

---

### Post by Skandall on 2007-05-03
> **lazyart said:**
> :( Another user who doesn't ask for help with Ubuntu, and whose first post is a complaint about how bad it is.
Anyhow, it's not hard to specify a CD as a source for .debs.  Go to Synaptic Package Manager, then Settings>Repositories. Click the Third Party Tab, then Add CDROM.  You might want to disable the other repositories to be sure it doesn't look outside the box so to speak.  But it's doable.

Your attitude is not welcome.  If Ubuntu was so great I wouldn't need to ask questions.  I wouldn't have one guy telling me to black list my card, another saying I just need the .inf and .sys, and another claiming this it's just a matter of setting up ndiswrapper to use my Windows drivers.  If it was so friendly, it would ask me if I have the package locally when it doesn't detect a network connection.  It seems that the real problem with Linux is all of the Linux users.  Far too many cooks in the kitchen and not a single one of you actually knows the right answer.

FYI:  The card is a Broadcom.  I found a post by some guy that said he got his to work after downloading .inf and .sys files then using the ndiswrapper-utils.  I tried that and it accomplished nothing.  As I said, maybe it's because my router isn't broadcasting its SSID.  I'll try that and see if things start working.

Rather than being so arrogant and stuck-up about your OS of choice you should take a step back and see that it's so convoluted and mismanaged that even a simple thing like connecting to the internet can be a total pain in the rear.  Maybe I wouldn't have to ask questions if I had just RTFM; oh wait there isn't ONE, there are millions and they all say different things about the same process because every Linux user has a different opinion about the way to do things.

Linux ought to be is embarrassed by the fact that something, anything, is easier to configure in that utter pile of vomit called Windows than it is in Linux.  How many years have people been working on Linux to make it more user friendly?  Or perhaps Linux users prefer it to be so troublesome to configure and install since those challenges make you feel smart once you've figured them out, like solving a Rubics Cube, never mind that the "challenge" wouldn't be one on any other OS.  Call be crazy, but I think that it would be far more useful to teach yourself Assembly than Linux.

Now, pause for a moment and soak in the irony of this situation because I know all too well the frustration and annoyance that results from user ignorance since I work in QA and have to answer the occasional tech support question regarding our software.

---

### Post by Zimmer on 2007-05-03
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you want to uninstall......

---

### Post by lazyart on 2007-05-03
> **Skandall said:**
> Your attitude is not welcome.  If Ubuntu was so great I wouldn't need to ask questions.  I wouldn't have one guy telling me to black list my card, another saying I just need the .inf and .sys, and another claiming this it's just a matter of setting up ndiswrapper to use my Windows drivers.  If it was so friendly, it would ask me if I have the package locally when it doesn't detect a network connection.  It seems that the real problem with Linux is all of the Linux users.  Far too many cooks in the kitchen and not a single one of you actually knows the right answer.

FYI:  The card is a Broadcom.  I found a post by some guy that said he got his to work after downloading .inf and .sys files then using the ndiswrapper-utils.  I tried that and it accomplished nothing.  As I said, maybe it's because my router isn't broadcasting its SSID.  I'll try that and see if things start working.

Rather than being so arrogant and stuck-up about your OS of choice you should take a step back and see that it's so convoluted and mismanaged that even a simple thing like connecting to the internet can be a total pain in the rear.  Maybe I wouldn't have to ask questions if I had just RTFM; oh wait there isn't ONE, there are millions and they all say different things about the same process because every Linux user has a different opinion about the way to do things.

Linux ought to be is embarrassed by the fact that something, anything, is easier to configure in that utter pile of vomit called Windows than it is in Linux.  How many years have people been working on Linux to make it more user friendly?  Or perhaps Linux users prefer it to be so troublesome to configure and install since those challenges make you feel smart once you've figured them out, like solving a Rubics Cube, never mind that the "challenge" wouldn't be one on any other OS.  Call be crazy, but I think that it would be far more useful to teach yourself Assembly than Linux.

Now, pause for a moment and soak in the irony of this situation because I know all too well the frustration and annoyance that results from user ignorance since I work in QA and have to answer the occasional tech support question regarding our software.


Respectfully sir, when you show up and preface your rant with "I have 20 years experience" and instead of asking for help, presume that the OS is broken, you should look to yourself before you declare someone's attitude as unwelcome.  With the thousands of users here who have installed without a glitch, maybe your installation woes are somewhat isolated.  For the record, my installation last week had 0 issues.  A 2 ghz P4 and Nvidia card.  And Beryl is amazing.  But it's not the same as Windows.  There are quite a few habits to unlearn.  The first time looking at Ubuntu is not unlike looking at OSX for the first time.  I cut my teeth on a TRS-80, Apple ][e and Commodore machines (and yes, I did learn assembly language).  As I have said in other threads, the Ubuntu kitchen is a bit different from the Windows kitchen.  You can still cook up a fantastic meal, but the appliances may be in a slightly different location and some of the controls might not be what you're used to.  But it works.  You just have to take the time to relearn.

And it's not easy.  It still smells to me that the install media is flawed.  If you're seriously interested in learning, folks here will help-- present company included.  I've only worked with Ubuntu for just under a year, so I'm not really the Linux zealot you paint me.  Two of my boxes are Ubuntu, the other 5 or 6 are Windows.  I run Server 2003 and XP clients because I'm really not interested in pushing Ubuntu onto the wife and kids.  It's my primary OS.

Is Linux perfect?  Of course not.  No more perfect than XP.  Each has their place and I certainly don't care which one anyone uses.  I'd like to see it succeed more.  It does bug me when folks assume that their XX years of experience in IT translates to a whole lot here.  No doubt you understand networking concepts and hardware issues and can see on pretty much any machine/OS what a problem might be.  I respect that.

Bottom line is, if you want help, we are more than happy to offer.  My personal help might be limited but I do what I can.  I started in the early 80's but LDA #$30: JSR $FFD2 (6502 assembly to print a comma on a Commodore machine) doesn't really do me much good here, so I don't advertise it.

If you want to come in and tell everyone that it doesn't work-- especially when we are all running it and you will get a totally different response.

I'm happy to leave this conversation at that.  I hope you are still interested in sticking with Ubuntu.  It a fun, sometimes seat of the pants ride.  I'm constantly uncovering stuff that makes me say "Wow, I didn't know I could do that."  While I used to use Ubuntu sparingly and depend on Windows, it has become the exact opposite.

Best of luck.

---

### Post by kittyhawk63 on 2007-05-03
Tagging this for future reference.

---

### Post by darkrose on 2007-05-03
> **Skandall said:**
> If it was so friendly, it would ask me if I have the package locally when it doesn't detect a network connection.
That's actually a good idea, you should submit a wishlist item to the developers.

> ... it only runs on Windows, I'm stuck with it.
Yes it would be good if one of the developers could create a Linux port of it, wait a minute...
> Since I'm a developer for it ...
hmm

---

### Post by drowner on 2007-05-03
Why dont you write a letter?

Actually, I'll write for you

[COLOR="Navy"]Dear Sir,

I had heard very good things about your product. Given that the price was free, I thought I would try it.

However I do not like it, so I will abuse a bunch of people who do.

Regards,[/COLOR]


There. Print that of and sign it, and send it to someone who cares.

---

### Post by Skandall on 2007-05-04
> **darkrose said:**
> Yes it would be good if one of the developers could create a Linux port of it, wait a minute...hmm

Yeah, it occurred to me that one might easily draw such a conclusion.  I develop games for play using their API.  I have zero knowledge with regard to writing a multi-platform client server application.  I wish I could.

---

### Post by teddybairs1 on 2007-05-04
Gentlemen please... Some civility here? We're all friends. We all hate MS. We're all wanting the same goal here. A functioning computer which doesn't need MS to tell us what to do.
Skandill, Is your card a Broadcom 4318?

This card is notorious for it's being a pain to get working. Is it possible? Yes. I have one, and it is working. Was it easy? No. In fact, sometimes it seemed like I needed to do a bit of raindancing, fasting and prayer in order to get it working.

One of the main problems is that the Ubuntu .iso ships with the driver, but without the firmware for legal/licensing reasons. From what I understand, Canonical had talked with Broadcom several times about including it under the GPL and Broadcom is stingy. The driver bcm43xx works. I know it does because my laptop is using it now without incident. But it does need the firmware. Someone here on the site managed to package a .deb with the firmware. I'm uploading it to this post. save it to your desktop, right click on it and select Gdebi package installer. This should install the package for you. For all intents and purposes this should install it for you. If you installed ndiswrapper, completely remove it. Feisty doesn't need it for this card.

I understand your pain. I've run into a number of snags with Linux in general myself. Most of them were easily fixable, I just didn't know how at the time and I made it worse by panicking and doing drastic things. Uninstalling your OS is drastic and desperate, especially over a wifi card.

---

### Post by Adramelech on 2007-05-04
If you have a package on a cd or your hard drive you dont have to use synaptic to install it, just double click on it. Am I wrong?

---

### Post by Skandall on 2007-05-04
> **lazyart said:**
> Respectfully sir, when you show up and preface your rant with "I have 20 years experience" and instead of asking for help, presume that the OS is broken, you should look to yourself before you declare someone's attitude as unwelcome.
Sorry, that's not how I meant it.  If anything, I was under the impression that Ubuntu wouldn't have issues like this.  I was frustrated and I vented.  I should have just put the laptop down and walked away.

> For the record, my installation last week had 0 issues.  A 2 ghz P4 and Nvidia card.  And Beryl is amazing.
Actually, Beryl was a large part of what motivated me to give this a try again.  I doubt that my laptop will be up to the task.  When I turned on Ubuntu's screen effects all I got was a white screen.  Then there's the who issue of not connecting to my wireless.  It'd be nice to see, but I doubt that any system I have could handle it.  I don't know, maybe my PS3 (which is the other motivation).

> But it's not the same as Windows.  There are quite a few habits to unlearn.  The first time looking at Ubuntu is not unlike looking at OSX for the first time.  I cut my teeth on a TRS-80, Apple ][e and Commodore machines (and yes, I did learn assembly language).  As I have said in other threads, the Ubuntu kitchen is a bit different from the Windows kitchen.  You can still cook up a fantastic meal, but the appliances may be in a slightly different location and some of the controls might not be what you're used to.  But it works.  You just have to take the time to relearn.
For me it was: Timex Sinclare 1000 > Commodore 64 > Amiga 500 > Amiga 4000 > MacOSX Quicksilver G4 > Compaq Presario V2000 laptop.

Given that I was using Amiga Workbench daily up until 2002, I don't think I have many Windows habits (certainly none that I wouldn't be happy to unlearn).  The fact that Ubuntu is not the same as Windows is a major draw.  Parts of it remind me of Workbench too which is all the better.

Anyway, I'm fairly sure that if I could get my system set-up right, I would much rather stay on Ubuntu most of the time.  I can do the majority of my dev work on Ubuntu and would only need Windows for updating the servers and playing.  I'll keep Ubuntu and tinker with it as time permits.

---

### Post by freebird54 on 2007-05-04
Glad to hear you're sticking with it a bit.  Even the Amiga had little gotchas at times :)

My path was C64 -> C128D -> A1000 -> A2000 -> A2500/030 -> PC OS/2 -> win -> Ubuntu!  Not that Windows was the only thing left at that point....

---

### Post by darkrose on 2007-05-04
On the subject of Amiga, anyone tried out AROS? - [http://aros.sourceforge.net/](http://aros.sourceforge.net/)
Definitely alpha level but interesting none the less.

---

### Post by katch22 on 2007-05-04
> **Skandall said:**
> Sorry, that's not how I meant it.  If anything, I was under the impression that Ubuntu wouldn't have issues like this.  I was frustrated and I vented.  I should have just put the laptop down and walked away.


Damnit. I was about to go off on what an @$$ this guy is and then he has to go and be all mature and polite.. grrrr.. lol! :)

---

### Post by houstonbofh on 2007-05-04
> **katch22 said:**
> Damnit. I was about to go off on what an @$$ this guy is and then he has to go and be all mature and polite.. grrrr.. lol! :)
Haha...  Me to.  However, I do have to go with one point...

> **Skandall said:**
> Your attitude is not welcome.  If Ubuntu was so great I wouldn't need to ask questions.
Just think about that for a minute...

Now, actually, you didn't.  This post, with almost the same title comes up at least weekly.  Reading regularly for a week, or a search would find it.  Most problems can be fixed with a search.  I rarely ask questions, as I have no patients at all, and a search is **rightnow!**  Yet still, many of us answer the same questions over and over to try and help.  One thing that I say over and over to people with WiFi trouble is to buy another card. **Many** are well supported.  And is all the stress you have suffered worth $20 for a new, well supported card?

Link for those that stumble upon this later;
[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

---

### Post by Docter on 2007-05-04
Woah.... back up...


New Hardware? This week?

oooh.



Ok.. carry on.

---

### Post by baekeland on 2007-05-04
I am using Feisty7.04 there were problems and this community helped a lot with clearing those small problems up.  Now there is a new problem for me.  I logged off of Ubuntu and went and did some work in XP when I booted feisty Ubuntu back up  it goes through it's splash screen, monitor blinks on and off, round hourglass appears and that is that.  The OS refuses to boot into the GUI format at all -- just the hourglass spinning and spinning.  I can get to a command line, I think ....but once there what commands should I try to get back into Ubuntu's GUI?  I am running an IBM ThinkCentre, Intel embedded graphic chip, 1G of Ram and Ubuntu has never done this to me before.  I also do not get an error message of any kind whatsoever.  I have tried using recover to no avail.

Also, I have another question in general:  Why when Grub loads up are there maybe **4 Ubuntus I could start** and under other **operating systems** there is only one edition of winBlows  XP.  I would like to have only one Ubuntu and One XP to choose from.  The other 3 Ubuntus are older than the one I boot to, but it is rather annoying having them sitting there in GRUB.

Any help would be greatly appreciated, for at this point of the game it appears to be Ubuntu breaking on me rather than XP.

Thanks,

Baekeland

---

### Post by baekeland on 2007-05-04
Just as an aside, to the guy who wants Ubuntu off his laptop and the dual boot.  How short are memories are.  It is utter nonsense to believe than ANY edition of Windows does not come with it's own variety of trouble and errors.  I have had to reload Windows more times than I care to remember and if you think for one minute all is rosy with that thing called Vista trust me I have the ULTIMATE EDITION OF VISTA that should be renamed the ULTIMATE NIGHTMARE.  Still, I play and prod it every now and then and refuse to allow it to frustrate me to the point of a breakdown.  I just take it real slowly.  XP has been around for awhile and you have worked on it for a while I am guessing and there is a certain comfort zone using it. I know as my learning curve for XP has pretty much expired.  

Ubuntu at the moment is frustrating me to death, but any thing worth learning has a learning curve to it and the day you show me a PERFECT OS (even Macs have some problems i.e., not enough memory, et cetera) is the day I might just drop dead!

Take it easy, Bro, learning curves are a bitch and Windows 3.1 to 98 were a **real **learning curve.  IBM's OS/2 Warp was easier in configuring the Internet, networking, or running a bulleting board.  Winsocks sucks, always has, always will, and, yes, it is still right there in Vista as is DOS.  

For a REAL learning curve trying jumping into Vista from XP.  

Peace,

Baekeland

---

### Post by lazyart on 2007-05-04
> **baekeland said:**
> I am using Feisty7.04 there were problems and this community helped a lot with clearing those small problems up.  Now there is a new problem for me.  I logged off of Ubuntu and went and did some work in XP when I booted feisty Ubuntu back up  it goes through it's splash screen, monitor blinks on and off, round hourglass appears and that is that.  The OS refuses to boot into the GUI format at all -- just the hourglass spinning and spinning.  I can get to a command line, I think ....but once there what commands should I try to get back into Ubuntu's GUI?  I am running an IBM ThinkCentre, Intel embedded graphic chip, 1G of Ram and Ubuntu has never done this to me before.  I also do not get an error message of any kind whatsoever.  I have tried using recover to no avail.

Also, I have another question in general:  Why when Grub loads up are there maybe **4 Ubuntus I could start** and under other **operating systems** there is only one edition of winBlows  XP.  I would like to have only one Ubuntu and One XP to choose from.  The other 3 Ubuntus are older than the one I boot to, but it is rather annoying having them sitting there in GRUB.

Any help would be greatly appreciated, for at this point of the game it appears to be Ubuntu breaking on me rather than XP.

Thanks,

Baekeland

You'd be better served to create a new thread for your questions-- it has nothing to do with the original post and you'll get more views with a topic that illustrates your issue.

---

### Post by Skandall on 2007-05-04
> @teddybairs1
Skandill, Is your card a Broadcom 4318?

Indeed, that is the one.  I'll give your steps and package a go and cross my fingers that it works.

> @ freebird54
Ack!  How could I forget my C128D?!
Timex Sinclare 1000 > C64 > C128D > Amiga 500 > Amiga 4000/060 > MacOSX Quicksilver G4 > Compaq Presario V2000 laptop

> @darkrose
On the subject of Amiga, anyone tried out AROS?

Frankly, AROS and MorphOS have done nothing but fracture what's left of the Amiga community.  The less said about it the better.  I don't even see how it's legal for them to clone an existing OS.

> @katch22 & houstonbofh
Damnit. I was about to go off on what an @$$ this guy is and then he has to go and be all mature and polite.. grrrr.. lol!

Sorry, well sort of anyway.

> @Docter
Woah.... back up... New Hardware? This week?

Yes, NEW hardware! The specs for the $500 entry level model were released Monday 30 April and the specs for the $1,500 high end version are due out Monday 7 May.

Previous hardware was also released, but never really did all that well, largely because AmigaOS 4.0 wasn't ready.  So, those motherboards that were intended for AmigaOS actually ended up with a version of Linux.

> @baekeland
For a REAL learning curve trying jumping into Vista from XP.

I QA 3D modeling software so I've had the "joy" of testing on Vista.  I seriously hope that I never have to use a Vista PC.  It's wishful thinking, I know.

---

### Post by ionospheric on 2007-05-04
I have had problems with this Broadcom card as well, but got it to work after an hour of struggling. Here is the  main link:

[http://ubuntuforums.org/showthread.php?t=420006&highlight=1370](http://ubuntuforums.org/showthread.php?t=420006&highlight=1370)

One thing to add is that I use WPA, and the keyring manager seemed to store the hexadecimal key rather than the actual password. Once I deleted the key in keyring manager and reentered it in the network manager applet (top right of screen, connect to other networks), it worked again.

A few comments:

I am a former Amiga user as well and Ubuntu has brought back the excitement of that machine to me. AmigaOS was a subset of Unix, but this here is the real deal.

A few reasons why I believe this version of Ubuntu is the breakthrough:

- the Debian-based package management simply works, and it is fast and vast. I have had problems with RPM-based distros.

- In Firefox, you click on a link to a video in a format that hasn't been installed yet. A window comes up asking if you want to install a codec, offers a few sorted by rating (!), and after you have acknowledged the installation, the video starts playing without restarting anything!

- Whatever network drives you find browsing in Nautilus, you can right-click and select "Connect To", and then a permanent link will be created on your desktop- as easy as "Map network drive" in Windows.

- I enabled dual monitors in minutes with a few clicks!

Final word:
Please don't bark at the helpful people in this forum. This community is what it is all about.

---

### Post by Josey on 2007-05-04
**[SIZE="3"]Broadcom 4318[/SIZE]**

Install this
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133)
reboot

your wireless is now working

---

### Post by xpod on 2007-05-04
> However I did setup a dual boot desktop (XP / Feisty Fawn) in our home office so her and I could learn and experiment together. We are learning something new everyday!!!

That exactly what i`ve done myself this last year of messing about with computers(8 month with Ubuntu):) 

I only ever sat down at that first (win)one to mabey learn the basics & hopefully have some idea what the kids were talking about as they began using the things.:-k 
Discovered Ubuntu a few months later and me & the kids have had a great ole time learning all about the things together.

Like many, my first pc was the commodore64  but that was really the last time i ever really touched a computer until last Spring :) 

Came back at just the right time me thinks:popcorn:

EDIT: stick at it scandall

---

### Post by idcmurali on 2007-05-04
Hey can anyone tell me what is the command to execute a c program in ubuntu 

tried this cc hello.c -o ram.out

did nt work ..please reply

---

### Post by compmodder26 on 2007-05-04
This should not have been posted here.  Please don't hijack other people's threads.

---

### Post by davahmet on 2007-05-04
I see that the problems you are having are with a Compaq Presario V2000, which incidentally is my laptop as well.  However, in my laptop, everything works, and works well.  Now, I can tell you what I've done to get around hardware issues, which really has only been with that cursed Broadcom wireless, but you have to first understand that in Linux, there really is more than one way to do something.  I know it can be frustrating, but when you realize that you aren't locked into someone else's method, and that most Linux people really do want to help as long as you ask, you will definitely enjoy being here.

If it's any help to you, these are the critical steps I took to get Broadcom working on my Presario V2000:
I'm not at my laptop so I'm working from memory here.  In other words, I may be mistaken about file locations but I am sure folks here will quickly correct me.

1.  Copy the Windows driver files for the wireless in the attached .zip file.
2.  Install ndiswrapper with Synaptic
3.  In a terminal run sudo ndiswrapper -i <path to .inf file>
4.  Add the default bcm43xx driver to the blacklist under /etc/modprobe.d/blacklist
5.  Add the line "alias eth1 ndiswrapper" to /etc/modprobe.d/alias
6.  Yes, setting ssid to not broadcast can cause problems.  Enable ssid broadcast on your router at least until your wireless is verified working.
7.  Install wifi-radar form Synaptic
8.  Run wifi-radar to verify your wireless card detects and identifies local wireless networks.

From this point, I don't remember but you may need a reboot.  Regardless, you should have a fully functioning wireless card now.  depending on security settings (WEP or WPA) you may need to do more configurations, but you at least can verify wireless functionality with wifi-radar (or iwlist eth1 scanning from the terminal).

I hope this helps, but if not, we can certainly get you up and running with a bit more troubleshooting.

---

### Post by SrDorothy on 2007-05-04
> **Skandall said:**
> All this talk about how great and easy to use Ubuntu Linux is, I decided to take a chance and install it.  Turns out it's all a bunch of hyperbole.  The installation instructions left out some important information resulting in having to make an educated guess.  What really bakes my noodle is that no matter what I do, it simply will not recognize my built-in wireless modem.  I've tried all of the tutorials.  Still nothing.  It's just not worth the frustration.  I've been through enough thanks to my Sharp Zaurus Linux PDA.  Not to mention that it now takes Windows (which, I should point out, I hate more than you can possibly know; but the laptop was free so I can't complain) forever to load.  So I just want to know what the best way is to safely remove it and the dual boot loader.

Oh, and can someone please explain why does Linux insist on only installing packages from the internet even when you have the package on a local drive?!

I'm just frustrated here because I really want to be rid of Windows and this Linux thing still isn't working for me.  If I had my way, I'd still be using Amiga Workbench.  Oh well.  I appreciate the help.

From an even newer newbie:  I was looking for a way to use wireless networking with Linux and found this--which looks like it has possibilities:  Article on "wireless networking in Linux with NDISwrapper":  [http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167) 

Sorry you're having trouble--I know from experience it can be very aggravating.

Sr. Dorothy

---

### Post by Skandall on 2007-05-05
> **teddybairs1 said:**
> One of the main problems is that the Ubuntu .iso ships with the driver, but without the firmware for legal/licensing reasons. From what I understand, Canonical had talked with Broadcom several times about including it under the GPL and Broadcom is stingy. The driver bcm43xx works. I know it does because my laptop is using it now without incident. But it does need the firmware. Someone here on the site managed to package a .deb with the firmware. I'm uploading it to this post. save it to your desktop, right click on it and select Gdebi package installer. This should install the package for you. For all intents and purposes this should install it for you. If you installed ndiswrapper, completely remove it. Feisty doesn't need it for this card.


Victory for Skandall!!!  I'm posting via Ubuntu which is now connected via my wireless card.  I installed the package from Teddybairs1's post (which kindly reminded me to uninstall ndiswrapper and delete another ndiswrapper file) and logged out then back in, 

Thanks for the help, despite my initial ranting.  In a lot of ways, everyones encouragement and help has reminded me of what I loved about the Amiga and its community.  Not to mention finding so many Amiga users here as well.

Thanks all!

---

### Post by Tux Aubrey on 2007-05-05
Wow.  This thread has been a real loller-coaster.  First Skandall is going back to Windows (or Amiga), then everyone's trying to help him, He's angry, then contrite then relieved all in the course of one thread. Nearly gets one of the Mod Squad taking him out as a troll.  Its been great.  More drama and emotion than Big Brother!  Well done everyone involved.  Skandall certainly earned his seven beans with this one.

---

### Post by Docter on 2007-05-05
To get this good would take SEGA AGES.


LOL

---

### Post by Skandall on 2007-05-05
> **Tux Aubrey said:**
> Wow.  This thread has been a real loller-coaster.  First Skandall is going back to Windows (or Amiga), then everyone's trying to help him, He's angry, then contrite then relieved all in the course of one thread. Nearly gets one of the Mod Squad taking him out as a troll.  Its been great.  More drama and emotion than Big Brother!  Well done everyone involved.  Skandall certainly earned his seven beans with this one.

Thanks!  I didn't get the screen name Skandall for nothing!  Glad to know that I have not only managed to have my problem solved, but also created such quality entertainment for the masses.  I blame my random mood swings on being half English and half Irish.

The End?

Tune in Next Thread...
Same Ubuntu Forum
Same Ubuntu User

---

### Post by freebird54 on 2007-05-05
> I blame my random mood swings on being half English and half Irish.

Now THAT sounds like a realistic scenario!  Back in the day - (my mom had that mix) I recall a guitar disintegrating over my head... and a cuppa arriving (with contents) at high speed.  Horrors? well - I was maybe 13 at the time..... :D

Welcome to the community.  We are not all the same - but mostly we have fun!  And, we get the problems fixed at a superior rate....

---

### Post by lazyart on 2007-05-05
Well now there's a happy ending. :)

---

### Post by Josey on 2007-05-05
congrads

---

### Post by teddybairs1 on 2007-05-05
Skandall, glad it worked. Wish I could claim credit for the package but I don't know how to compile or package worth a darn. I got it from another thread here on the forum from another user generous enough to go through the trouble to make life just a little easier for the rest of us. I'm just spreading the bcm43xx love. :guitar:

---

### Post by caspersghosts on 2007-08-15
I´d say it took me a good year to start having any sort of real understanding about how any of it works. And to make it more complicated, I use ubuntu studio now, for audio production, which is so ridiculously complicated to begin with...

Anyway, of course I still have computer issues now and then, but I´ve basically stopped using windows, even though I have it installed. (It got infected with spyware, and I really haven´t wanted to use it enough to clean it out!)

Some things I´m currently working on:
Getting mozilla to output to my soundcard (actually I´m pretty sure epiphany won´t output to my soundcard either, but obviously it works fine with jack n all)

Fixing my package managers (see my posts about it. seems like its a common enough issue when experimenting with proxy settings, but I haven´t seen a posted solution)

I´d love to learn how to run windows / dos programs in linux.

hmmm, probably a lot more, I just don´t have it in mind;....

anyway, there´s gotta be a way to figure it out.

sudo apt-get yermom

---

