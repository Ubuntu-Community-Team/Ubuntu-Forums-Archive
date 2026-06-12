---
title: "help designing structure of system"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ccfjeff on 2007-06-01
Hi,

Everyone helped me in my effort to verify and burn a copy of Feisty Fawn to CD and all ended up well to this point.  I booted off of the CD and did a little browsing.  The only little glitch was that it set my resolution too high & I could hardly read the menus in order to get that corrected.  I really liked it the little I've played with it so far, but I'll want to be setting it up to my hard drive if things continue to go well (I haven't verified yet that my printer, scanner & fax modem will work.)

I've been reading through the posts here as well as the nice tutorials etc., however, and it looks to me like I ought to make sure of the way I would want to set things up before I get started.  There are a number of options and I would rather get it right the first time, or at least be heading in the right direction before I set it up & then decide I would have preferred a different setup.

My options/needs are probably a little more complicated than most.

I have a small home office (insurance agent/broker/agency) and would also like to set up an older computer or two (or 3) for the rest of my family.  My 4 young children, ages 4 to 10, love to play games on the internet and my wife, an accountant, would like to do some spreadsheets, access her emails and perhaps some files from her office, do a little internet banking and a little browsing on occasion as well.

My brother and I both moved some distance from our old office and each other and decided to split the office and go our separate ways.  I moved my HP 1.3 Ghz PC which is my main machine at the moment to my home and a few older ones as well.  The HP is the only one hooked up at the moment and everyone is fighting for it all the time.  I would certainly prefer to not have others using my computer for security purposes if nothing else.

The 3 older computers were hooked in via a hub (10/100 ethernet hub?) but as I understand it, even the newest of them doesn't quite have the horsepower or the space to run Feisty Fawn.  That one has 96 Meg of memory, and an 8 Gig hard drive.  I believe it is 333 Mhz.  It is running on Win 98 - 1st edition (or whatever they call it).  We got a wireless network thingie, but the 1st edition of Win '98 won't support it, though the 2nd edition would have.  After I saw that Feisty Fawn needed 128 Meg of memory to run I figured [Xubuntu]("http://www.ubuntu.com/products/whatisubuntu/xubuntu") might do the trick.  It will run on 64 Meg of memory, though 128 Meg is recommended.  It does say that “AT LEAST 10 meg of hard drive space is needed”.  I do have a new still in the box hard drive but I'm not sure if it would be best to put it in that box or not.  That's part of the advice I would like to get.

I also have a 90 Mhz Pentium which was upgraded from a 70 Mhz system and probably had been upgraded from a 486 unit.  I would imagine the hard drive is less than 1 Gig and might be as small as 80 MB or so.  I also have at least on 486 unit in the basement, probably two, that had been retired, but still worked.  I'm sure they have even less memory and smaller hard drives.

All were networked peer to peer via Windows '95 &/or '98 & XP on the newer one via ethernet hub.
I believe all or most of them have CD Rom drives.

I'm a novice, but if using some sort of server setup would be the way to go, I would probably be willing to give it a try if it wouldn't be outlandish for a novice to even attempt.

Would it be better to attempt to set one or more of them up on some stripped down Linux as (a) stand alone unit(s) that could just be plugged directly into the internet router?

I saw somewhere on these forums someone mention a very stripped down Linux, [Damn Small Linux]("http://www.damnsmalllinux.org/") which allegedly could run on 486s with as low as 16 Meg of Ram.

Another option to throw into the mix was adding extra video cards to a "standard PC" and hooking additional terminals & keyboards etc. to it to make that PC a little mini-computer with up to 10 terminals as I understand it.  That is advertised as a solution by [Userful]("http://userful.com/?") on the Ubuntu software catalog page.

To complicate things further, I also need to interact with a number of insurance companies at least a few of which won't work with Firefox.  A couple let me do so with IE in a window in Firefox but at least a couple more will only work in IE mode alone.  Almost all are secure sites and several require that I allow them trusted access even in IE.

I also have multi company rating software that runs on the Windows desktop, as well as the legacy Time & Chaos 6, a neat little PIM that I really have come to depend on.  My wife has also gotten a bit ticked at me for tightening the security in IE as she has difficulty at times getting into her email or bank sites etc. unless I come in & fiddle with it to put some of the sites into IE's "trusted zone".

I'm wondering if Wine would work, or some VMWare or Win4Lin might be needed.

As if that weren't enough, there is one more complicating factor.

My main PC, the HP, was a factory refurbished unit that I purchased several years back from PCMall.com.  It did not come with any of the CDs for the software that was pre-installed.  The hard drive crashed and I lost it all.  Yeah, I know I was dumb for not having backups, but the bottom line is that some computer guru put in a new hard drive and reinstalled the software for me.  His company has gone out of business since then, by the way.  Unfortunately, Microsoft has nicely informed me that to protect me they put a "Genuine Advantage" virus on my computer which pops up messages all the time telling me I may have a pirated copy of their software and occasionally opens a webpage telling me to buy a copy of Win XP.

I bring this up because Win4Lin says that you need a valid copy of the software to use their product.  It looks to me like you must even have a non-OEM CD, not just a valid copy on your hard drive.  It would really tick me off if I had to buy another copy of Win XP even though my computer had come from the factory with a valid copy.

So any good ideas from anyone?

---

### Post by Tux Aubrey on 2007-06-01
This is really well beyond me but I'm replying to "bump" your request back up the list :D

You may need to repost in the "Networking" forum.  This is verging on a corporate support request and you may be lucky to find anyone with both the expertise and free time to help.

I do run a small home network through a D-Link router (two wifi enabled laptops and four desktops on the wired lan).  All but one of the machines run Ubuntu.  The other one is a high-end games machine run by my oldest child.  I do have an old P3 on this network and it runs fine with Ubuntu (using fluxbox as the WM to cut down on resource use).  I did upgrade the memory so that it wasn't struggling too much.

I am sure that what you have proposed is quite do-able with Ubuntu, but I have no idea what network protocols you would need - I started and remain with SAMBA because I needed access to the windows machine and some (now redundant) windows partitions on dual-boot machines.  


Good luck.  If you succeed it would make a great "case study"

---

### Post by ccfjeff on 2007-06-01
> **Tux Aubrey said:**
> This is really well beyond me but I'm replying to "bump" your request back up the list :D

You may need to repost in the "Networking" forum.  This is verging on a corporate support request and you may be lucky to find anyone with both the expertise and free time to help.

Thanks, I was wondering if this was beyond the "absolute beginner forum", but I am an "absolute beginner".  That might mean I'm biting off more than I can chew, though.  There are a number of issues in there.

On the other hand, I wasn't necessarily looking for someone to help me all the way through the process at this point, though that would obviously be nice.  I was thinking more along the lines of getting some idea of a broad outline of what might work &/or indications of what just absolutely won't work.

For instance, if the older machines are beyond help it might be a matter of just having to "buck up" and buy at least some newer machines with more ram & HD space.  In my case, unfortunately, my wife would  undoubtedly interpret that as "just live with what you got for now".  But if that is the case, I'd be better knowing the my &/or the hardware/software  limitations upfront and not waste time & effort on trying to make a go-cart viable transportation to work.  or something like that.  ;)

On the other other hand, if there is some clear cut best way to handle that, someone at least pointing me in the right direction could really help me out, make my wife a believer, my kids happy, save some old hardware from going to a landfill and maybe even a nice little case study as you say.  ;)

