---
title: "The state of the 64-bit Linux platform"
date: 2011-11-26
forum: Any Other OS
---

### Post by CryptAck on 2011-11-26
Before I begin, I admit that for the last few years I've been far removed from the Linux scene as my technology interests had changed. Nevertheless, the Open Source itch--for the lack of a better term--has rekindled and I am now attempting to catch up on what I've missed. :)

I can recall that 64-bit Linux was not mainstream a few years ago (even though the 64-bit Linux architecture preceded Window's by a year). At the time, the need to address memory above a 4GB limit was not necessary as most computer users' hardware capacities were below the addressing limit. Since then, physical memory capacities have increased substantially and x86 PAE has been used to address the physical capacity limits on 32-bit platforms. 

Although PAE serves as a great workaround I'm wondering: how much investment has been made in Linux 64-bit? 

Developers on Windows have been creating 64-bit applications for some time now, and the Windows 64-bit platform is almost identical to it's 32-bit counterpart. Today, there are only a few reasons not to use 64-bit Windows; I'm wondering if the same is true for Linux.

Thanks!

---

### Post by bluexrider on 2011-11-26
Look at the development of the 64 bit apps in Linux and then ask your question again.

Ubuntu still recommends the 32bit installation unless you are using it as a server appliance.

The long and short of it. Ive had a 64bit processor for years and still run 32bit installation. Why? Because I don't have issues with applications that I want to run.

---

### Post by tartalo on 2011-11-26
[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTQ)

---

### Post by sammiev on 2011-11-26
Been running 64 bit for 1-1/2 years now and after running both I perfer 64 bit. Both run very well but just my choice. :)

---

### Post by Bucky Ball on 2011-11-26
Never run anything else but 64bit on my 64bit machines (since 8.04 LTS). Never had an issue.

---

### Post by haqking on 2011-11-26
x64 for at least 3 years now, never had any issues.

never found an app that doesnt work.

With x64 bit hardware no reason at all to not use x64.

canonical currently defaults to 32 bit download as it will run on anything where as not everyone has x64 bit hardware however as of 12.04 release the default will be x64.

Enjoy

---

### Post by CryptAck on 2011-11-26
Thanks for the replies! I'm very glad to hear that 64 will be the 'default' soon. I was a bit surprised when I downloaded 11.10 that the recommended was still x86.

> **tartalo said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMTQ)

Thanks for the information! :)

---

### Post by LinuxFan999 on 2011-11-26
I believe that users of 64 bit computers should always use a 64 bit OS.
 
My main computer uses an Intel Core 2 Quad processor, which is 64 bit, and runs Windows Vista SP1 x64 (but i think the time for installing Ubuntu on it has come).
 
You should only use a 32 bit Operating system if you are using less than 3.5-4GB of RAM.

---

### Post by wolfen69 on 2011-11-26
64bit here for 2 years and no issues.

---

### Post by SeijiSensei on 2011-11-27
> **CryptAck said:**
> Developers on Windows have been creating 64-bit applications for some time now, and the Windows 64-bit platform is almost identical to it's 32-bit counterpart. Today, there are only a few reasons not to use 64-bit Windows; I'm wondering if the same is true for Linux.

The other day I was [looking for the DLL]("http://ubuntuforums.org/showpost.php?p=11451300&postcount=23") that includes one of the Windows Media codecs.  That DLL, and many more, are only 32-bit and reside in the system32 directory.  It made me wonder how much of Win7 is actually 64-bit, and how much is still 32-bit.

In the case of Linux, since the code is open source, it should be merely a matter of the platform on which it is compiled.  I'd be surprised, though, if all the applications have the hooks required to take advantage of the 64-bit platform.

As far as I can tell, the exhortation to use the 32-bit version is driven by Canonical's desire to avoid problems with installations by naive users.  Like others here, I've been using the 64-bit release for going on two years with nary a problem.

---

### Post by sophia911 on 2011-11-27
The most important reason is there are too few people to use 64-bit linux platform .... 

For now , more and more people join into iOS to earn money .

---

### Post by VeeDubb on 2011-11-27
Already a lot of folks saying more or less the same thing, but I'll throw in my $0.02

I've been using 64bit for a couple of years now, and I can honestly say that I wouldn't even consider installing 32-bit unless I was dealing with an older machine that wasn't capable of running 64-bit.  Of course, if I was installing on a system that old, I wouldn't be using main line Ubuntu anyway.  I'd run a lighter weight variant.

