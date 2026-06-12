---
title: "yellowdog 6"
date: 2008-02-07
forum: Apple PPC Users
---

### Post by ssam on 2008-02-07
yellowdog used to be THE linux distro for powerpc. I used it back in the days before ubuntu.

now that [yellow 6]("http://lists.terrasoftsolutions.com/pipermail/yellowdog-announce/2008-February/000177.html") is out i thought i should have a look. here are some notes. test machine is a ti powerbook G4 1ghz with 768MB ram.

it cost money. download and support for $70, dvd and no support $50 + shipping, there are a few other options 
[http://www.terrasoftsolutions.com/store/index.php?submit=software&submitimg](http://www.terrasoftsolutions.com/store/index.php?submit=software&submitimg)[software][ydl]=1 . There should be free downloads in a month. i paid for the download.

only download option is a dvd image. this uses the redhat anaconda installer (not a live cd). it is fairly simple, a few extra network/firewall questions compared to the ubuntu ubiquity installer. you also have options to customise which packages get installed.

default desktop is enlightenment 0.16 999 040 (E17). it seems like an odd choice to me. it is always billed as being very flashy and fast on slow hardware. the flash stuff is pretty basic, there is a shimmer on the tool bars as you select a window, and the panel icons pulsate on mouse over. dragging windows around is fairly jerky. i've seen E17 do very pretty things on youtube, so maybe it just takes some configuring. also its not very stable, right now my processor is at 100% and its 85% enlightenment. it also sometimes hands on logging out.

also installed is gnome which is a more sensible day to day choice.

package versions
linux 2.6.23-9.ydl6.1 - pretty new. its unfair to expect distros to be shipping 2.6.24 yet
xorg 7.1.1, xorg-server 1.1.1 - same as redhat EL5 and edgy
gnome 2.16.0 - same as redhat EL5,  edgy had 2.16.1 a bit old
openoffice.org 2.0.4 - same as redhat EL5, and edgy
firefox 2.0.0.4 -better hope this has all the security patches backported from 2.0.0.11
gimp 2.2.13 - same as edgy and feisty

(if anyone want to know about any other piece of software just ask)

hardware support seems very good. i did not have to configure anything. i have working wireless (orinoco), sound, video, sleep, cpu frequency scaling, screen brightness keys.

yes thats right sound!!! feisty through hardy can't make sound work for more than a few seconds [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652) on my powerbook. no can recent debian, gentoo or fedora. but in yellowdog it seems to work.

so for anyone with hardware trouble in ubuntu yellowdog may be the answer. as long as you don't mind running old software.

--update
yellowdog has gnash installed by default (claims to be version CVS which could mean anything). its plays the ads on slashdot fine, but can't pay youtube.

---

### Post by oswaldkelso on 2008-02-08
Thanks for that. As ppc users are a dying breed :) it's nice to see reviews of other ppc linux distros. Yellow dog was the first distro I ever tried though not my "cup of tea" due to the fact that at the time it used kde as the default desk-top and I was wanting to use a gnome or at least gtk based disto. I find it interesting that they have switched to E17 I guess you get a performance boost but still a strange choice.
I was suprised you could'nt get your sound working with other distros, I'd have thought that gentoo due to its good ppc support would have managed it even if you needed a little tweeking. 

The point you make about not having the latest and greatest makes me think of the clamour for gutsy which seems a retrograde step on ppc going by the problems on here. With any distro the nearer you get to the edge you get the more the pluses and minuses show up, I guess its down to personel preference at the end of the day.  I wouldn't recommend the latest ubuntu to a new ppc linux user where as I always would have in the past mostly due to the large community (this board) its noobie friendlynes and reasonable documentation.  I suspect that if fedora make then next to release a community distro then it will go the same way, leaving only debian and gentoo as being commited to ppc in any big way, debian because thats what debian is about (supporting lots of arcitectures)  and gentoo as there are a lot of ppc developers running gentoo. I'm not up on suse but they may be in there somewhere .
If the next ubuntu release is a downward step for ppc I can see this community fading, it would be a great pitty if that happened, as may users of other distros use these boards to get linux running on their ppc machines.

---

### Post by VCF on 2008-02-08
I get the feeling that Yellowdog 6 doesn't run in G3's as G3 isn't mentioned anywhere on their site.
Am I right in that assumption?

---

### Post by ssam on 2008-02-09
> **VCF said:**
> I get the feeling that Yellowdog 6 doesn't run in G3's as G3 isn't mentioned anywhere on their site.
Am I right in that assumption?

not sure, you could email them.

i found out why enlightenment was so slow. the yellowdog installer set xorg.conf to use fbdev. i copied my ubuntu xorg.conf to yellow dog and now its smooth.

---

### Post by forceofnature on 2008-02-09
I run Yellowdog 5 on the PS3.  Thanks for letting me know about vesion 6 I am downloading it now.  Maybe wireless support was added to PS3 in this distro.

---

### Post by stmiller on 2008-02-10
Hey Sam that's cool! Thanks for the mini review.

RE: G3 support: Most likely it would work on G3 machines, but seems like they made a cut off for technical support reasons. (Since you are a paying customer.) They have probably only tested on G4 and newer.

---

