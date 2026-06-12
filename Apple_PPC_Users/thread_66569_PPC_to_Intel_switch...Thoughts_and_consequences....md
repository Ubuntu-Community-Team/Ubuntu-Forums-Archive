---
title: "PPC to Intel switch...Thoughts and consequences..."
date: 2005-09-17
forum: Apple PPC Users
---

### Post by scotty on 2005-09-17
Hi all,

I did a search of this forum and couldn't find anything, so I figured I'd ask...

What's to happen when the Intel chips start living in our new Macintoshes?  I understand that this is not for two more years...But some of us cannot afford new equipment at the drop of a hat.  What's to happen with Ubuntu?  Can we just use x86 discs?  Will PPC development quit?

Thanks,
Scott

---

### Post by zxee on 2005-09-20
[QUOTE=scotty]Hi all,

I did a search of this forum and couldn't find anything, so I figured I'd ask...

What's to happen when the Intel chips start living in our new Macintoshes?  I understand that this is not for two more years...But some of us cannot afford new equipment at the drop of a hat.  What's to happen with Ubuntu?  Can we just use x86 discs?  Will PPC development quit?

Thanks,
Scott[/QUOTE]
 Good topic and there has been discussion of it here-I know because I've posted to it. My 1st thoughts immeadiately after the annoucement were that it's another business move to orphan past models (something apple has a reputation for)
After some reflection and reading what some others have said I think it's a mixed bag i.e some good some bad. I do "mess around with computer innards" put together an athlon computer that I run too many distros on and I also repair older macs-mostly as a hobby, but I'm not an engineer or developer. I do suspect that there will be differences with the intel-apple motherboards otherwise the hardware would be interchangable with pc stuff that's available everywhere, and those motherboard differences will have to be understood in order to enable linux to run on it. That's my opinion anyway. As far as PPC development goes IBM also makes a PPC computer so maybe there will be a continuing of linux for that platform-but it's hard to believe that with apple abandoning PPC that it won't have an effect.

---

### Post by stryder144 on 2005-09-21
I'd say that with the change two things will happen:

1.  Linux/PPC development will continue (DEC Alpha chips haven't been generally available for some time, yet we still see some development for them).  It will probably be quite some time before the current stock of PPC machines starts making it's way to the landfill in such numbers that it would make sense to quit development.  Not to mention, Power3/4 processors will continue to be available for a long time, so it would make sense to continue Linux development for the foreseeable future.

2.  We will see fewer problems when putting Linux on Macs.  The reason is that most of the development is for x86-based computers anyway.  So, this will allow developers to more closely focus attention on making the software better, since they won't have to ensure cross-cpu compatability.  Of course, that will take several years after the switch (meaning that there will still be a high demand for PPC arch compat).

Those are just my opinions/observations.

Cheers

---

### Post by fl1pper on 2005-10-05
That's optimistic, which is a good thing. Unfortunately, there is already very crap[py development happening on the ppc side of the Linux world, and with Jobs' premature announcement of the move to Intel.... the development of ppc is 'deprecated', unless IBM really steps up to the plate, which I hope to God they do. Because Sun, and all the others don't give a rat's ass about the rest of us. So all you guys out there that end up with ppc cell stuff in your gameboxes, install ubuntu, ya hear me? <laughs>

---

### Post by joshuapurcell on 2005-10-05
The idea that Power architecture is depricated is pretty far from the facts, actually. Apple computers were some of the most well-known Power-based computers that individual consumers were able to use, but in the scientific and corporate world the Power architecture is by far the most popular architecture. I just looked into this type of architecture a couple of weeks ago for the first time, and here are some examples that impressed me:
-World's fastest supercomputer: [Blue Gene](http://www.research.ibm.com/bluegene/)
-First supercomputer to beat a human grandmaster chess player: [Deep Blue](http://www.research.ibm.com/deepblue/)
-Advanced space exploration: [Mars Rovers](http://marsrovers.jpl.nasa.gov/home/)
-All three of the future consoles: [Playstation3](http://en.wikipedia.org/wiki/PlayStation_3), [Nintendo Revolution](http://en.wikipedia.org/wiki/Nintendo_Revolution), [Xbox360](http://en.wikipedia.org/wiki/Xbox_360)
-Linux-based virtualization: [Dynamic LPAR](http://www.ibm.com/developerworks/linux/library/l-pow-dynamic/?ca=dgr-lnxw01pa-DynamicLPAR)
-Upcoming motherboards: [Cell Reference Chipset](http://www.vr-zone.com/?i=2733&s=1)
The last item on that list is the one reason I'm planning on having Power architecture in my next home computer. I haven't owned a Power-based machine since the Apple IIGS, and I never really understood what the big deal was about... until I read the details on the architecture in general and the Cell processor specifically. [Here's](http://ubuntuforums.org/showthread.php?t=71609) another post I made on this subject in this same forum that is sorta related to this subject.
The one thing that does suck about Power architecture is that it isn't as accessible as it was now that Apple won't be using it in their future computers. There are other manufacturers of this architecture that are targeting developers and home users though, and I fully expect (and hope) that someone will attempt to fill in where Apple left off. Nearly every serious gamer will have Power architecture in their house by the end of next year (due to the consoles), and the first revision of the Cell processor will actually be in the Playstation 3.
The main reason why the majority of us use x86 at home over Power is because we have all (manufacturers, home users, etc.) followed the popular software that only runs on x86, that was more or less Microsoft software. You haven't seen that as much in corporations and the scientific communities because they had no need to install software that only ran on x86-based systems. Those organizations historically used a UNIX variant, and chose the hardware that was the best performer. Now that Linux has come along and gained popularity, there really isn't any reason for me not to get the type of computer that I think will perform the best... it will run on virtually anything up for consideration. There's a reason why Ubuntu chose to limit their support to only three architectures (Power being one of them), and this limitation seems to be one of the main reasons why Ubuntu exists separate of Debian. Apple wasn't the only thing that Power architecture has going for it.

---

### Post by joshuapurcell on 2005-10-05
[QUOTE=fl1pper]unless IBM really steps up to the plate, which I hope to God they do[/QUOTE]
I forgot to mention that IBM recently released a Power server line that only supports Linux:
[http://openpowerproject.org/us/index.php](http://openpowerproject.org/us/index.php)
[http://www-03.ibm.com/servers/eserver/openpower/](http://www-03.ibm.com/servers/eserver/openpower/)

These are way out of regular people's budget, but it's a start.

Note: The new automatic forum editing that takes out spaces makes longer posts harder to read... sorry about that in my above post.

---

### Post by fl1pper on 2005-10-06
[QUOTE=joshuapurcell]I forgot to mention that IBM recently released a Power server line that only supports Linux:
[http://openpowerproject.org/us/index.php](http://openpowerproject.org/us/index.php)
[http://www-03.ibm.com/servers/eserver/openpower/](http://www-03.ibm.com/servers/eserver/openpower/)

Thanks for responding Joshua. I have to say, being an Apple user since '78, I am not as in need of a sales pitch re: the PowerPC, as might have seemed from my earlier post. :)  That being said, the fact is, there is a lot of software available on the intel side of the ubuntu linux distro, but, example: Blender, great app... then we get to the major plugin, YafRay...oops, Intel/AMD-only.

I wish I was a programmer, because there are a ton of projects on the ppc side that need work: Airport Extreme, Extended Desktop (Monitor2, or whatever they call it in the outside world), the hole audio situation, DVD playback (atrocious) which is completely taken for granted on the Mac platform... some apps in ubuntu will show video (with dropped frames here and there), but no audio (Ogle doesn't even have an audio preference access, WTF?), others are killer on the audio, but play back in slo-mo, or no-mo.

The loading process recognizes an external firewire drive, just fine, but can't "see" the other two internal partitions on my internal drive...(with Linux being an "invisible"-to the Mac- third partition), why? What's the difference between one HFS+ /dev and another? None.

Don't get me wrong, in the ten days since I loaded ubuntu I've only booted into OS X to retrieve my address book as a v-card (seamless merge into Evolution, by the way), and grab a few files, change the permissions on an external drive, etc.

I've worked in several fields, but am "between engagements", currently, so having full Office and Adobe CS installs in OS X and Win2kPro (in VPC) doesn't matter to me right now. Ubuntu is great and runs way faster on the G4 in this Powerbook, than any version of OS X, no question about it. 

As for IBM, yeah, forget the cost of the huge multi core Blades or whatever, IBM isn't in the business of catering to ppc installs of little OpenSource apps and plugins, and I seriously doubt an engineer over there would last in his job if he came out with a suggestion to help out our old buddies on Apple gear.

---

