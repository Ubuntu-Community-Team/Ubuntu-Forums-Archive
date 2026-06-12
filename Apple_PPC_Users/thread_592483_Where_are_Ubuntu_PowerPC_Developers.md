---
title: "Where are Ubuntu PowerPC Developers?"
date: 2007-10-26
forum: Apple PPC Users
---

### Post by Tommy on 2007-10-26
Last month I got added to the Ubuntu PowerPC Architecture team in launchpad, but I'm not a developer -- though I COULD portray one on TV ;-) . I probably requested to be added long ago, but I have no idea where any development discussions occur. There are 70 of us listed in Launchpad, and a dozen "related" bugs, but I haven't seen a place where there's any GENERAL attention given to the release.

While the Apple PPC section of ubuntuforums has been helpful, the topics seem to be discussing various workarounds and tips people have discovered, NOT any active changes to the Ubuntu PowerPC distro. 

I moved my active work to a Pentium box so I can get the critical software updates I need, and I use a PowerBook running Dapper as an X terminal. It would be nice to move PowerPC to newer code! (I would have to buy a newer machine, but they have gotten pretty cheap lately...)

Is there an online forum for active Ubuntu PowerPC development?

---

### Post by nursegirl on 2007-10-26
Have you tried the #ubuntu-powerpc IRC channel? Developer-types seem to greatly prefer IRC over forums.

---

### Post by grazie on 2007-10-26
The question posed in your thread heading is good one, but I don't know the answer. I'm also one the 70 members of the Ubuntu PowerPC Architecture Team. In the past I have done some testing, but I got a little disheartened when Canonical withdrew their support and due to the lack of action on newly reported and outstanding bugs. I also know ssam is reasonably active on the team as well as posting on this forum. I also hang out on #ubuntu-powerpc occasionaly, but to be honest not a lot happens there apart the occasional support type question.

> IMHO the problem goes back to the Debian structure Ubuntu depends upon -- a leadership vacuum developed in the Debian PowerPC community and the problems bubbled downstream into Ubuntu.

There are some really knowledgeable people working actively with Ubuntu (as with Debian) so the "community support" may eventually get it straight. But we need somebody with the right credentials taking some control on behalf of the PowerPC community.
You posted the above on another thread and I thought it was worthy material for starting a new thread, so I'm glad you did.  What you said could be very true...I just don't know. I think it's very important to state that you don't need to be developer (or an aspiring one) to add significantly to the project.

If those of us that what Ubuntu on PPC to continue get ourselves organised (that's the majority of forum users I'd hope) we could improve the releases substantially. As most of the code is platform independent we still get a massive amount from Canonical and the x86 teams (as well as other platform communities) by default.

---

### Post by stmiller on 2007-10-26
Ben Collins was the head guy, though I'm not sure what his involvement is with PowerPC right now.

---

### Post by Tommy on 2007-10-27
Thanks for the responses ... I have written Ben Collins directly, but haven't heard (nor do I necessarily expect to -- he's a busy guy).

For years I have subscribed to the Debian PowerPC list, and the former leaders have been squabbling and departing over the past year or two. Unfortunately the problem has directly affected the quality of Ubuntu's port, because I gather the PowerPC code comes "downstream" into Ubuntu with little attention. IMHO if we had anyone "at the wheel" in Ubuntu PPC, Gutsy PPC would never have been released. (Maybe that's a bit strong, but I think it's a big problem.)

Anyway, A message came through the Debian list recently that has me in a deeper funk -- the Debian maintainers requested ANY existing developers to add their names to the list for re-certification of PowerPC port, and as of this moment, NOBODY has. So the Debian PowerPC port MAY be about to die, which I presume will mean the end of Ubuntu PowerPC.

Here's the page to be updated: [http://wiki.debian.org/powerpcLennyReleaseRecertification](http://wiki.debian.org/powerpcLennyReleaseRecertification)

If no certified Debian developer "signs on," that's the end of the Debian port...

P.S.: someone has added the "popcon" stats -- which is Popularity-Contest, which shows what platforms and what software people are running. Ubuntu PowerPC folks should consider turning it on, though I don't know who collects the Ubuntu stats.It would be nice to see how many folks are using it.

---

### Post by prairie_dad on 2007-10-27
...that's pretty grim...the popcon stats say there are only 600+ Debian PPC users...that's in the world!  While I would like to see this port work, I have to wonder.  I have six or seven G4s, one and two CPUs, 256 meg to 1.5 gig RAM, and while I don't need them all at once, I hate to pitch old hardware that works, for the most part, just fine.  Something about recycling...and these are machines that won't run OS X 10.5, all too slow processors...So Ubuntu seems the way to go.  I like Gentoo fine, I don't find it hard to use, particularly, but setting each machine is slow, what with all the compiling to do.  And I don't see it spreading widely, as Ubuntu has done.  Is there anything to be done?  Do we know the popcon numbers for Ubuntu, or is that what you were after finding out?

