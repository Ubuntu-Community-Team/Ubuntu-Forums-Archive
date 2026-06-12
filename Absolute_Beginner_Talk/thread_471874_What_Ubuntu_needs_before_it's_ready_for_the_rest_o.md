---
title: "What Ubuntu needs before it's ready for the rest of us."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by doobey on 2007-06-12
What Ubuntu needs before it's ready for the rest of us.

**Hardware compatibility.** Without it, install and setup takes so much time, that XP is efficient and easy by comparison. It's the installation and setup that stands between you guys and the world!!!

It took me 15 hours to set-up only to find that my wireless card (it's the last one - [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell) ) probably won't work even if I get the system to recognize it (probably another two hours of work). I almost went for it but when I tried to update the driver for my 915GM chipset (sudo apt-get install xserver-xorg-video-intel)  and it just kept re-installing the driver again and again until I had to re-install Ubuntu again, I decided to drop it.
[B]
Don't get me wrong, I think you guys are doing a great job!!![/B] And, I hope you are successful with this thing. It's just not ready for guys like me. 

[B]My recommendation to the Ubuntu community and Canonical: 
1) [/B]Setp up a hardware database and a quick program that a guy like me can run BEFORE installing Ubuntu that cross checks a newbies computer hardware with the database foretelling of install issues. 
**2) ** Recommend  computer configurations that are currently for sale (at Dell, HP, etc) that that Ubuntu will install  with no issues. This way if I choose to buy a new laptop, I can choose one that will install Ubuntu in one shot!!! That's the way to get converts, hassle free!

Funny thing, back in '98 or '99 I tried to load Linux on a Micron laptop. It took about a week, several hours a night and I finally got it and the gui of the time running, but the gui needed a special script or something for my screen and I finally capitulated at that point. Deja vu.

**Good luck and keep up the great work!!!** 

PS anybody know how I can recover my partitioned disk space for XP?

---

### Post by luckyd on 2007-06-12
I think that the idea of a preinstallation utility to see if hardware is fully compatible is a great one. I just ordered a dell with ubuntu preinstalled, so that I will have complete compatibility, but not every will be willing to buy a new computer just for ubuntu. So, someone should post that as an idea in the Gusty Developement forum...

---

### Post by Najand on 2007-06-12
Boot to Windows, From Control Panel, Reformat the partition to NTFS
Then open MS DOS Prompt and run "fixmbr" command.

---

### Post by Najand on 2007-06-12
> **luckyd said:**
> I think that the idea of a preinstallation utility to see if hardware is fully compatible is a great one. I just ordered a dell with ubuntu preinstalled, so that I will have complete compatibility, but not every will be willing to buy a new computer just for ubuntu. So, someone should post that as an idea in the Gusty Development forum...

Hope they haven't canceled your order as the guys in DELL have canceled many pre-installed ubuntu orders without any notifications during the past few days. Check your order again in Dell.com and ensure if it is ok or not.

---

### Post by kelvin spratt on 2007-06-12
It took me 15 mins to completely install feisty with every thing working as it should so don't generalise that its got major problems some people unfortunately do have problems, the majority have no problems at all

---

### Post by starcraft.man on 2007-06-12
> **doobey said:**
> What Ubuntu needs before it's ready for the rest of us.

**Hardware compatibility.** Without it, install and setup takes so much time, that XP is efficient and easy by comparison. It's the installation and setup that stands between you guys and the world!!!

It took me 15 hours to set-up only to find that my wireless card (it's the last one - [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell) ) probably won't work even if I get the system to recognize it (probably another two hours of work). I almost went for it but when I tried to update the driver for my 915GM chipset (sudo apt-get install xserver-xorg-video-intel)  and it just kept re-installing the driver again and again until I had to re-install Ubuntu again, I decided to drop it.
[B]
Don't get me wrong, I think you guys are doing a great job!!![/B] And, I hope you are successful with this thing. It's just not ready for guys like me. 

[B]My recommendation to the Ubuntu community and Canonical: 
1) [/B]Setp up a hardware database and a quick program that a guy like me can run BEFORE installing Ubuntu that cross checks a newbies computer hardware with the database foretelling of install issues. 
**2) ** Recommend  computer configurations that are currently for sale (at Dell, HP, etc) that that Ubuntu will install  with no issues. This way if I choose to buy a new laptop, I can choose one that will install Ubuntu in one shot!!! That's the way to get converts, hassle free!

