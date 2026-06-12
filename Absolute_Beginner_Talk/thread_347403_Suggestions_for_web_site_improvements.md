---
title: "Suggestions for web site improvements"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by LukeKendall on 2007-01-27
I realise I'm coming to Ubuntu with a possibly unusual viewpoint, but I have a whole lot of questions which I feel should be covered by the Ubuntu download web site that isn't.  On the Ubuntu site ([www.ubuntu.com)](www.ubuntu.com)), if you go to the download link it offers 6.10 saying:

"Ubuntu 6.10, the newest Ubuntu release: If you would like to benefit from the latest Ubuntu features, this is the release for you"

So, is this a release that tracks unstable packages that could cause you problems?  There's no indication that I could find.  Are you meant to read between the lines and know that "latest features" means "less tested" or even "use at your own risk"?  I couldn't tell.

and it offers 6.06 LTS saying:

"Ubuntu 6.06 LTS, Ubuntu with long-term support: Choose this to benefit from the long support life-cycle of the 6.06 LTS release. This version is supported for 3 years on the desktop and 5 years on servers."

- so what does that mean?  What happens over those 3 years?  Do you get updates?  Is *this* the stable version?  If you get updates, what does "6.06" mean?  What sort of updates are they?  Obviously a Ubuntu 6.06 system that's been updated over 3 years is quite different to one that has never had an update applied.  So in what sense can they both be called "6.06"? 

And which of these (6.06 or 6.10) should I choose?  There's not enough information on the pages to guide me.  I need to know whether one of these is bleeding edge and one is stable.  The site doesn't say: it says one has the latest stuff, the other is "supported"

Note that I'm feeling sensitive to these issues because my 6.06 Ubuntu system was ruined (made totally unbootable) by simply doing "apt-get update; apt-get upgrade" and then rebooting.

CD and DVD images are offered, too, which is nice.  But I couldn't see any information about what's on the DVD.  It's bigger - is that a better thing to download?  You'd think so, but there's no information about how the DVD differs functionally from the CD.  For the CD there's also an "alternate" version, which I gather is what you have to use if you want to set up RAID or LVM during installation.  What about the DVD?  If I use that, can I also choose to setup RAID or LVM?

I also expected a big, obvious link from these forums to the [www.ubuntu.com](www.ubuntu.com) site, and spent five minutes looking for it.  I guessed it would be ubuntu.org, but that's not the site I wanted, so in the end I used google.

---

### Post by PurplePenguin on 2007-01-27
> **LukeKendall said:**
> I also expected a big, obvious link from these forums to the [www.ubuntu.com](www.ubuntu.com) site, and spent five minutes looking for it.  I guessed it would be ubuntu.org, but that's not the site I wanted, so in the end I used google.

It took you five minutes to see that big "Ubuntu" tab right at the top of the screen that takes you directly to ubuntu.com? :confused:

---

### Post by PurplePenguin on 2007-01-27
> **LukeKendall said:**
> Obviously a Ubuntu 6.06 system that's been updated over 3 years is quite different to one that has never had an update applied.  So in what sense can they both be called "6.06"? 

So if you have Windows 98 and apply patches, does it become Windows 99?  Windows 98.1?  I don't quite see what you're saying here, and don't think that many people would be confused, either.

The worst thing would be to overload potential new users with information that they really don't care about.  You seem to want a full explanation as to the version naming scheme, a full list of packages comparing the CD and DVD versions, and so on.  This would be the *worst* thing to do, in my very humble opinion.  People already have a misconception that linux is unnecessarily difficult to use - we don't really want to have pages upon pages full of information and explanations when a simple Download This or That Version link will do. 

Of course, I am looking at this whole situation from a certain perspective, which obviously differs from yours.  Despite the fact that we don't agree, this is a good thing! :)  I'm sure it is very helpful to get a lot of different people to take a look at the same thing (like the ubuntu.com website) and toss in their ideas.  This should include people who are really techy all the way to people who have very little experience with computers (not just linux).  That said, I think they've already done a very clear job, and it seems like any detailed or potentially confusing things should be kept off the main pages.

But that's just my opinion.  Any other takers? :D

---

### Post by az on 2007-01-27
> **LukeKendall said:**
> 
"Ubuntu 6.10, the newest Ubuntu release: If you would like to benefit from the latest Ubuntu features, this is the release for you"

So, is this a release that tracks unstable packages that could cause you problems?  
No.  The unstable version is in development and not released yet.  That page only displayes the released (stable) versions.