It seems like it's worth a shot in case someone says "oh yeah, that can be done.  This is how I did a similar setup..."
> 
I do run a small home network through a D-Link router (two wifi enabled laptops and four desktops on the wired lan).  All but one of the machines run Ubuntu.  The other one is a high-end games machine run by my oldest child.  I do have an old P3 on this network and it runs fine with Ubuntu (using fluxbox as the WM to cut down on resource use).  I did upgrade the memory so that it wasn't struggling too much.

That's interesting and sounds like a pretty complicated setup. Are those all on a peer to peer network then, or does one of them act as a server?  Is there a big learning curve on using Fluxbox?  I saw that [Damn Small Linux]("http://www.damnsmalllinux.org/") uses Fluxbox because it is very light on the resources.  I don't mind using command lines or menus if there isn't a huge new vocabulary to memorize, though I don't know if it would be tough for my kids to use.  My wife might balk a little at it as well, but if it makes a computer available they might well go for it.

What I was hoping might be viable would be setting up one of the older computers (ie. the 333 Mhz) as a server, and maybe dropping in the new hard drive and the remote terminals would hardly need any resources.  I used to have an old Wang mini-computer which had hardly any resources even compared to the old 486 machines.  I think the terminals only had 2k of memory.  Yes, that was 2k NOT meg.  That's what that [Userful]("http://userful.com/products/trials") sounds like, though I don't know of anyone who's ever used a setup like that.