Funny thing, back in '98 or '99 I tried to load Linux on a Micron laptop. It took about a week, several hours a night and I finally got it and the gui of the time running, but the gui needed a special script or something for my screen and I finally capitulated at that point. Deja vu.

**Good luck and keep up the great work!!!** 

PS anybody know how I can recover my partitioned disk space for XP?

Just a note on this but like we (I and others) have said before again and again. It's not Ubuntu's fault it doesn't support your hardware. Windows works so well out of the box because all of the companies writes generic/specific drivers for their products, ship them to MS and they are included by default to allow for complete running out of the box. Windows also has majority share with 90% so companies know that they can write one set of drivers for windows and ignore Apple and Linux users and they will still make tonnes of money.

If companies chose to support Ubuntu, then we'd have excellent support. Look at NVidia and ATI for examples of acceptable and not acceptable support respectively.

As for the database idea, it'd never work completely. We already have something [similar here. ]("https://wiki.ubuntu.com/HardwareSupport")It isn't perfectly accurate though, hardware is still kinda a crap shoot.

Anyway, bye, have fun with Windows I guess if your sticking with that. Just remember its the companies who make your hardware you should write to (maybe start a petition), not Ubuntu.

---

### Post by justin whitaker on 2007-06-12
Wireless is one of those things that is hit or miss: some people got it up and running easily, others had to pull teeth. Personally, I never use wireless. I tried getting my sister-in-laws' laptop to run wireless in XP, and frankly, it was down or disconnected randomly more often than not. Give me the cables! 

That does not help you though. Personally, I like the idea of a hardware database, but sure enough, once you post it, someone will say "that doesn't work! you guys suck!". See the WineHQ database, or Transgaming's Cedega database for examples of this.

Also, the database would have to be maintained. Wireless, for example, is one of those things that are a moving target: kernel and driver developers are working to fix things, and the status on any particular card could vary from day to day. 

Here's my suggestion: the latest hardware are probably not the best platforms to run Linux on, since hardware tends to lag a bit behind proprietary OSes. If you do want to run specific hardware, than checking online to see if anyone is running Linux on it successfully is probably your next bet. 

Neither of which helps you right now. ;)

---

### Post by Jimmyfj on 2007-06-12
Your idea about a pre-install-tool that check the hardware WILL come in handy for me too - I'm new to Ubuntu and it would take the heat of the air if I had a tool like that on a live-Cd that would do the job. A tool like that will make the Linux Live-Cd even more priceless that it already is. The tool would also make it even more possible to share Linux. I'd have NO WORRIES about installing Linux for my friends if I knew their hardware was properly tested before installing- Hope that some programmer is reading about your idea and starts working on such a tool. Unfortunately I'm not a programmer otherwise I'd have glowing keys on my keyboard by now. Thank you for the wonderful idea.

---

### Post by Najand on 2007-06-12
You guys can send you ideas to canonical or just post them in launchpad.

---

### Post by lazyart on 2007-06-12
> **doobey said:**
> 
My recommendation to the Ubuntu community and Canonical: 
1) [/B]Setp up a hardware database and a quick program that a guy like me can run BEFORE installing Ubuntu that cross checks a newbies computer hardware with the database foretelling of install issues. 
**2) ** Recommend  computer configurations that are currently for sale (at Dell, HP, etc) that that Ubuntu will install  with no issues. This way if I choose to buy a new laptop, I can choose one that will install Ubuntu in one shot!!! That's the way to get converts, hassle free!


1) LiveCD
2) System76

...next...

---

### Post by smartsaah on 2007-06-12
I agree with Doobey that there should be a systematic checking procedure for the hardware compatibility for Ubuntu. 
But then again, isn't it the responsibility from the manufacturer's side also to make products at par with the carrier of the humane side of the gizmo world i.e Ubuntu?

---

### Post by Najand on 2007-06-12
Well, some manufactures don't give a damn to open source society, especially linux.... I can name some: Lexmark, broadcom, ati, etc.

---

### Post by luckyd on 2007-06-12
What would it say if my order had been canceled?

---

