---
title: "BSD, Solaris, OpenSolaris, FreeBSD, OpenBSD, OSX... what's the difference?"
date: 2008-02-28
forum: BSD
---

### Post by the8thstar on 2008-02-28
Alright, alright! I know they HAVE to be different :) and it's likely that some are forks of others. However, I'm looking for an easy way to tell them apart because I want to try one of them on my laptop.

I want something where I can use Gnome, easily triple boot with Ubuntu and Vista, while keeping my /home partition separate and accessible to all three systems.

I want to do what I do with Ubuntu and Windows, which is: surf the net with Firefox as anonymously as possible (by using my wifi card), work on documents with OpenOffice 2.3, StarOffice 8 or MSOffice 2007, do some occasional video editing), benefit from a rock solid kernel and enjoyable speed to enable some nice effects (Aero, Compiz, you know what I mean). I also want to benefit from a wide range of apps like Synaptic offers in Ubuntu.

I have in my machine an Intel Core Solo Intel @1.87GHz, 2Gb of RAM, an Intel 945GM graphics card 128-256Mb and 80Gb of hard disk, currently split b/w Vista (45Gb), Ubuntu (14Gb) and Home (12Gb).

At this point, I've considered trying Solaris Express Developer Edition Desktop or PCBSD... I hope they won't mess up GRUB!

What are your suggestions and ideas? Thanks a lot!
[I]
Edit : I have checked all that I could on Wikipedia,but I'm still wondering in the dark...[/I]

---

### Post by jinx099 on 2008-02-28
> **the8thstar said:**
> Alright, alright! I know they HAVE to be different :) and it's likely that some are forks of others. However, I'm looking for an easy way to tell them apart because I want to try one of them on my laptop.

I want something where I can use Gnome, easily triple boot with Ubuntu and Vista, while keeping my /home partition separate and accessible to all three systems.

I want to do what I do with Ubuntu and Windows, which is: surf the net with Firefox as anonymously as possible (by using my wifi card), work on documents with OpenOffice 2.3, StarOffice 8 or MSOffice 2007, do some occasional video editing), benefit from a rock solid kernel and enjoyable speed to enable some nice effects (Aero, Compiz, you know what I mean). I also want to benefit from a wide range of apps like Synaptic offers in Ubuntu.

I have in my machine an Intel Core Solo Intel @1.87GHz, 2Gb of RAM, an Intel 945GM graphics card 128-256Mb and 80Gb of hard disk, currently split b/w Vista (45Gb), Ubuntu (14Gb) and Home (12Gb).

At this point, I've considered trying Solaris 10 or PCBSD... I hope they won't mess up GRUB!

What are your suggestions and ideas? Thanks a lot!

Well obviously, there is no gnome for OSX, and running OSX on non-mac hardware is probably a violation of their EULA, not to mention  you would probably have driver issues, so thats pretty much out.

I think your best bets would be FreeBSD or OpenSolaris, leaning towards FreeBSD.  The major killer with either of those 2 would be the wifi drivers, so you should try both of them out.  

FreeBSD has a great selection of apps to choose from in their ports collection, including gnome and openoffice.  OpenSolaris will be harder to find a lot of apps you're probably used to in linux, but has most of what you need in the default installation.  It would be really nice if you're a Java developer for sure!

I'm not 100% sure, but I think you can get compiz running on FreeBSD, but not solaris yet.

My recommendation is FreeBSD.  Hope that helps!  :)

---

### Post by 3rdalbum on 2008-02-28
For what you're doing, you'd probably be happy with any of those operating systems except OS X.

---

### Post by smartboyathome on 2008-02-29
> **jinx099 said:**
> Well obviously, there is no gnome for OSX, and running OSX on non-mac hardware is probably a violation of their EULA, not to mention  you would probably have driver issues, so thats pretty much out.

I think your best bets would be FreeBSD or OpenSolaris, leaning towards FreeBSD.  The major killer with either of those 2 would be the wifi drivers, so you should try both of them out.  

FreeBSD has a great selection of apps to choose from in their ports collection, including gnome and openoffice.  OpenSolaris will be harder to find a lot of apps you're probably used to in linux, but has most of what you need in the default installation.  It would be really nice if you're a Java developer for sure!

I'm not 100% sure, but I think you can get compiz running on FreeBSD, but not solaris yet.

My recommendation is FreeBSD.  Hope that helps!  :)