One of the VERY few advantages to 32bit is that the 32bit flashplayer is more mature.  However, HTML5 and other technologies really are starting to replace flash, and 64bit flash is very very close at this point anyway.  Adding the sevenmachines ppa for 64bit flash eliminates 99% of flash problems, not counting those created by people trying to follow old tutorials and how-to's.

---

### Post by jorok_tupur on 2011-11-27
I use the 64-bit version, and the only problem I encountered was not caused by software in Ubuntu's official repository.

I tried installing Oracle XE 10g Debian i386 package into my Ubuntu system, and ... well ... I learned that installing packages that were made for other distro (Debian package into Ubuntu system) and other architecture (i386 package into x86-64 system) is poor decision.

Instead, I should have installed Debian as guest OS into VirtualBox, installed the DBMS there, and connect the host and the guest OS via VirtualBox's network or whatever it is called. (haven't tried this, though)

Other than that, there's no difference with i386 system (for me anyway).

The state of the 64-bit platform? I think this can be described as: no significant problem, yet. Maybe in the future, where 64-bit is not enough anymore...

---

### Post by CryptAck on 2011-11-27
> **SeijiSensei said:**
> The other day I was [looking for the DLL]("http://ubuntuforums.org/showpost.php?p=11451300&postcount=23") that includes one of the Windows Media codecs.  That DLL, and many more, are only 32-bit and reside in the system32 directory.  It made me wonder how much of Win7 is actually 64-bit, and how much is still 32-bit.

Yes, this is very true. WoW64 provides the capability for Windows32 to run on top of a 64-bit architecture. Because of this, many of the older/current applications are still 32-bit. Even the default Internet Explorer is still 32-bit on many Windows 7 desktops (although a 64-bit option is available).

---

### Post by oldos2er on 2011-11-27
> **LinuxFan999 said:**
> You should only use a 32 bit Operating system if you are using less than 3.5-4GB of RAM.

64-bit Ubuntu runs perfectly on 2GB RAM.

> **bluexrider said:**
> Ubuntu still recommends the 32bit installation unless you are using it as a server appliance.

This is finally going to change in 12.04 (long overdue in my opinion) [http://www.techdrivein.com/2011/11/6-key-changes-in-next-ubuntu-1204_12.html](http://www.techdrivein.com/2011/11/6-key-changes-in-next-ubuntu-1204_12.html)

---

### Post by wolfen69 on 2011-11-28
> **oldos2er said:**
> 64-bit Ubuntu runs perfectly on 2GB RAM.


It runs even better with 8gb ram. ;)

---

### Post by Bucky Ball on 2011-11-28
> **LinuxFan999 said:**
> I believe that users of 64 bit computers should always use a 64 bit OS.
 
My main computer uses an Intel Core 2 Quad processor, which is 64 bit, and runs Windows Vista SP1 x64 (but i think the time for installing Ubuntu on it has come).
 
You should only use a 32 bit Operating system if you are using less than 3.5-4GB of RAM.

First bit; yes. Second bit; that would make your quad core theoretically 128Bit? No matter. Third bit; nothing to do with installed RAM. This is about the processor. ;)

---

### Post by BrokenKingpin on 2011-11-28
I have been using 64-bit Linux on all my machines for years with no issues. If you have a 64-bit CPU, you should be using a 64-bit OS... it is that simple.

For the next Ubuntu release the 64-bit will be the recommended version. It is as stable as the 32-bit version without a doubt.

---

### Post by hg21 on 2011-11-28
I've used 64 bit for several years without problem BUT last week I got Musescore from the repository and it was the most unstable linux software I've ever seen - crashes every few minutes and some aspects did not work at all.

I installed 32bit (Kubuntu) on a spare partition and Musescore behaved perfectly.

Best wishes,
Howard

---

### Post by haqking on 2011-11-28
> **hg21 said:**
> I've used 64 bit for several years without problem BUT last week I got Musescore from the repository and it was the most unstable linux software I've ever seen - crashes every few minutes and some aspects did not work at all.

I installed 32bit (Kubuntu) on a spare partition and Musescore behaved perfectly.

Best wishes,
Howard