### Post by smartsaah on 2007-06-12
Sure....thats the main reason why we are still bound by the giant corporations to and are compelled to pay money for their stolen or copeid strokes of brilliance!

---

### Post by Najand on 2007-06-12
Check "my order status".
If it is canceled, it would be written there... Well, it doesn't happen to all customers.

---

### Post by luckyd on 2007-06-12
Thank god, it says "in production"

P.S. Why are they canceling orders?

---

### Post by Brightbelt on 2007-06-12
The guys are right about the how owning 90% of the PC market puts drivers into MS's lap. 

But I'll state this again, because these are facts that few people are noticing these days:

Vista and Linux are much more similar in terms of forced hardware compatibility than people think. These days, you have to either buy a computer with Vista pre-installed or cherry pick your brand and/or your hardware. Sound familiar?

Also, Vista has had to wait for a lot of drivers that are lagging behind the market and taking a longer time to arrive. Sound familiar? 

Obviously one is cheaper than the other!! With Vista, you HAVE to move forward in terms of software versions or newly released hardware.  With Linux there is a lot of backwards compatibility, which I think will give it a lot more power in the market than people now realize.

At least, I hope so,...Frank B.

---

### Post by DoricMan on 2007-06-12
As a new Ubuntu 7.04 Feisty Fawn user I would have appreciated knowing what hardware works or could be made to work using something like the Live CD. 
Searching for wireless setup for my Belkin wireless card was surprisingly easy, with the well trodden tips in the Absolute Beginner resource.
My NVida video card is working satisfactorily, again using the Absolute Beginner resource.
My Canon PIXMA iP3000 printer is the last thing to get working, and have found some useful advice using tonight's search.
Having had a lot of useful tips and tricks from the forums, is fine for me, but others may find this a put off. :D

---

### Post by RobN on 2007-06-12
> **starcraft.man said:**
> Just remember its the companies who make your hardware you should write to (maybe start a petition), not Ubuntu.
While technically accurate, you're missing the point.

99% of the users out there don't give a fig who manufactures their hardware -- they don't know, don't want to know, and certainly are not about to go write a letter to anyone to complain about it. As a tech-savvy (though not Linux-savy) user, I understand the issues you raise, and I knew (for the most part) what hardware was in my laptop. I knew exactly what hardware was in my desktop, since I built it myself. But ask my father what's in his PC, and he won't have a clue. My wife doesn't know much about what hardware she's running on that desktop I built, either -- and she's never updated a driver on her own.

No matter what the reality is, if there aren't drivers ready to go out of the box, then people will perceive Linux as being less capable than Windows. Period. I struggled for days to get the wireless on my laptop working reliably -- now it works well, but connects at a fraction of the speed under Ubuntu that it is able to connect at when running XP, with no indication that it will ever improve. The fact that the fault may lie in a lack of vendor-backed drivers rather than the developers of Ubuntu and its supporting applications does nothing to minimize my dissatisfaction with the issue.

I must say that the live CD was a powerful tool for helping evaluate Ubuntu, yet it's somewhat lacking since extensive driver reconfiguration is difficult or impossible to perform.

If the computer is a tool to get things done, then I still find that Ubuntu, while easily the most compelling Linux distribution I've tried so far, is still somewhat lacking. Some of that is Ubuntu's fault, and much of it is not. Yet if I cast aside any philosophical debate and simply go with what works, then I end up with what I'm doing now -- dual-booting into Ubuntu on occaision when I want to play around and tinker, but dual-booting into XP the vast majority of the time when I want to get things done. If I'm going to change my mind on that, I'll need higher-quality drivers and higher-quality applications. Both seem to be improving, but neither is where it needs to be just yet.

---

### Post by Najand on 2007-06-12
> **luckyd said:**
> Thank god, it says "in production"

P.S. Why are they canceling orders?
Good to hear that.
Maybe the numbers of orders was much more than the numbers of computers they have scheduled to sell with ubuntu.

---

### Post by starcraft.man on 2007-06-12
> **RobN said:**
> While technically accurate, you're missing the point.

**99% of the users out there don't give a fig who manufactures their hardware -- they don't know, don't want to know, and certainly are not about to go write a letter to anyone to complain about it. **As a tech-savvy (though not Linux-savy) user, I understand the issues you raise, and I knew (for the most part) what hardware was in my laptop. I knew exactly what hardware was in my desktop, since I built it myself. But ask my father what's in his PC, and he won't have a clue. My wife doesn't know much about what hardware she's running on that desktop I built, either -- and she's never updated a driver on her own.