> I am sure that what you have proposed is quite do-able with Ubuntu, but I have no idea what network protocols you would need - I started and remain with SAMBA because I needed access to the windows machine and some (now redundant) windows partitions on dual-boot machines.  

I don't believe I've come across "SAMBA" yet, at least not in this context.  I actually use a [Samba]("http://samba.biz/") to get driving records for people who aren't sure how many tickets they have or how old they are.  I'm sure that isn't what you're talking about, though.  Is that some sort of emulator program or something like Win4Lin?

> **Tux Aubrey said:**
> Good luck.  If you succeed it would make a great "case study"

Thanks.  I appreciate the feedback, info and well wishes.  I just hope it doesn't end up as some sort of train wreck case study.  ;)

---

### Post by Tux Aubrey on 2007-06-02
Another bump.

> I just hope it doesn't end up as some sort of train wreck case study. 

That will only happen if you insist on getting advice from me.:D

I am a self taught networker and my teacher is an idiot.  The fact that my home network periodically allows sharing of files and an internet connection is a surprise to me and my family that I can only attribute to the genius of the people behind Ubuntu.  I just plug wires into boxes and tinker till something works.  Concepts such as "server" and peer-to peer" are strangely familiar but not really understood.

I hope that someone can direct you (us) to a tutorial (or even a basic pop-up book) on simple networks.

I am fairly confident you will need the "Alternate Install" iso image for your old machines.  

And Fluxbox does take a bit of learning (it is configured through text files - a bit like those old *.ini files that earlier versions of Windows used).  It really is great once you get it figured out.  There is a a good post about setting it up [[COLOR="Navy"]_**here**_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=371144")

Good luck.

---

### Post by ccfjeff on 2007-06-02
> **Tux Aubrey said:**
> Another bump.

I am a self taught networker and my teacher is an idiot.  The fact that my home network periodically allows sharing of files and an internet connection is a surprise to me and my family that I can only attribute to the genius of the people behind Ubuntu.  I just plug wires into boxes and tinker till something works.  Concepts such as "server" and peer-to peer" are strangely familiar but not really understood.

Thanks.  Hopefully you're only kidding about the "periodically" allows sharing of files & internet connection.

> I hope that someone can direct you (us) to a tutorial (or even a basic pop-up book) on simple networks.

That would be nice.  I did check out a "Networking for Dummies" from the library, but it was pretty old and it was also pretty thick.  Maybe a lot of reading/learning is required.  I'd prefer to skip what I don't need to learn, though.  I seldom use 90% of what I learned in school and I wouldn't doubt if I never need/use a majority of it.  I was hoping that figuring out the best way to structure this might be readily apparent to someone that knew what was needed etc.  Then I could focus on doing what was needed to actually set that up.

> I am fairly confident you will need the "Alternate Install" iso image for your old machines.  

Perhaps so.  I was wondering, though, if the *Damn Small Linux* might be a way to salvage the old 486s to use as terminals if setting up stand alone systems was the way to go.  But maybe the same thing can be accomplished with the "Alternate Install".  As I understand it, both are based on Debian.

If setting it up as a server/client setup is the way to go, however, maybe I wouldn't even need to set up full blown operating systems on any of the terminals and they could operate on a shoestring as far as hardware and software resources go.

> And Fluxbox does take a bit of learning (it is configured through text files - a bit like those old *.ini files that earlier versions of Windows used).  It really is great once you get it figured out.  There is a a good post about setting it up [[COLOR="Navy"]_**here**_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=371144")

Good luck.

Thanks.  That looks like a handy tutorial to bookmark.  Thanks to for the mention on [Samba]("http://us3.samba.org/samba/what_is_samba.html").  That sounds like another very useful program.  I'm kind of surprised I hadn't come across a mention of it earlier, though perhaps I just didn't notice it.

Anyway, thanks again.

BTW, I did [copy the original post]("http://ubuntuforums.org/showthread.php?t=461744") over to the Networking & Wireless Forum but no one has responded yet.  Perhaps I'm asking a bit too much here or am as in over my head as a first year med student wanting some advice on how to do his first brain surgery.  ;)

---