From [http://musescore.org/en/download](http://musescore.org/en/download)

> There are ready-to-install packages for Ubuntu in the "universe" repository. **The packages provided are often older versions than the current stable version**

Try a stable version from the webpage or backports (not supported by Ubuntu Developers however).

Cheers

---

### Post by Dlambert on 2011-11-29
If i know I have 64 bit hardware, I will NOT run anything but 64 bit.

---

### Post by OrangeCrate on 2011-11-29
I've run 64-bit Lucid at the office since the day it was released, and currently, I'm running 64-bit Oneiric at home. 4GB of memory on both machines. On the home computer, I've also tried several other 64-bit distros. I've never had a problem with any of them. I agree with the others here, that if your hardware is 64-bit, there's no reason not to run 64-bit operating systems.

Edit:

Jaunty was my first serious 64-bit install, and I do have to admit, that it left some things to be desired - particularly random flash freezes. But, since the Lucid install, everything has worked just fine.

---

### Post by S2UIRR3L on 2011-11-29
First off... I'm a HUGE fan of Jaunty 32-bit. I still use Jaunty on all my computers. Why haven't I upgraded? Well... I tried a few live discs and didn't care for them. Jaunty works so flawlessly, that I keep telling my self "If it ain't broken, why fix it?" Sure, I know there's a million security issues and everyone wants me to move on to the newest flavor, but I'll wait a little for everyone to work out the bugs, then I'll consider it.

MY MAIN QUESTION

I just got a computer from a friend. It's a tiny little Gateway (about the size of a telephone book). It came pre-installed with Windows-7 Home Premium 64-bit OS. It has an Intel Pentium G6951, Intel GMA HD Graphics and 6-GB of DDR3 RAM. Windows-7 got corrupted and the hard drive got fried. He didn't have any restore discs and lost his activation number. So he gave the tower to me and bought a new one. I put a new hard drive in it and now I'm confused...

Should I go Ubuntu 32-bit...?
Should I go Ubuntu 64-bit...?

CAN I go 32-bit on a system that can handle 64-bit jobs or, SHOULD i go with the 64-bit BECAUSE it's a 64-bit system? I'm not a hard core gamer and don't do a lot of stuff. My main use for a computer is Facebooking, eBaying, emailing, and once in a while I'll check out my friends' videos on YouTube. Nothing serious and I'm far FAR far from being a programmer lol. I'd like to stay with Jaunty, but if I must, I'll download a copy of the newest 11.04 (is that the newest LTS?).

As always, thanks a million for all the help and the support.
-Leo

---

### Post by OrangeCrate on 2011-11-29
> **S2UIRR3L said:**
> First off... I'm a HUGE fan of Jaunty 32-bit. I still use Jaunty on all my computers. Why haven't I upgraded? Well... I tried a few live discs and didn't care for them. **Jaunty works so flawlessly, that I keep telling my self "If it ain't broken, why fix it?" Sure, I know there's a million security issues and everyone wants me to move on to the newest flavor, but I'll wait a little for everyone to work out the bugs, then I'll consider it.**

MY MAIN QUESTION

I just got a computer from a friend. It's a tiny little Gateway (about the size of a telephone book). It came pre-installed with Windows-7 Home Premium 64-bit OS. It has an Intel Pentium G6951, Intel GMA HD Graphics and 6-GB of DDR3 RAM. Windows-7 got corrupted and the hard drive got fried. He didn't have any restore discs and lost his activation number. So he gave the tower to me and bought a new one. I put a new hard drive in it and now I'm confused...

Should I go Ubuntu 32-bit...?
Should I go Ubuntu 64-bit...?

**CAN I go 32-bit on a system that can handle 64-bit jobs or, SHOULD i go with the 64-bit BECAUSE it's a 64-bit system?** I'm not a hard core gamer and don't do a lot of stuff. My main use for a computer is Facebooking, eBaying, emailing, and once in a while I'll check out my friends' videos on YouTube. Nothing serious and I'm far FAR far from being a programmer lol. I'd like to stay with Jaunty, but if I must, I'll download a copy of the newest 11.04 (is that the newest LTS?).

As always, thanks a million for all the help and the support.
-Leo

It's totally up to you, you can go either way. Just remember, that you can install a 32-bit operating system on a 64-bit computer, but, not the other way around. Though I don't, there are a lot of people who prefer 32-bit over 64-bit systems on 64-bit hardware - there's actually one guy here in this thread - see post #2.

Edit:

You really should upgrade. How about to the next LTS version from Jaunty, which is 10.04? As I posted earlier in this thread, I run that version in the office. At least for me, it's rock solid.

[https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html)

---

### Post by S2UIRR3L on 2011-11-29
Okay cool...
I already have a Jaunty 32-bit disc, as well as a USB ISO.
But if I wanted to try the 64-bit, which one would I download?

This is the site that I go to for downloading a copy of Jaunty:
[http://old-releases.ubuntu.com/releases/9.04/](http://old-releases.ubuntu.com/releases/9.04/)

Even tho my computer is an Intel Pentium G6951, would the
AMD64-bit work on it... or is that TOTALLY WRONG lol...?
I believe it's a Dual Core... but I don't know for certain...?

-Leo

---

### Post by OrangeCrate on 2011-11-29
> **S2UIRR3L said:**
> Okay cool...
I already have a **Jaunty** 32-bit disc, as well as a USB ISO.
But if I wanted to try the 64-bit, which one would I download?

This is the site that I go to for downloading a copy of **Jaunty**:
[http://old-releases.ubuntu.com/releases/9.04/](http://old-releases.ubuntu.com/releases/9.04/)

Even tho my computer is an Intel Pentium G6951, would the
AMD64-bit work on it... or is that TOTALLY WRONG lol

-Leo

Please be sure to read my "Edit". I was adding info the same time you posted.

---

### Post by S2UIRR3L on 2011-11-29
I just read it... I think you're right... I'll just download a new copy of 10.04 (maybe 11.04 if I'm feeling bold at the time). and just stick with the 32-bit system. Even tho my computer can handle 64-bit processing, there's nothing wrong with using 32-bit Linux still.

THANK YOU FOR THE HELP
IT'S MUCH APPRECIATED!!!!!

You're one of the many reasons these forums are so helpful.

-Leo

---

### Post by OrangeCrate on 2011-11-29
^,

You're welcome, and good luck...

:)

---

### Post by S2UIRR3L on 2011-12-01
Okay - Just tried the Jaunty 32-bit live USB and it was REALLY slow.
I poked around and what not... In the system info thing, it says that I
have two Intel processors @ 2.8-Ghz each (guessing it's dual core).
The memory registers as being 5.9-Gigs of DDR-3 RAM installed...

I'm going to download and try a Lucid 10.04 LTS (AMD-64-bit) CD.
I'm wondering if the Jaunty-32 runs slow because the tower is 64?
I'm hoping Lucid-64-bit will run quicker because it's 64-bit on 64-bit.

Any thoughts on why Jaunty-32 worked GREAT on a Sony Vaio-64?
Same situation with my uncle's Sony Vaio... Came with Vista 64-bit,
it got corrupted... I formatted and installed Jaunty-32, works flawless.

EDIT - I forgot to mention that his computer only had 2-Gigs or RAM.

-Leo

---

### Post by Bucky Ball on 2011-12-02
Always going be slower from a CD (or a Wubi install for that matter).

---

### Post by S2UIRR3L on 2011-12-03
OMG - Lucid Lynx 64 CD is so much faster than Jaunty Jackalope 32 on USB!
I've installed it on my computer and it's the best thing EVERRRRRRRRRR!!!!!!!!!

As for now, my laptop will stay with Jaunty-32 because it just works fantastic...
But my desktop is Licid-64 and I couldn't be happier with it... It's REALLY fast!!!

Thanks to everyone who suggested I go Lucid - I've been proven wrong and
I thank you because it's been such a positive wrong ha ha ha - I love you all!

-Leo

---

### Post by screaminj3sus on 2011-12-04
There's really no reason not to use 64 bit linux if your machine is capable (if you have a low amount of memory I'd stick with 32 bit, because 64 bit will use more memory)

My only issue with 64 bit linux has only even been flash, and now we have a stable 64 bit flash release that works great :)

---

### Post by S2UIRR3L on 2011-12-04
With the Jaunty-32 and a 512-Mb of RAM on my P-4 laptop, flash is not too bad. Very slightly choppy in full screen, but not horrible.

With the Lucid-64 and 6-Gigs of RAM on an Intel Dual Core, flash will play in full screen without breaking a single bead of sweat!!!

I do have a question that I've asked in another part of the forum, but haven't gotten any responses. With Jaunty, I had to get some kind of libdvd4 (something) to play a store bought DVD. I'm wondering if it's the same commands for Lucid-64 bit? Here's a link to that thread (because it's a different issue than this one).

[http://ubuntuforums.org/showthread.php?t=1410675](http://ubuntuforums.org/showthread.php?t=1410675)

-Leo

---

### Post by coldraven on 2011-12-04
I've been running 64 bit on this dual core laptop (4GB) for three years. The only issue was about one year ago when Adobe Flash 64bit had a serious security problem.
I just installed 32bit Flash for a while, now I'm back with 64bit Flash.
I run 10.10 for work and 11.10 for experiments.

---

### Post by ubuntu27 on 2011-12-04
I do have a question that I've asked in another part of the forum, but haven't gotten any responses. With Jaunty, I had to get some kind of libdvd4 (something) to play a store bought DVD. I'm wondering if it's the same commands for Lucid-64 bit? Here's a link to that thread (because it's a different issue than this one).

[http://ubuntuforums.org/showthread.php?t=1410675](http://ubuntuforums.org/showthread.php?t=1410675)

-Leo[/QUOTE]

After installing the [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras"), install commercial DVD support by opening the Terminal and typing (or COPY&PASTE):

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

More info can be found here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by oldos2er on 2011-12-04
I believe it's the same. That script downloads and installs libdvdcss2 from the Medibuntu repository. [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by S2UIRR3L on 2011-12-05
This gets better and better... Downloaded the restricted extras and the libdvdcss2 thing in terminal and again, everything works flawless. You guys are the best and seriously, if you were in front of me right now I'd give ya'll a great big hug for everything!

-Leo

---

### Post by craig10x on 2011-12-05
And in fact, aside from using the terminal to install, the medibuntu site actually has it as a deb file...that is how i installed it on my ubuntu 11.10...works great...No problem playing commercial dvds now...and using K3b, once that libdvdcss2 codec is installed, you can even rip (using copy to copy) an encrypted commercial dvd to an unencrypted copy!

---

### Post by Khakilang on 2011-12-05
I am using 64 bit although my memory is only 2GB. Why? My reason is 64bit processing is much faster than 32bit processing. Please correct me if I am wrong.

---

### Post by thatguruguy on 2011-12-05
> **Khakilang said:**
> I am using 64 bit although my memory is only 2GB. Why? My reason is 64bit processing is much faster than 32bit processing. Please correct me if I am wrong.

That depends on what you're doing.  If, for instance, you do a lot of video transcoding, you'll notice a significant improvement when you run 64-bit.

---

### Post by S2UIRR3L on 2011-12-05
All I have to say is:

I have a new love for Ubuntu. I've finally made the full transition and no longer use XP. I'm only using Ubuntu and don't care for XP anymore.

It's still in my laptop's hard drive, but I'm just keeping it there sort of like a fossil to show future generations what the dinosaurs were like lol.

I really like the 32-bit systems... but this 64-bit system rocks!!!

-Leo

---

### Post by wolfen69 on 2011-12-05
> **S2UIRR3L said:**
> All I have to say is:

I have a new love for Ubuntu. I've finally made the full transition and no longer use XP. I'm only using Ubuntu and don't care for XP anymore.

It's still in my laptop's hard drive, but I'm just keeping it there sort of like a fossil to show future generations what the dinosaurs were like lol.

I really like the 32-bit systems... but this 64-bit system rocks!!!

-Leo

I remember days like you've had. Linux is still perfect *for me*, but my "gee whiz" days are over. I just don't get too excited anymore.

---

### Post by oldrocker99 on 2011-12-06
The biggest problem I have found is with essential packages I want that are only available as a 32-bit .deb. (Specifically, Avasys' pipslite scanner program for my Epson NX420.) So, I got the .tar.gz and compiled it. Presto! a 64-bit program installed.

I have noticed a lot of 32-bit only programs in the Software Center...

---

### Post by VeeDubb on 2011-12-06
I still stick by my earlier comments, that 64bit has been ready for primetime for a very long time now, and that the Ububntu devs are well overdue in making 64bit the default.

However, I will say that I've had a small, nagging gripe with 64bit for a while.

When you double click on a 32bit deb file that you've downloaded, you should be able to install it with nothing more than a warning that it's designed for an older architecture, and may not work perfectly.  I cannot see any reason why we should be forced to install them from the command line.

---

### Post by S2UIRR3L on 2011-12-06
> **oldrocker99 said:**
> The biggest problem I have found is with essential packages I want that are only available as a 32-bit .deb. (Specifically, Avasys' pipslite scanner program for my Epson NX420.) So, I got the .tar.gz and compiled it. Presto! a 64-bit program installed.

I have noticed a lot of 32-bit only programs in the Software Center...

I'm not very good with computers, never mind how many bits is uses for each program... I can't tell which one is which? I don't have anything special installed on my new 64-bit computer, other than the libdvdcssread4 something that I did to watch a movie once in a while... And even then, I'm assuming that it's up to my RAM to make it play smooth without the "strobing" affect. Oh, and one more thing. I don't know what program it is, but flash is flawless on this little computer. I don't know if it's a 64-bit thing or because it's a dual-core processor? Once I learn more about all this, I hope to be as good as all of you!

-Leo

---

### Post by Drone4four on 2011-12-09
When I got my single core s939 AMD "Venice" Athlon 64 3000+ in summer 2005 I installed Slamd64.  Everything worked flawlessly except YouTube b/c there were no 64-bit libraries for Flash.  The trick to get around that was a compatibility application called nspluginwrapper.  I never got it working b/c I was a Linux novice at that point.  At that point I was dual booting with Windows.  

My brother today works at BestBuy and he says they don't even sell computers with 32-bit operating systems pre-installed.  32-bit is going the way of the dodo like 16-bit did aons ago.

---

### Post by oldos2er on 2011-12-09
> **Drone4four said:**
> My brother today works at BestBuy and he says they don't even sell computers with 32-bit operating systems pre-installed.  32-bit is going the way of the dodo like 16-bit did aons ago.

It seems the transition from 32- to 64-bit is taking far longer than the one from 16- to 32-bit did. Most people I knew then were tripping over themselves in the rush to 32-bit, and I don't recall anyone saying "don't upgrade to 32-bit unless you have 4MB RAM or more"!
:)

---

### Post by S2UIRR3L on 2011-12-10
[QUOTE=oldos2er]It seems the transition from 32- to 64-bit is taking far longer than the one from 16- to 32-bit did.[/QUOTE]

I can only assume that it's taking a while because 32-bit computers have been around for quite some time and to be honest, there's a lot of them that were built better than some 64-bit computers.

For instance; Do I take the generic 64-bit computer who's name I've never heard of? Or do I take the Fujitsu computer because I know it's quality, even tho it's a 32-bit computer? I'll take the Fujitsu lol.

I'll tell ya... This little Gateway computer that I'm using is my first 64-bit computer and I couldn't be happier with it. If I had to pay for it, I would, because I'm familiar with the "Gateway" name.

---

### Post by lolpenguin on 2011-12-10
Ever heard of the [Year 2038 problem]("http://en.wikipedia.org/wiki/Year_2038_problem")? This affects all 32-bit Unix-based systems.
:)This is why you use x86_64

---

### Post by exploder on 2011-12-11
The PCLinuxOS KDE 64 bit test releases have made a believer out of me where 64 bit is concerned. I understand everyone has their own individual preferences and that's cool.

64 bit is the future and I like how Texstar has tweaked and tuned the 64 bit test release. I have been running test 3, fully updated for some time now and I am convinced that 64 is the way to go provided you have the hardware for it.

New computers come with a lot of memory theses days and 64 bit operating systems are ideal so long as the system has good solid drivers and PCLinuxOS really delivers where hardware support is concerned for me. My first experience with 64 bit was Ubuntu 8.04, it was pretty nice but graphics support has gone downhill for my hardware since then.

64 bit is ready for prime time, it all just depends on your hardware and how much care the developers take to ensure good hardware support.

---

### Post by S2UIRR3L on 2011-12-13
@ lolpenguin:
You just freaked me out! I thought we were all safe and totally out of any danger once the calenders started saying 01-JAN-02 (or better said: 01-JAN-2002). Not sure if I'll be alive in 2038, don't know if the world will be a place I'd want to live in by then, but I'll burn that bridge when I get there lol.

@ ecploder:
I've tried PCLOS on my 32-bit systems and I thought it was great. Never had a problem with it other than I didn't care too much for the KDE stuff. I didn't use it enough to learn to use it properly, but from what I experienced, it was pretty smooth. I may try it again in the future if I can find the time.

-Leo

---