No matter what the reality is, if there aren't drivers ready to go out of the box, then people will perceive Linux as being less capable than Windows. Period. I struggled for days to get the wireless on my laptop working reliably -- now it works well, but connects at a fraction of the speed under Ubuntu that it is able to connect at when running XP, with no indication that it will ever improve. The fact that the fault may lie in a lack of vendor-backed drivers rather than the developers of Ubuntu and its supporting applications does nothing to minimize my dissatisfaction with the issue.

I must say that the live CD was a powerful tool for helping evaluate Ubuntu, yet it's somewhat lacking since extensive driver reconfiguration is difficult or impossible to perform.

If the computer is a tool to get things done, then I still find that Ubuntu, while easily the most compelling Linux distribution I've tried so far, is still somewhat lacking. Some of that is Ubuntu's fault, and much of it is not. Yet if I cast aside any philosophical debate and simply go with what works, then I end up with what I'm doing now -- dual-booting into Ubuntu on occaision when I want to play around and tinker, but dual-booting into XP the vast majority of the time when I want to get things done. If I'm going to change my mind on that, I'll need higher-quality drivers and higher-quality applications. Both seem to be improving, but neither is where it needs to be just yet.

No I didn't miss any point, you did. I bolded what's wrong.

Companies produce things based on market demand. If the market demands a driver for Vista, thats what they get. Why? Because they need it and DEMAND it, they make sure their company knows their happiness and business rides on that driver being good. If the average consumer does continue to ignore the issue and fail to bring the attention to the companies he/she will continue the cycle of being ignored by large manufacturers and companies.

There are many problems that fail to be addressed in the world because the average person is content to do nothing and ignore it, choosing instead the easier more convenient solution. If you want to get things done, you have to be willing to endure a bit of inconvenience, thus we need to educate those "average consumers" and get them moving.

> **Najand said:**
> Good to hear that.
Maybe the numbers of orders was much more than the numbers of computers they have scheduled to sell with ubuntu.

The dell orders were cancelled recently I believe because they dropped the extended warranty support "accidentally" and then put it back. Thus they cancelled the orders with it when it was dropped.

Anyway, this isn't getting anywhere. Make a new thread in the cafe for discussion... we (I and others) have people to get back to helping...

---

### Post by 13thMonkey on 2007-06-12
One trick, even if you're buying online, is to pop into your local PC store and ask if you can try out a LiveCD on one of their PCs that has whatever hardware it is that you're worried about.