Actually, you can with Macports,  but Darwin is a much better choice in this case (if the drivers have been ported to mac, that is).

---

### Post by igknighted on 2008-02-29
> **jinx099 said:**
> Well obviously, there is no gnome for OSX, and running OSX on non-mac hardware is probably a violation of their EULA, not to mention  you would probably have driver issues, so thats pretty much out.

I think your best bets would be FreeBSD or OpenSolaris, leaning towards FreeBSD.  The major killer with either of those 2 would be the wifi drivers, so you should try both of them out.  

FreeBSD has a great selection of apps to choose from in their ports collection, including gnome and openoffice.  OpenSolaris will be harder to find a lot of apps you're probably used to in linux, but has most of what you need in the default installation.  It would be really nice if you're a Java developer for sure!

I'm not 100% sure, but I think you can get compiz running on FreeBSD, but not solaris yet.

My recommendation is FreeBSD.  Hope that helps!  :)

[http://thermalnoise.wordpress.com/2007/04/21/compiz-on-solaris/](http://thermalnoise.wordpress.com/2007/04/21/compiz-on-solaris/)

Compiz does in fact work on Solaris.  I think Solaris really isn't that far off from being a really good desktop OS option.  As of right now it's usable... barely... but I think that is changing rapidly.

---

### Post by jrusso2 on 2008-02-29
For a laptop your best bet would be PCBSD.  Its more tuned towards desktop use.

Second choice would probably be Solaris. Solaris doesn't have gnome but the Sun Java desktop is based on it

Neither will be as good as Linux on a laptop

---

### Post by SunnyRabbiera on 2008-03-01
Yeh BSD will serve you well as most of it is similar to linux.
BSD is getting there, I am bound to give them another shot in the near future, the issue with flash is almost patched

---

### Post by bwhite82 on 2008-03-01
I gave FreeBSD and Solaris a spin about a month ago. I was able to get both running on my laptop: Dell E1505. FreeBSD ran great, the only thing with it is that you must do a lot of the initial configuration yourself. Although, they have excellent documentation for this purpose.

Solaris was another story altogether. I had headache after headache trying to get a working, usable system. The "community" is nearly non-existent. You can ask for help from the developers but you wont get very far. Driver support is seriously lacking. Be sure to check their compatibility database if you want to plunge into Solaris.

---

### Post by SunnyRabbiera on 2008-03-01
Yeh but solaris is promising, its got a bright future ahead for it from what I see.

---

### Post by init1 on 2008-03-01
BeleniX is OpenSolaris based, and I was quite impressed with their desktop. I think I'll get the newest version now :D

---

### Post by bwhite82 on 2008-03-01
> **SunnyRabbiera said:**
> Yeh but solaris is promising, its got a bright future ahead for it from what I see.

Agreed. But its moving along very slowly IMO.

---

### Post by the8thstar on 2008-03-01
Thank you guys for your timely feedback, as always.

I'll be honest with you: the reason I wanted to try Solaris or any xBSD is because I'm tired of one of my friend telling me that his OSX is true Unix legacy and my Ubuntu Linux is not.

For one, I wanted to show him I can install and run these Unix systems on my laptop just as easily as he can play with OSX on his (way overpriced) Mac. Second, I wanted to know if they are really that different from Linux after all and actually better in everyday use. It may not be the noblest reason, but I basically want to crush my friend's pride and kick it back where it belongs.

Eventually, I don't want to ditch Linux because it's everywhere now and our community at Ubuntu is big and strong; I personally have invested a lot of time and efforts during the past year to learn WHAT Ubuntu is. I love the OS and I love the team.

I can't say the BSD distros and SunOSes have such a powerful community at first glance, although I admit that they're backed up by powerful companies and/or extremely intelligent people.

For the record, I have visited PCBSD website and I ordered the DVD of Solaris Express Developer Edition 1/08 (Sun's free OpenSolaris-based distribution). We'll see how I can fare with that.

Anyway, the discussion goes on and your opinions will be appreciated. :)

---

### Post by K.Mandla on 2008-03-02
Moved to BSD Discussions. Because it's about the BSDs.

---

### Post by Antman on 2008-03-02
> **the8thstar said:**
> 
For the record, I have visited PCBSD website and I ordered the DVD of Solaris Express Developer Edition 1/08 (Sun's free OpenSolaris-based distribution). We'll see how I can fare with that.


I downloaded the Solaris Express DVD last night and I'm installing it on my laptop now. After the initial text mode the installer starts in a GUI mode and seems pretty clean and slick. After it installs, I will play with it for a while to see what it offers.

Ant

---

### Post by scottro on 2008-03-02
Your friend says that Mac is true Unix?  Sigh. 

It runs a userland based on FreeBSD.  You'll find many standard FreeBSD commands missing, however.  (Of course, as I type, I can't think of any, but we had to do something with a user's Mac the other day, and there was some  standard command missing, which annoyed me.  :)  )

BSD is certainly more Unixlike than is LInux, but I don't think I'd say Mac is really BSD.  

Actually, BSD is not entitled to call itself Linux--there were a bunch of legal battles with AT&T back in the late 80's and/or early 90's about this and the code had to be entirely re-written.   Although it is one of the 4 O/S's in the O'Reilly Essential Unix Administration, so is RedHat, which is of course, a LInux.  


EDIT---I wrote "...entitled to call itself Linux..."  I meant Unix, of course.  
p_quarles, that's interesting, I hadn't known that.  Thanks for the info. 

So your friend is on somewhat shaky ground, I think.  I do suspect that a Linux user, skilled with command line, would do a better job at a Solaris or AIX console than would a very skilled, but mostly GUI oriented Mac user.  Don't let it get to you.  :)   Just tell him you'd get a Mac but you dislike being locked in by hardware vendors.

---

### Post by p_quarles on 2008-03-02
Actually Mac OS X 10.5 did achieve official UNIX status, i.e., the right to bear the UNIX trademark. 
[http://en.wikipedia.org/wiki/Single_UNIX_Specification](http://en.wikipedia.org/wiki/Single_UNIX_Specification)

That's not to say that it's any more UNIX-like than SCO, Solaris, or even Linux, but it does meet the UNIX specification.

---

### Post by HuBaghdadi on 2008-03-03
I would really like to try Solaris on my old PC but it requires 750 MB of RAM which I don't have so I'm going to give FreeBSD a shot.
Maybe Solaris suffers from a small community because historically it has been locked on Sun's hardware but things are changing now.

---

### Post by D-EJ915 on 2008-03-03
I wouldn't use Solaris on a laptop, not yet anyway.  But if you have an nvidia motherboard and graphics card it'll be easy as pie getting your desktop setup, lol (solaris runs better on my AMD x64 system than windows does)

Solaris has only been open for like 2 years or so now?  They've come pretty damn far in that time but "update speed" comes with people and it has fewer than FreeBSD and much much fewer than Linux, linux guys are spoiled hehe.

Community edition is the most up-to-date version if you do want to give it a whack.  Just note that the only way to update the core OS is to download the newest version and upgrade from that disc...

---

### Post by djbsteart1 on 2008-03-06
I would go for a BSD, Solaris as people have stated isn't too laptop friendly yet. Personally I would go for PC-BSD as it has a very good packaging system, I feel that it is better than synaptic, but I don't think that it has all of the software that is available in Ubuntu, but there is still easily enough to do.

---

### Post by cammin on 2008-03-07
I like PC-BSD but the amount of PBI packages is so low, that it's not really worth using.
It has a nice installer, and a really professional look to it.
My only other experience with KDE was Kubuntu 7.10 which I've heard wasn't so great. But PC-BSD's KDE was much better.
If you don't like KDE, start off with FreeBSD and add what you want.

---

### Post by djbsteart1 on 2008-03-07
> **cammin said:**
> I like PC-BSD but the amount of PBI packages is so low, that it's not really worth using.
It has a nice installer, and a really professional look to it.
My only other experience with KDE was Kubuntu 7.10 which I've heard wasn't so great. But PC-BSD's KDE was much better.
If you don't like KDE, start off with FreeBSD and add what you want.

This is true about the number of PBI packages, but that will only increase, and until them there is always source. But this is the case with all of the BSD's, if you want a good KDE experience try Mandriv or SUSE, there are many excellent KDE distro's available.

---

### Post by the8thstar on 2008-03-15
Thank you guys for your replies. In addition to your comments, I have read many webpages full of interesting information over the last two weeks, and I downloaded and tried several BSD or BSD-derived flavors: Nexenta Core (OpenSolaris), Solaris 10 SXDE, PC-BSD. At this point, I have to see how I like FreeBSD. As I said before, I am not an IT professional by any means. I'm the average Joe trying a new OS just for the kicks. Therefore don't expect my judgement to be based on solid, hardcore facts, but rather on personal impressions. I started off with virtualization, but due to the fact that Solaris was slooooow under VirtualBox and PC-BSD just wouldn't run (it's a known issue in the knowledge base), I headed off to dual booting with Ubuntu instead. Funny thing, I wiped out my Vista partition in the meantime and it now lives again as a VM in VirtualBox, haha!

Nexenta Core was a breeze to install, but it apparently has NO GUI at all, just a command line. Where is the desktop??? Bummer. Maybe I missed something. Anyway, out of frustration I wiped it off the HD. :( Off to Solaris now... Hmm... Tough cookie! The SXDE install failed repeatedly, so I had to fall back on Solaris 10 Express Install screen eventually. The walkthrough was fairly easy, until I made the wrong choice for the window manager and ended up with a desktop that must a colorblind person's worse nightmare. So... I reinstalled again, this time with Gnome, which was much nicer of course. 

Since I couldn't get my Solaris XFS partition to be found in Ubuntu, I chose to wipe out Solaris altogether. I should say also that Solaris looks like it has potential, but as an end-user, it doesn't do anything different than Ubuntu 7.10. The only noticeable difference I found was that Solaris 10 couldn't get my wifi card to run properly. I haven't closed the door on Solaris yet, but OpenSolaris needs to gain more users and momentum before I can use it. **I was wondering if Project Indiana (Sun's own OpenSolaris) would be a better alternative than Nexenta Core? Has anyone heard of it or tried it?**

Okay, then... At this point, I still have my PC-BSD and FreeBSD .isoes to try. I will have to find a way to get rid of KDE to install Gnome instead (I find KDE ugly as sin) before I can use any of them though. Also, the idea of PC-BSD's PBI package manager sounds nice, but I wonder if I should stick with FreeBSD which looks altogether more mainstream and supported than the former. In comparison to FreeBSD, PC-BSD looks very 'young'. I don't want to go through the effort of installing yet an other OS and end up feeling 'trapped' by design limitations. **Do you have any advice to give in the matter?**

Again, I'm just an end-user and these are MY opinions. Don't feel offended if I don't like the distro you love :)

To extend the debate, I was also wondering about the following topics:

[B]_SWAP: _

1. Can swap partitions be shared between Ubuntu and *BSD. If so, how? 
2. How can I tell Ubuntu not to use my Solaris partition as swap (since it thinks they are the same thing)?

_ext3/*FS PARTITIONS:_

1. Can my /home (ext3) partition in Ubuntu be mounted as such in *BSD? Again, if so, how?
2. How can Ubuntu mount *FS (*BSD/Solaris) partitions? Are they read-only? 
3. Likewise, can my Ubuntu ext3 partitions be mounted and written on by *BSD/Solaris systems?

_OSX and Linux apps:_

1. I read that apps developed for one *BSD can be run on all *BSDs? If true, does it mean that you can run MacOSX software under *BSD?
2. Linux apps are said to run under *BSD, thanks to a compatibility layer. Let's say I want to install Penguin Racer in *BSD. How do I accomplish that?[/B]

---

### Post by D-EJ915 on 2008-03-15
> The SXDE install failed repeatedlyIf you are using the community edition CD the Developer edition part doesn't work.

Swap is swap, should be able to use that between all your OSes.


Linux has experimental UFS support, FFS in BSD is somewhat alike but the implementations are different which is why the support is read-only...

---

### Post by JonUK76 on 2008-03-16
> **the8thstar said:**
> 1. I read that apps developed for one *BSD can be run on all *BSDs? If true, does it mean that you can run MacOSX software under *BSD?


If only :)

No, to the best of my knowledge Mac OSX software will not run on BSD. Mac OSX is built on the open source operating system [Darwin]("http://en.wikipedia.org/wiki/Darwin_(operating_system)") which if I understand correctly can trace its lineage to NextStep and BSD. However Darwin does not include the proprietary elements that make MacOSX what it is (Aqua etc). Therefore MacOSX applications will not run on Darwin (or BSD).

---

### Post by the8thstar on 2008-03-16
> If you are using the community edition CD the Developer edition part doesn't work.

Swap is swap, should be able to use that between all your OSes.

Linux has experimental UFS support, FFS in BSD is somewhat alike but the implementations are different which is why the support is read-only...

Hmm, thanks for the feedback. I guess I can live with these restrictions if:

1. GRUB lets me choose which OS I want to launch
2. FreeBSD can set my /Home partition (ext3) to be its own /Home or equivalent (**HOW DO I DO THAT?**)
3. Should I choose to reinstall Solaris, I must find a way to protect the partition from being mistakenly used by Ubuntu as a swap partition

> If only 

No, to the best of my knowledge Mac OSX software will not run on BSD. Mac OSX is built on the open source operating system Darwin which if I understand correctly can trace its lineage to NextStep and BSD. However Darwin does not include the proprietary elements that make MacOSX what it is (Aqua etc). Therefore MacOSX applications will not run on Darwin (or BSD). 

I was pretty sure but I had to try! :) I wonder if there is some sort of OpenAqua (or OpenApple or OpenMac, or OpenOSX) being worked on out there... Sun did it with OpenSolaris, didn't they? FreeBSD has developed a compatibility layer to run Linux apps, so how about some 'OpenOSX' layer?

Anyway, that was just a thought.

---

### Post by dmitrijledkov on 2008-03-20
Small Comment about Mac OS X. I'm MacBook owner since 2006.

It's great OS X. Loads of eye candy (Aqua, Core Animation, etc.) and they made it standard (Just look at Microsoft Office from Mac all version =D )

But except kernel there is nothing similar to any other *BSD, Linux, Solaris. They pushed their own API's and design guide from bottom-up. For end-user great integration and everything looks&feels native. Great for developers it's a breeze to develop with XCode.

Not so great for FOSS is Linux sence. There is almost everything eg OpenOffice, Firefox, gpg and etc. But there is no X.org, Gnome etc. Plus Mac OS X is a mayor dependency hell in my opinion. If you look at the core libs' they are outdated as hell. I'm talking about python, openssl, apache and etc.

But again it is incredible to see you system boot up in less than 3 seconds because of launch.d.

They decided to take the best out there BSD kernel and NeXTStep at that time and push it to extremes. But they pushed it in proprietary way.

Also you should forget that Apple is hardware vendor. Macs don't have any chips design by apple it's all someone else. They pick out hardware stick on PCB board and use to the full extend from kernel to OS.

On iPod's and iPhone there are some custom IC's but it's not the mayor part. So again it's software and hardware accelerated where it make sence. (H.264/AAC on ipod/iphone).

The best thing they did I believe is it media editing Final Cut Studio and Aperture (iLife as side of this). Just go to their websites to find revalent. And second best thing is Human Design guidelines a believe you should be able to drag the icon from the titlebar of image previewer and drop on the Email application to create a new email with that image attached. I do believe that you should be able to move files to new locations without closing them in the editor app and etc.

My 2 cents. Comments are welcome. I like it a lot but I switched to ubuntu (I have dual boot but never use it now) simply due to Freedom aspect.

ps:

Vendor lockin? You're kidding me. You do get used to the whole userspace quite fast but they do provide 100% drivers to run Windows on macs and Linux kind of gets there similar to all other boxes. If it runs and looks well (whether it's Compiz or Aqua) you are likely to get it again and tell your friends.

DRM? Well that's iPod+iTunes. They are trying to push DRM free music and they have some, but there is far more larger demand for DRM unfortunately. They try to hide it then.

---

### Post by toobuntu on 2008-05-27
OpenSolaris (ka Project Indiana) boots to a beautiful looking GNOME desktop, and looks to have a promising future.

Nexenta Core is just the core OS for now, no GUI.  That will follow, they say.  Until then, they've left the apt repos up from the alpha releases (that did feature full desktops).  See [http://www.nexenta.org/os/FAQ#head-87e98175a6d3f7aa088e1e24916a419e11882854]("http://www.nexenta.org/os/FAQ#head-87e98175a6d3f7aa088e1e24916a419e11882854")for the how-to.

I have a feeling that OpenSolaris will probably take off more than Nexenta did because of Sun's attempts to create a community v. Nexenta's approach to the community.

---

### Post by Kowalski_GT-R on 2008-05-28
> **toobuntu said:**
> OpenSolaris (ka Project Indiana) boots to a beautiful looking GNOME desktop, and looks to have a promising future.



Oh yeah, I've looked at some configuration/desktop screenshots. Indiana seems the Solaris to try...

cheers,

Andre

---

