---
title: "OpenBSD?"
date: 2007-03-11
forum: BSD
---

### Post by billdotson on 2007-03-11
so how does OpenBSD compare to the others.. FreeBSD, NetBSD, etc. apart from having less packages?

---

### Post by Takmadeus on 2007-03-12
werll... AFAIK OpenBSD's goal is security (seems that it has a rock solid policy and is currently on active development) and is pretty stable... NetBSD is all about postability (it means that it even runs on a dreamcast!) and freeBSD is like for the normal user (normal is a relative term by the way :p)

---

### Post by handy on 2007-03-13
& PC-BSD is based on FreeBSD, with the prime intention of being used on the desktop, & to be as easy as possible to do everything!

---

### Post by mips on 2007-03-13
Is there anything based on freebsd 6.2 yet. I have desktopbsd 1.6 RC1 somewhere on my drive. Cant remember what that is based on.

Is there any laymans guide out there to get 6.2 into a fully functional desktop environment ?

---

### Post by handy on 2007-03-13
PC-BSD is based on FreeBSD 6.?, I've asked on the PC-BSD forum which exact version it is currently based on, & also what the policy is on this topic (if there actually is one at this early stage) ?

I'll ask about the guide.

Cheers

---

### Post by mips on 2007-03-13
Based on 6.1. you can update to 6.2 but they wont support you and you should not use the pcbsd updates any longer as it could break things. This according to Tim from irc.

---

### Post by handy on 2007-03-13
Yep, I used the ***uname -a*** command to find the 6.1 thing.

The next PC-BSD release 1.4 will be on FreeBSD 6.2 apparently.

It's due out this year *when it's ready*, is the only time frame we have at the moment.

I'll post here if someone answers your question re: a ***layman's guide*** that I've posted on the PC-BSD forum...  There are users with a lot of BSD experience on the forum, so an answer not PC-BSD specific is quite possible.

---

### Post by mips on 2007-03-13
> **handy said:**
> 
I'll post here if someone answers your question re: a layman's guide that I've posted on the PC-BSD forum...

Thanks handy, much appreciated!

---

### Post by handy on 2007-03-14
Mips, I have a link here for [***KDE on FreeBSD***]("http://freebsd.kde.org/"), it's the best I could come up with so far, I hope it is useful to you...

Cheers

---

### Post by mips on 2007-03-15
handy, thanks!

I had Freebsd 6.2 installed last night and then started adding fluxbox from ports. While doing this I was reading on KDE setup etc and I came to the conclusion to roll your own kde (via ports or pkg_add) and apps is just to much of a hassle for me right now. 

So last night I downloaded the latest PC-BSD iso and I have just finished that installation now. I will just ignore PBI :)

---

### Post by handy on 2007-03-15
The FreeBSD ports are so useful if for no other reason than the sheer number of  them.

I use .pbi's or ports, it doesn't really matter to me.  You seem to have a dislike for .pbi's? :confused:

---

### Post by mips on 2007-03-15
> **handy said:**
> The FreeBSD ports are so useful if for no other reason than the sheer number of  them.

I use .pbi's or ports, it doesn't really matter to me.  You seem to have a dislike for .pbi's? :confused:

Not really but I would prefer to use ports where possible and then pkg_add. This is something I need to learn and that can be transfered to other bsds, not so with .pbi

I also discovered kports which makes the searching and install so much less time consuming.

---

### Post by handy on 2007-03-15
I understand now...

Yes, I use Kports too.

Just a minor fork in the thread here:

Have you been following the [***Haiku***]("http://haiku-os.org/") OS? It looks very interesting to me, I found it via [***Zeta***]("http://www.zeta-os.com/cms/news.php"), which is also interesting but expensive & unstable at this point. There is a bootable Zeta OS CD available on their site, It worked fine for me for hours on the web, allowed me to configure it to suit (english) & all, I did manage to crash it in the end!

It's nice to see that **BeOS** is surviving. :)

---