---

### Post by Tommy on 2007-10-27
> **prairie_dad said:**
> ...that's pretty grim...the popcon stats say there are only 600+ Debian PPC users....  Do we know the popcon numbers for Ubuntu, or is that what you were after finding out?

Don't put TOO much stock in Popularity-Contest numbers -- I suspect that YOU don't have yours turned on -- it's 100% opt-in. Newer versions of Ubuntu make it easier (it's a tab in the Software Sources dialog), but I bet even still most folks don't turn it on.

(Technically there's a slight exposure to privacy concerns -- not sure how to say it... probably not a huge risk for most folks, but if you're in an authoritarian country and you have a banned package activated it might cause some worry, for example, because there's a possibility of tracking it to a particular IP address.)

I haven't seen whether Ubuntu has done anything to "expose" their stats to the world like Debian does. If anyone knows where to look, please point it here, 

BUT my major points are 

1) PopCon can't tell you much so don't pay much attention to the raw numbers.

2) 600 users logged in PopCon is PLENTY to keep Debian PPC going, but the lack of even one developer is a total killer.

---

### Post by ssam on 2007-10-28
[http://popcon.ubuntu.com/](http://popcon.ubuntu.com/)

enable it in in system->administration -> software sources on the statistics tab.

---

### Post by pxwpxw on 2007-10-28
This is the only platform specific info I could find.
I think 1363/16000 is a very significant ratio of ppc/total.

```

87    linux-image-386                12326     0     0     0 12326 (Ubuntu Kernel Team)            
88    linux-image-686                 2519     0     0     0  2519 (Ubuntu Kernel Team)            
89    linux-image-686-smp               56     0     0     0    56 (Ubuntu Kernel Team)            
90    linux-image-amd64-generic        640     0     0     0   640 (Ubuntu Kernel Team)            
91    linux-image-amd64-k8             241     0     0     0   241 (Ubuntu Kernel Team)            
92    linux-image-amd64-k8-smp           7     0     0     0     7 (Ubuntu Kernel Team)            
93    linux-image-amd64-xeon            27     0     0     0    27 (Ubuntu Kernel Team)            
94    linux-image-k7                  1077     0     0     0  1077 (Ubuntu Kernel Team)            
95    linux-image-k7-smp                 6     0     0     0     6 (Ubuntu Kernel Team)            
96    linux-image-mckinley               2     0     0     0     2 (Ubuntu Kernel Team)            
97    linux-image-powerpc             1345     0     0     0  1345 (Ubuntu Kernel Team)            
98    linux-image-powerpc-smp           18     0     0     0    18 (Ubuntu Kernel Team)            
99    linux-image-sparc64               12     0     0     0    12 (Ubuntu Kernel Team)            
100   linux-image-sparc64-smp            1     0     0     0     1 (Ubuntu Kernel Team)            
101   linux-mckinley                     2     0     0     0     2 (Ubuntu Kernel Team)            
102   linux-sparc64                     10     0     0     0    10 (Ubuntu Kernel Team)     

```

And its 1 more now and I still have around 5 other ppc installs somewhere to popcon, I could fit a few more in if it helps.

I have more problems understanding the debian motivation and selection criteria.

---

### Post by stmiller on 2007-10-28
> **Tommy said:**
> 
If no certified Debian developer "signs on," that's the end of the Debian port...


Well, there is always drama with Debian. One reason I stay away. I would take all of this with a grain of salt.

The main kernel hackers who write most of the PowerPC drivers and other things (snd-aoa, creator of yaboot, etc. etc.) are pretty high up the Linux chain in working with the kernel. Most are either die-hard Debian or Gentoo folks. Ben Herrenschmidt, JoseJX, lots of IBM employees, people working on xen for powerpc, etc. PowerPC is not going anywhere, and is backed by corporate interests to keep it going. (IBM R&D and the POWER arch.) For example, this is a recent note on the kernel list by Ben Herrenschmidt: [http://lkml.org/lkml/2007/10/25/578](http://lkml.org/lkml/2007/10/25/578)

Not to mention Debian supports about 10 different archs out of tradition. To kill off PowerPC would upset the entire Debian mentality- which would not fly with most of the Debian folks. 
Though I'm keenly watching to see how this pans out...

---