Depending on who you talk to you may get funny looks - either ask to speak to the manager or try again on a different day when a more enlightened salesperson is working. I've done it a couple of times at my local PCWorld. Once I managed to convince them that it wouldn't screw up their shiny Vista display model they were quite receptive to the idea. One guy was so interested that I left him the CD to try at home. :D (As a bonus side-effect I tend not to get any "can we sell you this over-priced piece of junk ma'am" whenever I go in there as they've got used to me now ;))

---

### Post by RobN on 2007-06-12
> **starcraft.man said:**
> Companies produce things based on market demand. If the market demands a driver for Vista, thats what they get. Why? Because they need it and DEMAND it, they make sure their company knows their happiness and business rides on that driver being good. 
My last comment on this thread, then I'll shut up.

If all things were equal, you'd be right. But all things are most definitely not equal. A manufacturer who doesn't release a Vista driver won't sell any product, and they know it. For better or worse, Windows support is as necessary as support for the power grid in the country you're selling your product -- it's literally the lifeblood of the product.

A relatively tiny percentage of people are buying hardware based on whether or not it is compatible with Linux. An overwhelming majority, if they're considering Linux at all, are wondering if it will run on their current hardware. If it doesn't, they simply are not going to complain to a manufacturer of some subcomponent they don't know anything about. **It won't matter whose fault it really is** -- 99% of the time it will be Linux that gets the blame, not the hardware manufacturer. A positive step that may prove me wrong would be the success of Dell's program, mentioned in this thread.

I guess you're right in asking people to complain to the manufacturers. I'm just extremely pessimistic that it will do any good in the short term. It's a cart-and-horse problem -- you won't have enough people complaining to the manufacturers to make them change until Linux is dramatically more popular than it is today, but it won't be dramatically more popular than it is today until it has more widespread hardware support. Sitting on the sidelines I've seen a lot of progress made, but I still agree with the OP that it's not enough just yet.

That said, serious kudos need to go out to all those who have done as much as they have to make it work as well as it does. It's a lot easier to install and use Ubuntu than any previous version of Linux I've tried. There's still room for improvement, and I still don't think it's a viable option for the desktop for most people until those improvements show up, but it keeps getting a lot better.

---

### Post by ajskhan on 2007-06-12
The only thing Ubuntu needs is support and we have it right here. I installed it this morning not expecting it to work at all. It took me a while and a couple CDs but the folks here at Ubuntu Forums - THANKS A LOT!

(and I will continue to post my ongoing stupidity)

---

### Post by stchman on 2007-06-12
> **doobey said:**
> What Ubuntu needs before it's ready for the rest of us.

**Hardware compatibility.** Without it, install and setup takes so much time, that XP is efficient and easy by comparison. It's the installation and setup that stands between you guys and the world!!!

It took me 15 hours to set-up only to find that my wireless card (it's the last one - [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell) ) probably won't work even if I get the system to recognize it (probably another two hours of work). I almost went for it but when I tried to update the driver for my 915GM chipset (sudo apt-get install xserver-xorg-video-intel)  and it just kept re-installing the driver again and again until I had to re-install Ubuntu again, I decided to drop it.
[B]
Don't get me wrong, I think you guys are doing a great job!!![/B] And, I hope you are successful with this thing. It's just not ready for guys like me. 

[B]My recommendation to the Ubuntu community and Canonical: 
1) [/B]Setp up a hardware database and a quick program that a guy like me can run BEFORE installing Ubuntu that cross checks a newbies computer hardware with the database foretelling of install issues. 
**2) ** Recommend  computer configurations that are currently for sale (at Dell, HP, etc) that that Ubuntu will install  with no issues. This way if I choose to buy a new laptop, I can choose one that will install Ubuntu in one shot!!! That's the way to get converts, hassle free!

Funny thing, back in '98 or '99 I tried to load Linux on a Micron laptop. It took about a week, several hours a night and I finally got it and the gui of the time running, but the gui needed a special script or something for my screen and I finally capitulated at that point. Deja vu.

**Good luck and keep up the great work!!!** 

PS anybody know how I can recover my partitioned disk space for XP?

Ubuntu has a hardware compatibility list on their site.  Nothing kept you from going there.

Ubuntu supports far more hardware out of the box than Windows.  If you stick with the mainstream hardware you ususally have no problems.

---

### Post by phr0ze on 2007-06-12
> **RobN said:**
> But ask my father what's in his PC, and he won't have a clue. My wife doesn't know much about what hardware she's running on that desktop I built, either -- and she's never updated a driver on her own.

No matter what the reality is, if there aren't drivers ready to go out of the box, then people will perceive Linux as being less capable than Windows. Period.

I think a few points are missed here. The normal mass market user isn't going to install an OS or a driver. They buy new, call some geeks, or have a friend. PERIOD. Making ubuntu install easy isn't going to do anything for them.

Windows XP on just about any machine these days sucks with drivers. Infact nothing works out of the box other than basic VGA, keyboard, mouse. And if you have a pre-SP2 disk you better hope you don't have any hard drives over 137GB. And have you noticed with XP, most USB devices insist you install (guess what) the driver before plugging it into the computer. But, if you plug it in first you are in a world of hurt. And this is often on USB wireless adapters. So don't tell me XP doesn't have driver issues.

EDIT: BTW, Ubuntu is aware of driver issues and these are improved with every release. They are working on it. It's not like they are ignoring the issue, there just isn't an easy solution.

---

### Post by silkstone on 2007-06-12
Most people don't install XP, Vista, OSX or whatever - it's pre-installed and stays that way. It's a minor miracle that Ubuntu will run on a machine designed for a completely different OS, but run it does in most cases.