> **LukeKendall said:**
> 

and it offers 6.06 LTS saying:

"Ubuntu 6.06 LTS, Ubuntu with long-term support: Choose this to benefit from the long support life-cycle of the 6.06 LTS release. This version is supported for 3 years on the desktop and 5 years on servers."

- so what does that mean?  What happens over those 3 years?  Do you get updates?  Is *this* the stable version?  If you get updates, what does "6.06" mean?  What sort of updates are they?  Obviously a Ubuntu 6.06 system that's been updated over 3 years is quite different to one that has never had an update applied.  So in what sense can they both be called "6.06"? 

LTS is also a stable release but it just has a longer cycle.  For uses where you do not need cutting-edge applications, but something that is solid and will be supported for an abnormally long time for a linux desktop.  Releases are not binary-compatible with one another.  Regardless of what packages you install, whatever is built for 6.06 will run on 6.06.  If a package is built for 6.10, it won't work on 6.06.

You should apply updates.  That's the whole point.  You get a system with up-to-date security patches.

> **LukeKendall said:**
> 
And which of these (6.06 or 6.10) should I choose?  There's not enough information on the pages to guide me.  I need to know whether one of these is bleeding edge and one is stable.  The site doesn't say: it says one has the latest stuff, the other is "supported".

They are both stable.  It depends on your needs.  If you just want a linux box to play with, use 6.10 (Edgy).  If you want a workstation that you will not tinker with, but use for real work, install Dapper (6.06)

> **LukeKendall said:**
> 
Note that I'm feeling sensitive to these issues because my 6.06 Ubuntu system was ruined (made totally unbootable) by simply doing "apt-get update; apt-get upgrade" and then rebooting.

Never mix repositories and stick with installing applications from the archive.  If you do that, you will not have problems.

> **LukeKendall said:**
> CD and DVD images are offered, too, which is nice.  But I couldn't see any information about what's on the DVD.  It's bigger - is that a better thing to download?  You'd think so, but there's no information about how the DVD differs functionally from the CD.  For the CD there's also an "alternate" version, which I gather is what you have to use if you want to set up RAID or LVM during installation.  What about the DVD?  If I use that, can I also choose to setup RAID or LVM?

The DVD has everything in main.  It also has the live session and the alternate installer, AFAIK.  I beleive that the live cd does RAID and LVM just as well as the alternate installer.

---

### Post by LukeKendall on 2007-01-27
> **PurplePenguin said:**
> It took you five minutes to see that big "Ubuntu" tab right at the top of the screen that takes you directly to ubuntu.com? :confused:

Sorry, I clearly don't play enough computer games.  It hadn't occurred to me to hover the mouse over all the objects on the screen to see which ones were links to other areas.  The Home, About, Guidelines, etc. and the Community, Support, Partneres etc, all were pretty obviously links.  I simpky hadn't noticed the concealed link under the big Ubuntu graphic.

luke

---

### Post by LukeKendall on 2007-01-27
> **PurplePenguin said:**
> So if you have Windows 98 and apply patches, does it become Windows 99?  Windows 98.1?  I don't quite see what you're saying here, and don't think that many people would be confused, either.

Fair point.  I guess I'm trying to work out what's the *general* difference between 6.06 and 6.10.  I guess that simply applying upgrades to packages within 6.06 wouldn't turn it into 6.10.  So I'm trying to work out what the general difference is.
> **PurplePenguin said:**
> 
The worst thing would be to overload potential new users with information that they really don't care about.  You seem to want a full explanation as to the version naming scheme, a full list of packages comparing the CD and DVD versions, and so on.   This would be the *worst* thing to do, in my very humble opinion.
I completely agree.  Sorry if I gave the idea I wanted a detail description of the differences.  All I wanted to know was a general idea.  Knowing that one has long term support, and one is the latest, is too little information to be useful, if you stop and think about it for more than a few seconds.  I mean, who wouldn't want the latest?  And if so, why is the choice offered to take 6.06 instead?  There must be some downside to choosing 6.10, in that case.  So, what is the disadvantage?  That's what I want to know: on what basis should I choose between 6.06 and 6.10?
> **PurplePenguin said:**
> 
 People already have a misconception that linux is unnecessarily difficult to use - we don't really want to have pages upon pages full of information and explanations when a simple Download This or That Version link will do. 