### Post by billdotson on 2007-03-15
I was following Haiku OS but I just decided to quit caring and just wait until it is released.. from what I hear ~1 year from now.  From what I hear it is pretty much an upgraded BeOS on an open source platform to keep it strong.. as BeOS *died because it was closed source.  Someone was telling me that is Haiku OS accomplishes what it's goal is that we could boot from a dead start into Haiku OS in ~5-10 seconds.  He said it was supposed to be lightning fast and be unlike anything we have seen before.  I do not know though if he is/was a BeOS zealot or not.. or maybe he just follows Haiku OS pretty closely.  Nevertheless I will try it when it is released as it sounds pretty cool.

There is an official BeOS/Zeta/Haiku thread somewhere in the Other OS section of these forums.

I saw the intro to Haiku OS video that was a podcast for it's 5th birthday and it looked really.. boring.  It looked as boring as Windows 95 or 98.  They were showing off the "cool apps" and the apps were like the calendar and the time.  Maybe they just have to actually finish the OS before making software for it..

---

### Post by handy on 2007-03-16
You may enjoy a having a look at the Zeta bootable CD, I found it worth the download, less than 300mb from memory.

Yes, I agree, I won't hold my breath for Haiku, I do look forward to using it though! :)

---

### Post by mips on 2007-03-16
> **handy said:**
> I understand now...

Yes, I use Kports too.

Just a minor fork in the thread here:

Have you been following the [***Haiku***]("http://haiku-os.org/") OS? It looks very interesting to me, I found it via [***Zeta***]("http://www.zeta-os.com/cms/news.php"), which is also interesting but expensive & unstable at this point. There is a bootable Zeta OS CD available on their site, It worked fine for me for hours on the web, allowed me to configure it to suit (english) & all, I did manage to crash it in the end!

It's nice to see that **BeOS** is surviving. :)


I was cleaning out some cd's about a month ago and actually came across my BeOS cd from yonks ago. Was a really cool OS but I have not followed any developments recently.

---

### Post by Sunnz on 2007-04-15
Heh, seems the whole thread turns into FreeBSD(based) OS discussion... but I'll try address the original topic anyway...
> **billdotson said:**
> so how does OpenBSD compare to the others.. FreeBSD, NetBSD, etc. apart from having less packages?

As you may have noticed now FreeBSD (and perhaps PC-BSD) users  prefer use port to compile software from source then use pkd_add if port did not work.

In OpenBSD, it is the other way around. OpenBSD users usually set up a PKG_PATH that points to a ftp OpenBSD packages repository, which is similar to Ubuntu's apt-get repository, and uses pkg_add to install precompiled, binary software.

It is discouraged to use any optimisations to compile software from ports, since OpenBSD dev have already examine the most correct (and thus, the most secure) compiling options for the ports, it is unnecessary to waste CPU cycle that compiles the same binary that is already offered from FTP.

The port still exists, however, since there are few ports that has certain restrictions from distributing the binary. But all the port does is to build a binary package, which is in term used pkg_add to install.

Also, the packages and the ports tree are 'in sync' with OpenBSD versions. E.g. OpenBSD 3.8 has a 3.8 version of ports and packages, instead of the one port fits all approach in FreeBSD.

Other than that, OpenBSD advocates full documentation of device and drivers and dislike blobs. They either go great strength to convince hardware vendors to open their documentation or reverse engineer the blob drivers that may have been compiled for Linux. It is again, tied to the correctness and security approach that's the heart of OpenBSD - should there be a bug in a binary blob, there is no way to debug and fix it, further more, blobs usually have workarounds on top of workarounds on bugs, this contradicts with the correctness approach of OpenBSD and imposes bugs and security vulnerabilities.

BTW, Theo, the founder of OpenBSD, is a bit like Linus to Linux, except that he can be an *** sometimes.

---

### Post by mips on 2007-04-16
> **Sunnz said:**
> 
BTW, Theo, the founder of OpenBSD, is a bit like Linus to Linux, except that he can be an *** sometimes.

Theo is not 'subtle' in any way. Sometimes a 'friendlier' approach towards companies that don't supply information mght be tried initially. He is pretty direct and to the point though, some people might see this as rude.

Overall I appreciate the uncomprimising efforts of Theo and the team towards security and not backing down from their principals.

---