I have Edgy on an upgraded four-year-old desktop, and everything worked out of the box. Same with Feisty on a newish dual-core laptop (with Nvidia card). Everything worked including wireless - no tweaking required. Others haven't been so lucky, including quite a few who've tried 'upgrading' to Vista. ;)

---

### Post by doobey on 2007-06-12
> **13thMonkey said:**
> One trick, even if you're buying online, is to pop into your local PC store and ask if you can try out a LiveCD on one of their PCs that has whatever hardware it is that you're worried about.
)

Hmmm, did u install (& partition)? That would be cool.

---

### Post by mikewhatever on 2007-06-12
> My recommendation to the Ubuntu community and Canonical:
1) Setp up a hardware database and a quick program that a guy like me can run BEFORE installing Ubuntu that cross checks a newbies computer hardware with the database foretelling of install issues.
2) Recommend computer configurations that are currently for sale (at Dell, HP, etc) that that Ubuntu will install with no issues. This way if I choose to buy a new laptop, I can choose one that will install Ubuntu in one shot!!! That's the way to get converts, hassle free!


1)This is what the live cd functionality is for.

2) Dell sells computers with Ubuntu preinstalled. Did you know that?

---

### Post by doobey on 2007-06-12
> **mikewhatever said:**
> 1)This is what the live cd functionality is for.

2) Dell sells computers with Ubuntu preinstalled. Did you know that?

LiveCD doesn't allow you to save changes. So you can't reboot after installing the drivers. Besides, one really wants to tinker around for months before deciding to wipe put their old OS.

---

### Post by bodhi.zazen on 2007-06-12
> **doobey said:**
> LiveCD doesn't allow you to save changes. So you can't reboot after installing the drivers.

The Ubuntu CD, no

Other live linux CD's yes.

>  Besides, one really wants to tinker around for months before deciding to wipe put their old OS.

Realistically it takes weeks/months to learn a new OS, windows included.

Also, although not perfect to be sure, Linux runs a wider range of hardware then Windows.

In terms of compatibility, yes it is YOUR responsibility to check compatibility before you buy. True of any OS. If you are a lazy consumer you will suffer the consequences.

---

### Post by doobey on 2007-06-12
> **bodhi.zazen said:**
> 

In terms of compatibility, yes it is YOUR responsibility to check compatibility before you buy. True of any OS. If you are a lazy consumer you will suffer the consequences.

Sure it is always "let the buyer beware." But my original point stands, its not going to be successful in the mass market unless it is easier to setup than windows. That is why it is free, and you still have a hard time *giving* it away. McDonalds has a location philosophy, if the "lazy consumer" has to make more than two turns to park and buy, they ain't coming. 

And the truth is, it's not laziness, its time constraints. In Today's world fast food survives because people don't have the time. My comments were intended to help. And I think a lot of people agreed with them. Ubuntu is not ready for the masses, yet.

Good luck.

---

### Post by durrell on 2007-06-12
This is a good post. Instead of bashing, you made recommendations of how to fix what your problem is. I definitely agree that a hardware compatibility database would be a great thing for new users..the only thing is most truly new users don't even know how to find out what hardware they even have. I think Dell selling computers pre-loaded with Ubuntu is an awesome step for Ubuntu and Linux, I know when I get my laptop for college that is likely to be the one I get.

---

### Post by phr0ze on 2007-06-13
> **doobey said:**
> Sure it is always "let the buyer beware." But my original point stands, its not going to be successful in the mass market unless it is easier to setup than windows. That is why it is free, and you still have a hard time *giving* it away. McDonalds has a location philosophy, if the "lazy consumer" has to make more than two turns to park and buy, they ain't coming. 

And the truth is, it's not laziness, its time constraints. In Today's world fast food survives because people don't have the time. My comments were intended to help. And I think a lot of people agreed with them. Ubuntu is not ready for the masses, yet.

Good luck.

The people you are talking about aren't going to ever use the Live CD, the install, or even the windows setup. They are not going to try linux until they can easily buy it pre-installed. Thats it. Only the people who tinker, who have the desire to start tinkering, or have a linux friend are going to download and try the live CD. 
Do I think the Live CD could be easier? No. 
Could it use more & better drivers? Yes. 
If the live CD was flawless would it get grandma to try it? No.

And there it is. The Live CD will not be tried by grandma, ever. (I'm generalizing by using grandma. I mean the mass market.)

---

