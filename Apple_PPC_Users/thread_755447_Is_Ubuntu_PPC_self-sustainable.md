---
title: "Is Ubuntu PPC self-sustainable?"
date: 2008-04-14
forum: Apple PPC Users
---

### Post by stream303 on 2008-04-14
An interesting thread showed up on the Debian port archives about removing ppc architecture, although I think it has more to do with Xara Xtreme, rather than pulling the entire architecture.

So maybe, no need to panic! :)

[http://lists.debian.org/debian-powerpc/2008/04/threads.html](http://lists.debian.org/debian-powerpc/2008/04/threads.html)

But it does raise a question:  How much do we depend on upstream (ie Debian) builds?  If they fail, or if the architecture is just removed, **is Ubuntu PPC self-sustainable with the volunteers we have already?**

Could we support ourselves with our own existing code-base, or would we have to look to another upstream provider, such as Fedora et al, ?

There's no doubt that our hardware won't last forever, and I'd hate to see a port go away, acknowledging that it exists by the graces of volunteers.

I'm not raising the "official" vs "unofficial" support issue here.  That has already been covered for a few years now.

It makes me wonder if Hardy will be the last PPC release, even "UNofficially", and if so I guess that's ok since we can get at least 3 more years out of it, unless upstream code drops, or volunteer dev interest wanes to nothing.

I'd love to see PDP-11 like support like NetBSD does, but maybe that's a bit unrealistic for our ppc's. :)

---

### Post by driven1 on 2008-04-15
I've had my eyes open for a sweet little 12" Powerbook to run Ubuntu. Maybe I should reconsider, but I don't know of anything else that would be a good substitute. Here's to hoping the ppc platform can hang on a bit longer.

---

### Post by oswaldkelso on 2008-04-15
In a word NO
Luckily Debian will probably keep supporting it for a while yet if the length of time they  were supporting 68k macs is anything to go by. I also suspect that ps3 has given ppc a bit of a boost looking at the yellowdog and fedora forums. A large number of posts relate to new ps3 users.  This can only bode well for keeping linux on ppc alive for a few years yet .
I would  think ubuntu on ppc would get one more release after Hardy  but there is a feeling that ubuntu is deviating a little to far from debian and that can only make things hard for  ubuntu ppc given the none rolling release cycle. Taking experimental and changing it every 6 months must be hard to keep it bug free and on time.

I know Mark Shuttleworth  said he saw ubuntu as weaving either side of debian. At the moment  there seems to be a feeling its strayed a bit to far. I hope it gets back on track. After all a successful ubuntu could be good for debian and visa versa.  Given the differing ideals I doubt it it will enough for a community supported ubuntu ppc to survive much longer after Hardy.

Ubuntu wants to replace windows Debian wants to support  many architectures

---

### Post by stream303 on 2008-04-15
I'm going to take a break from Hardy Beta testing and am actually downloading the latest daily image of Lenny-Testing right now, since about a month ago I had troubles with the cdrom on my G5...

[http://www.debian.org/devel/debian-installer/](http://www.debian.org/devel/debian-installer/)

The great thing is that what I learn from either Debian or Ubuntu usually applies to each other for the most part.  Win - Win!

I'll let you know how it goes...

---

### Post by ndlsjk on 2008-04-15
My thoughts would lean toward no, also.

PPC is getting to be pretty old and although it can be used effectively (read: PS3) it only  has a small share of the market when compared to the x86 machines. It isn't a big mystery as to why, with most large computing companies(Microsoft) supporting x86 platforms, the PPC architecture is fairly obsolete/unknown of by most consumers. I would even venture a guess that some Mac users do not know whether they are running a PPC machine or not.

I'm not saying that it is going to die soon. Whether or not the devs keep producing a PPC port, I will keep using Ubuntu (the most recent PPC version) until my little iBook dies. I ran 6.06 up until last week, and with 8.04 I feel like I have a system that could replace my desktop in every regard, except for Flash and Gaming. With 3 years of support on 8.04, I have a feeling that it will outlast this laptop (Which was built in 2002).

Even after the end of the 8.04 support, if this computer is still running, I will continue to use it (given there is no alternative) with Hardy. In fact, I know a few people that are using computers running Windows 98(se) for their office/desktop computer with few problems.

I think, in the grander scheme of things, PPC will die. With it, support for the architecture will die also. Until the number of users reaches a very low number, the developers will continue to release PPC software.

Well, I completely rambled there, but, I do feel that PPC support will die, however I think it will happen in tandem with the inevitable death of the PPC hardware.

Just my 2 cents.

Peace
   Jake

---

### Post by BladeMelbourne on 2008-04-16
PowerPC isn't quite dead yet. With PS3s and IBM's new Power 6 chips, we may be ok for a few more years:

[http://tech.slashdot.org/article.pl?sid=08/04/10/1152205&from=rss]("http://tech.slashdot.org/article.pl?sid=08/04/10/1152205&from=rss")

---

### Post by stream303 on 2008-04-16
I hope so.  I was just thinking along the lines of say our upstream Debian getting royally teed-off at something, and what would happen if they pulled the ppc port - would that also mean the end of the Ubuntu ppc port, or could it continue for at least the lifetime of Hardy?

I guess I shouldn't be thinking such gloomy thoughts.

That being said, I just pulled up Lenny-Testing on my G5 iMac, and so far pretty snappy!  Unfortunately I had to dist-upgrade from Etch to do it - the debian installer froze when recognizing my hardware again...bummer.

---

### Post by Jammy4041 on 2008-04-18
Beware of the POWER PC- it's making a comeback. Not wide scale, comeback, but enough to get a slice of the market share. I think that Linux has to support as many architectures as it can to go forward. (and get a bigger slice of the market share at the same time)

Long Live POWER PC!

---

### Post by stream303 on 2008-04-18
The thing is, have all the distro's diverged so far apart from each other on either technical or political grounds that code-sharing isn't happening?

I guess as an end-user, we'll never know.  I like / use both Debian and Ubuntu and would hope that code sharing is happening so we end-users benefit from the mind-pool.  We'll see....

---

### Post by jdp on 2008-04-19
With every release of OS X more Macs are considered obsolete and can't run current the current release.  That means every couple years more and more PPC Macs are behind a generation OS-wise ad are prime candidates to drop something like Ubuntu on.  I don't really get why an architecture that has limited hardware variants (we know all machines that Apple has released specs-wise) and a growing userbase looking for modern OSs to run on them is being actively pushed to the side by Ubuntu.  Tech support is hard, and I know that, but the Mac platform is a very limited and specific one compared to the PC world.  There's even fewer non-Mac PPC machines out there, too.

---

### Post by stream303 on 2008-04-19
> **jdp said:**
> I don't really get why an architecture that has limited hardware variants (we know all machines that Apple has released specs-wise) and a growing userbase looking for modern OSs to run on them is being actively pushed to the side by Ubuntu.

It's from a commercial standpoint, and I understand their reasoning from that angle.  I don't know how many data centers are running huge loads of ppc iMacs or even xserves, so the commercial support has to come from mainstream architectures.  Fortunately we have unofficial community-based support from users and devs, but that is all volunteer.  Thankfully we have that, as much as we'd like to see it back in mainstream.  They could have pulled the plug on us with Hardy, but it seems that we are good to go.  As much as I love my ppc, and if I was a director, if there was a good time to pull the plug it would have been now.  Thankfully Hardy is available to us.

The good news is that recently a dev caught wind of a major problem in the installer for G5 fans upon initial installation, and is going to fix it in the next Hardy spin, ie 8.04.1.  That might help ease concerns that we are being totally ignored - which isn't the case as long as there are unofficial repos and volunteer devs to get our goods from. :)

Thing is, it isn't the end of the world if ppc support was dropped from Ubuntu - there are many alternatives (Debian, Gentoo, Fedora, et al), so perhaps the value of community support is the driving factor here.

---