Of course, I am looking at this whole situation from a certain perspective, which obviously differs from yours.  Despite the fact that we don't agree, this is a good thing! :)  I'm sure it is very helpful to get a lot of different people to take a look at the same thing (like the ubuntu.com website) and toss in their ideas.  This should include people who are really techy all the way to people who have very little experience with computers (not just linux).  That said, I think they've already done a very clear job, and it seems like any detailed or potentially confusing things should be kept off the main pages.

But that's just my opinion.  Any other takers? :D

I'm suggesting that it needs may two, maybe four more sentences.  I'm certainly not asking for lots more details.  I agree that would be very bad from the usability point of view.

luke

---

### Post by coolen on 2007-01-27
No disadvantage, but 6.06 was an important release because of the extended support. It's going to continue to be supported for the next two years on the desktop, and four for the server, so taking away that choice would pretty much negate that advantage.

---

### Post by aysiu on 2007-01-27
If you really believe there's something wrong with the website, file a bug report on it:
[https://launchpad.net/ubuntu-website/+filebug/+login](https://launchpad.net/ubuntu-website/+filebug/+login)

You can see a list of existing website bugs here:
[https://launchpad.net/ubuntu-website/](https://launchpad.net/ubuntu-website/)

---

### Post by LukeKendall on 2007-01-27
> **azz said:**
> No.  The unstable version is in development and not released yet.  That page only displayes the released (stable) versions.

Well, that would be a good snippet of information to add.

> **azz said:**
> 
LTS is also a stable release but it just has a longer cycle.  For uses where you do not need cutting-edge applications, but something that is solid and will be supported for an abnormally long time for a linux desktop.  Releases are not binary-compatible with one another.  Regardless of what packages you install, whatever is built for 6.06 will run on 6.06.  If a package is built for 6.10, it won't work on 6.06.

I'm still trying to work out what that means.  Do they have the same amount of testing?  Will things that worked in 6.06 work in 6.10?  Do you mean that packages supported in 6.06 might be dropped from 6.10?  I still don't know the answers to any of those questions, even after your helpful explanation.  I think a lot of people (most people?) would not expect packages from a newer release to work in an older release, so if we can take that as a starting point, what information needs to be given to distinguish 6.06 from 6.10?
> **azz said:**
> 
You should apply updates.  That's the whole point.  You get a system with up-to-date security patches.

Yes, I assume that.  But let me guess: to upgrade from 6.06 to 6.10 you'd do a dist-upgrade, but to stay within 6.06 you'd just do an "apt-get upgrade"?  And from what you mention below, if I've added any other repository then when I "apt-get upgrade" I could hose the whole system again?
> **azz said:**
> 
They are both stable.  It depends on your needs.  If you just want a linux box to play with, use 6.10 (Edgy).  If you want a workstation that you will not tinker with, but use for real work, install Dapper (6.06)

Sorry, I don't understand that.  You seem to be saying that you shouldn't trust Edgy for doing real work on.  Why is that?  It would be good to know.  You seem to be saying that Edgy is a toy release, for playing with.  Do you mean that it might break in bad ways, and I shouldn't rely on it?  So given that I've installed Edgy, what do I need to do to protect myself, if I want to use it for real work?  I can't tell from the download page, and I still don't know now.  I *do* think I'm gradually getting a glimmer of understanding.

I'm not trying to be snide, or nasty.  It sounds like the difference between Dapper and Edgy is significant but subtle, so of course it would be hard to distill the difference down into a simple sentence or two.  What I *am* trying to point out is that it would be worth the effort to clarify what the difference is.

> **azz said:**
> 
Never mix repositories and stick with installing applications from the archive.  If you do that, you will not have problems.

That sounds like good advice.  So the various articles in magazines and advice that says "add these other repositories to your apt config files to get access to a bigger range of packages" should come with a hearty disclaimer?  Do you mean that you should *never* add another repository beyond what the install CD sets up for you, if you want to be sure that upgrades won't break everything?  Are there *any* additional repositories that are safe to add?  If there are, how do I find out which repositories are safe or unsafe?

Seriously, I'd like to know: because if another apt-get upgrade breaks my Ubuntu system again, I will absolutely give up on it and shift to another, less fragile, Linux distro.
> **azz said:**
> 
The DVD has everything in main.  It also has the live session and the alternate installer, AFAIK.  I beleive that the live cd does RAID and LVM just as well as the alternate installer.
Ah!  That would be a good thing to know about the DVD version.  Perhaps a sentence could be added to that effect?

Incidentally, I tried downloading the DVD from the US, from Taiwan, and from Sweden.  In each case the downloads simply stopped partway through the process.  From the US, I think it was downloading at about 1kb/sec.  From Taiwan, it stopped after downloading about 39MB.  From Sweden, it stopped after 152MB.  When I tried a wget from Taiwan it stopped after 1kb.  Given that I'm well under my monthly downlaod limit, I don't understand.  Maybe the DVD releases are so popular that the servers can't handle the load? :-)  So I never got a chance to try the DVD.  But that's a minor thing.

luke

---

### Post by LukeKendall on 2007-01-27
> **aysiu said:**
> If you really believe there's something wrong with the website, file a bug report on it:
[https://launchpad.net/ubuntu-website/+filebug/+login](https://launchpad.net/ubuntu-website/+filebug/+login)

You can see a list of existing website bugs here:
[https://launchpad.net/ubuntu-website/](https://launchpad.net/ubuntu-website/)

Thanks, I've now done that.

luke

---

### Post by aysiu on 2007-01-27
In the meantime, until the website does get updated, please keep asking any questions you may have, and we'll try our best to clear things up for you.

---

### Post by aysiu on 2007-01-27
> **LukeKendall said:**
> 
I'm still trying to work out what that means.  Do they have the same amount of testing? No, they don't. 6.06 had eight months of testing, and 6.10 had only four months. > Will things that worked in 6.06 work in 6.10? Theoretically, yes. Actually... most of the time. > Do you mean that packages supported in 6.06 might be dropped from 6.10? In some rare cases, this has happened. Usually when it does, a similar (and probably better) package gets introduced in its place. > I still don't know the answers to any of those questions, even after your helpful explanation.  I think a lot of people (most people?) would not expect packages from a newer release to work in an older release, so if we can take that as a starting point, what information needs to be given to distinguish 6.06 from 6.10? I don't know if I agree with you there. There are a lot of programs, for example, that work only in Windows 2000 or XP and not in Windows 98 or ME. Backwards compatibility is a nice thing, but it doesn't always happen. Ubuntu is a tightly-knit system made up of a lot of dependencies--mixing and matching versions of software can sometimes break that system. Your best bet is to upgrade to a newer version if you want newer packages. > Yes, I assume that.  But let me guess: to upgrade from 6.06 to 6.10 you'd do a dist-upgrade, but to stay within 6.06 you'd just do an "apt-get upgrade"?  And from what you mention below, if I've added any other repository then when I "apt-get upgrade" I could hose the whole system again? If you're using Dapper, all your repositories will have the word *dapper* in them. It won't matter if you do a ```
sudo apt-get upgrade
``` or a ```
sudo apt-get dist-upgrade
``` In fact, I was told at one point that you should always do a ```
sudo apt-get dist-upgrade
``` The latter command won't actually upgrade you to 6.10 unless you change your repositories to have the word *edgy* instead of *dapper*.

> Sorry, I don't understand that.  You seem to be saying that you shouldn't trust Edgy for doing real work on.  Why is that?  It would be good to know.  You seem to be saying that Edgy is a toy release, for playing with.  Do you mean that it might break in bad ways, and I shouldn't rely on it?  So given that I've installed Edgy, what do I need to do to protect myself, if I want to use it for real work?  I can't tell from the download page, and I still don't know now.  I *do* think I'm gradually getting a glimmer of understanding. I don't know why people keep saying this. Edgy works just fine for a lot of people. Most of the problems I've seen (on the forums) with Edgy have to do with the upgrade process, not with a fresh installation of Edgy. Edgy is an official release and a stable one. It just gets a bad rap because it's new. Those of us who have been around know that Dapper got a lot of flak, too, when it was newly released. There were a lot of threads of the "we waited an extra two months for this?!" and "Dapper is *not* stable" variety when Dapper was first released. People like to bag on new releases.

> I'm not trying to be snide, or nasty.  It sounds like the difference between Dapper and Edgy is significant but subtle, so of course it would be hard to distill the difference down into a simple sentence or two.  What I *am* trying to point out is that it would be worth the effort to clarify what the difference is. Edgy is a newer version of Ubuntu, just as Vista is a newer version of Windows and Leopard is a newer version of Mac OS X. Edgy has new features and more up-to-date versions of software.

> That sounds like good advice.  So the various articles in magazines and advice that says "add these other repositories to your apt config files to get access to a bigger range of packages" should come with a hearty disclaimer?  Do you mean that you should *never* add another repository beyond what the install CD sets up for you, if you want to be sure that upgrades won't break everything?  Are there *any* additional repositories that are safe to add?  If there are, how do I find out which repositories are safe or unsafe? I think you're safest (in terms of stability) by using the standard repositories, but you could probably have a fairly stable system by adding other non-standard Ubuntu repositories (Universe, Multiverse, etc.--read more [here](http://www.ubuntu.com/ubuntu/components)). Adding non-Ubuntu repositories can definitely screw up your system. Mixing and matching versions can also screw up your system (having some Edgy repositories and some Dapper ones).

> Seriously, I'd like to know: because if another apt-get upgrade breaks my Ubuntu system again, I will absolutely give up on it and shift to another, less fragile, Linux distro. There are ones you could move to. Debian, for example, is solid as a rock and has a longer release cycle (every few years instead of every six months).

> Incidentally, I tried downloading the DVD from the US, from Taiwan, and from Sweden.  In each case the downloads simply stopped partway through the process.  From the US, I think it was downloading at about 1kb/sec.  From Taiwan, it stopped after downloading about 39MB.  From Sweden, it stopped after 152MB.  When I tried a wget from Taiwan it stopped after 1kb.  Given that I'm well under my monthly downlaod limit, I don't understand.  Maybe the DVD releases are so popular that the servers can't handle the load? :-)  So I never got a chance to try the DVD.  But that's a minor thing. Have you tried downloading via BitTorrent?

---

### Post by e_james on 2007-01-27
A piece of information that most readers will already know. 6.06 means June 2006 and 6.10 means October 2006. What I can't understand is how I bought a cover disc today with 7.04 on it.

---

### Post by StickyStyle on 2007-01-28
> 
*They are both stable. It depends on your needs. If you just want a linux box to play with, use 6.10 (Edgy). If you want a workstation that you will not tinker with, but use for real work, install Dapper (6.06)*
                                 Sorry, I don't understand that. You seem to be saying that you shouldn't trust Edgy for doing real work on. Why is that? It would be good to know. You seem to be saying that Edgy is a toy release, for playing with. Do you mean that it might break in bad ways, and I shouldn't rely on it? So given that I've installed Edgy, what do I need to do to protect myself, if I want to use it for real work? I can't tell from the download page, and I still don't know now. I *do* think I'm gradually getting a glimmer of understanding.
The big point of the LTS version is for corporate users like myself.  With the longer support cycle we have much more time test and plan deployments the LTS versions also have a longer testing cycle before release.  I couldn't care less if my desktop users have the newest shiniest desktop, because they are here to work and they don't need it.  But when I'm at home i like to play with the new stuff and i run whatever the latest stable release is (Edgy 6.10 right now).

Also I think there was a bit of confusion as to what the 'upgrade' process over the support lifecycle is upgrading.  Once a version is released (actually well before it is released) the versions of the applications are 'frozen' meaning that no new versions of each application will be released for that version of ubuntu, what is released over that time is bug fixes and security updates.  I think explaining this clears up the point i was trying to make above.

For example in 2009, people that are running the 6.06 LTS version of ubuntu will still be using GNOME 2.14, even though they did 'apt-get upgrade' every day.  But over that time they will continue to get major bug fixes and security fixes applied.  For most people this could get boring in the fast moving OSS world, that is why there is the every six month release of ubuntu, so they can play with all the new stuff.

---

### Post by Chris Beall on 2007-01-28
> **aysiu said:**
> If you really believe there's something wrong with the website, file a bug report on it:
[https://launchpad.net/ubuntu-website/+filebug/+login](https://launchpad.net/ubuntu-website/+filebug/+login)

You can see a list of existing website bugs here:
[https://launchpad.net/ubuntu-website/](https://launchpad.net/ubuntu-website/)

Great information!  But how on earth did you get it?  Or more to the point, how would I, a newbie who saw a problem with the Ubuntu home page, figure out how to report it (without having stumbled on your post above)?

Chris Beall

---

### Post by aysiu on 2007-01-28
> **Chris Beall said:**
> Great information!  But how on earth did you get it?  Or more to the point, how would I, a newbie who saw a problem with the Ubuntu home page, figure out how to report it (without having stumbled on your post above)?

Chris Beall
Do a Google search for [bug ubuntu website](http://www.google.com/search?hl=en&q=bug+ubuntu+website&btnG=Google+Search). That's what I did.

---

