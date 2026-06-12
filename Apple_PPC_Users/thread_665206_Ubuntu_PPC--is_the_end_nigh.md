---
title: "Ubuntu PPC--is the end nigh?"
date: 2008-01-12
forum: Apple PPC Users
---

### Post by VidiotGeek on 2008-01-12
I only recently embarked on my adventure to run Linux on my 800MHz iMac G4. After a great start with Feisty, a foolish dist upgrade to Gutsy has left me unable to get a working install. I understand that PPC is no longer an officially supported architecture & that it's now community maintained. From all the reading I've done in an attempt to figure out how to get a working install again, it sounds like the PPC community is having some problems maintaining the distro. 

(References)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337")
[https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html]("https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html")
[http://ubuntuforums.org/archive/index.php/t-151188.html]("http://ubuntuforums.org/archive/index.php/t-151188.html")

Namely, the fact that Gutsy contains multiple show stopper bugs that are non-trivial to fix for your average desktop user when Gutsy has been out for 4 months. Yet no ISO exists (that i can find) which installs & boots with the same relative lack of hassle I had with my initial install of Feisty. 

I'm not giving up entirely on running Ubuntu on my Mac but for the time being, it looks like I'll have to turn to another distribution that has better PPC support. I really like Ubuntu, but it seems my best shot of Linux on a Mac is Yellow Dog...& really, that's just a terrible name, isn't it? Two words with a negative slang connotation, combined. Genius...

I guess I just want this as a general thread to collect everyones thoughts on the specific problems & obstacles of running Ubuntu or any Linux distro on a Mac/PPC computers that one does not face when working with the x86 (et all) platform. Especially from the perspective of new users trying Linux in earnest for the first time, such as myself. Those who are less capable of exercising any sort of command line prowess to solve their problems.

---

### Post by stmiller on 2008-01-12
Ubuntu PowerPC is not community maintained. The official packages and security updates come from the same ubuntu channels as the x86 and x86_64 bit versions. 

The only thing that was dropped was paid Canonical tech support for PowerPC. So for tech support you have to come here (the forum). 

There are many threads on the Gutsy booting and other issues which might have some more info. Yellow Dog is basically outdated Fedora with no community. I'd recommend anything over Yellow Dog...

---

### Post by DirtDawg on 2008-01-12
Yellow Dawg is just awful. I've yet to have a good experience with it. Ppc's have been losing support for some time now and I think that trend is going to continue as Macs use Intel architecture now. 

On my imac G3, I now use Debian Etch (or 'stable'). I highly recommend you try it. It works well and is faster than Ubuntu in my experience. Especially with a lighter Desktop Environment like XCFE or IceWM. Some thing's are a little tougher to set up than Ubuntu, but if you already have some experience, you should be okay. 

I suppose I should toss my G3 someday, but I have an emotional attachment to it. It was the first computer that was really *mine* and it's just so cute!

---

### Post by uxe1 on 2008-01-12
its gutsy, not your mac. 
all in all gutsy has many show stopper buggs.
like others i know ive reverted back to feisty and am waiting for hardy. with hardy being a long term support release, maybe, just maybe it will be a little more reliable. (OR work at all as the case may be)

---

### Post by Jason-X on 2008-01-12
I have used Yellow Dog before and it felt really slow and bloated. Strange as it is a powerpc distro. Fedora 8 is very good if you want the latest software including Gnome 2.2. Although my fan never kicked in when I was using that and the laptop got very hot.

I am happy with Feisty for now. It is very fast and stable on my G4 Powerbook. I would also recommend Debian if you want something faster. That too works really well.

---

### Post by VidiotGeek on 2008-01-12
> **DirtDawg said:**
> I suppose I should toss my G3 someday, but I have an emotional attachment to it. It was the first computer that was really *mine* and it's just so cute!

Same here, this iMac isn't the very first computer I could claim as my own but when you consider that  my previous ones included an old Commodore 64, an Epson running some version of MS-DOS, & a Packard Bell chugging along on Win95--all bought at yard sales with a fist full of dollars--then this is my first "real" computer. Though, I did have fun & learn alot by playing around with all that retro hardware in my early teens.

It looks like the general consensus is stay away from Yellow Dog but I just downloaded 6 CD iso's for YDL 5.0.2...so I might still try it at some point. Why they don't make a single DVD iso is beyond me, but I've got plenty CD-RW's. The fact that they have some sort of deal with Sony for the PS3 & alot of other Power architecture vendors does seem to lend them some credibility as "the place to go" for Linux on PPC.

I think that Apple's move to Intel was the smartest thing they could have done at the time, especially since running Windows with BootCamp & Parallels have become such major selling points for Macs. Unfortunately, it also means less incentive to develop for the PowerPC, and with Apple "orphaning" (as I heard someone else refer to it) so many older Macs with the release of Leopard, including mine. Linux is the only place for users to turn for modern updated software. The community maintained statement is something I read at the second link I posted, scroll down to where it says PowerPC architecture. I realize that they still depend on alot of work from the primary Ubuntu development, but my instant-kill upgrade to Gutsy (aptly named, I guess) doesn't shine well upon the PPC team. Though the main reason for the problems is that Ubuntu no longer holds up a release because of PPC specific issues (part of that "not an official port" distinction) so the ISO's hit the streets whether the PPC version is ready for prime-time or not. This is a pain in the *** for n00bs such as myself who can't easily fix things when they break.

The PPC team probably just needs more hands to be able to deal with it than what they currently have & I hope that they can find them. Because Apple certainly isn't going to give me a new OS for this machine. Perhaps I'm expecting too much & being too critical, but Mac users seem to have a reputation for being demanding. For now, I will try reinstalling Feisty & wait patiently for Hardy while all those smart people toil away at the code to make it the best release yet. :-) May the force be with the Ubuntu-PPC developers.

---

### Post by bodycoach2 on 2008-01-13
I hope the Ubuntu team continues working on Ubuntu PPC code, even if there is no official support. There are many older iMacs out there that run Xubuntu just fine. Those computers could donated to other countries for educational purpose. 

There is a lady on our local free cycle board that take the older iMacs, guts them, and makes cat bed boxes out of them. At the very least, she's keeping part of the machines in use.

The PPC isn't going away anytime soon. IBM uses it in their high end equipment.

---

### Post by VidiotGeek on 2008-01-16
> **bodycoach2 said:**
> I hope the Ubuntu team continues working on Ubuntu PPC code, even if there is no official support. There are many older iMacs out there that run Xubuntu just fine. Those computers could donated to other countries for educational purpose. 

There is a lady on our local free cycle board that take the older iMacs, guts them, and makes cat bed boxes out of them. At the very least, she's keeping part of the machines in use.

The PPC isn't going away anytime soon. IBM uses it in their high end equipment.

I've always wanted an iMac aquarium since I first saw one. That has to be one of the coolest repurpose ideas I've seen, next to gutting it & putting generic PC hardware inside. That has the nice bonus of still giving you a working computer...but something still kinda feels dirty about it, lol. I guess it's not so bad as long as you're running Linux on it. I bet our cat would sleep in it if we had a Mac cat bed though.

As for IBM, I realize that their servers still use POWER chips & with the PS3 Cell processor, the architecture is far from dead. But as far as desktop computing machines for daily use, the PPC architecture has been a niche player for along time & with Macintels, it's margin can only go down for the near future. I'm sure distros like Fedora/Red Hat, Yellow Dog, Debian (?) will continue to  support the platform but this is likely to be VERY server & pro user oriented rather than the "Linux for human beings" goal of Ubuntu. It would be a shame to lose such an easy to use distro for a great platform with already fewer OS options.

---