### Post by Sunnz on 2007-04-18
Well here's Theo's take on hardware documentation:
[http://www.openbsd.org/papers/brhard2007/mgp00001.html](http://www.openbsd.org/papers/brhard2007/mgp00001.html)

I think their approach is good and more pressure is needed to the vendors to releaser documentation.

---

### Post by mips on 2007-04-18
> **Sunnz said:**
> Well here's Theo's take on hardware documentation:
[http://www.openbsd.org/papers/brhard2007/mgp00001.html](http://www.openbsd.org/papers/brhard2007/mgp00001.html)

I think their approach is good and more pressure is needed to the vendors to releaser documentation.

Weird that page wont render for in Konqueror or Firefox ? Need any special plugins ?

---

### Post by Sunnz on 2007-04-18
No they are just jpeg... very weird indeed...

Try the index: [http://www.openbsd.org/papers/brhard2007/index.html](http://www.openbsd.org/papers/brhard2007/index.html)

Works here on Firefox and Safari.

---

### Post by mips on 2007-04-18
> **Sunnz said:**
> 
Try the index: [http://www.openbsd.org/papers/brhard2007/index.html](http://www.openbsd.org/papers/brhard2007/index.html)


Now it works just fine :confused: Must be the weather or something...

---

### Post by Th3Professor on 2008-04-17
It is interesting how so many people reply to OpenBSD threads, emails in lists, etc. and completely ignore the subject of OpenBSD and replace it with nothing but FreeBSD discussion.

There are a few of those replies in this thread... it just reminded me of that.

Sunnz:
You said some very useful things regarding OpenBSD.
This might sound backwards but I am a much more experienced user of OpenBSD than (specifically Ubuntu) Linux. It's nice to read someone else's discussion on OpenBSD and only find myself nodding my head and agreeing with everything they say! :)

---

### Post by Sunnz on 2008-04-17
Heh nice timing, I just got the new 4.3-release CD set earlier today!!

I probably has more experience with Linux than OpenBSD, have been using Linux for years before even looking at any BSD's... though I use more OpenBSD than Linux at home these days... just glad that I didn't get any facts wrong!!

But looking back this thread, it is funny that the first response just gives a general description of the 3 BSD's, (leaving out Dragonfly), then the rest went off to discuss PC-BSD!!

So, Th3Professor, are you on misc? Did you see the whole RMS thing? The new song is based on jabbing on RMS and there are more jabs at him on the back of the CD set!! It doesn't even mention FSF... but I think any person who followed 'that' thread on misc knows what it is all about.

---

### Post by Th3Professor on 2008-04-17
> **Sunnz said:**
> Heh nice timing, I just got the new 4.3-release CD set earlier today!!

I probably has more experience with OpenBSD than Linux, though I use more OpenBSD than Linux at home these days... glad that I didn't get any facts wrong!!

But looking back, it is funny that the first response just gives a general description of the 3 BSD's, (leaving out Dragonfly), then the rest went off to discuss PC-BSD!!

So, Th3Professor, are you on misc? Did you see the whole RMS thing? The new song is based on jabbing on RMS and there are more jabs at him on the back of the CD set!! It doesn't even mention FSF... but I think any person who followed 'that' thread on misc knows what it is all about.

Oh man the thread... was... absolute... torture.

Yep, I'm on misc, a very interesting mailing list. I've only sent a few emails to it, basic questions on some random things, long time ago. Usually just read or skim through it. So, regarding that one thread, I just gave up after a while. It went on and on for so long I just resorted with deleting anything on it. But yeah I know what you're talking about.

I love the OpenBSD songs! So much is very successfully summed up in that music. Great themes, great arrangements, and definitely great lyrics. One of my favorites was the Rush song remake, I forget which one it was... but it was awesome in that geeky-cool kind of way. I'm going to have to check out the new one! :) Especially if it has that RMS-jabbing. (I must admit, Richard redefined my opinion of him in what he said (and how he said it) in those emails.)

Yeah I noticed the PC-BSD thing too. Interesting. Actually unexpected, though perhaps there's more of that crowd in here.

---

### Post by PmDematagoda on 2008-04-17
TH3Professor I already told you to make a new thread if you want to talk about OpenBSD, you are not doing this and you are continually resurrecting old threads. Please do not do this again.

This thread is closed.

---

