---
title: "simple question regarding download of debian 7 wheezy"
date: 2013-05-06
forum: Any Other OS
---

### Post by sid0972 on 2013-05-06
do i heard that debian wheezy was released, and decided to give it a try
but when i go to the downloads page to download dvd, i can see 3 dvd's for download

are [all these]("http://cdimage.debian.org/debian-cd/7.0.0/amd64/iso-dvd/") dvd's required? 

cause i was just trying to download a live cd from [here]("http://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/"), but they all are 6.0.7 not 7.0

Kinda curious, what are those big dvd's for.............and where should i download 7.0 from

---

### Post by deadflowr on 2013-05-06
You only need disk 1 to get an install of debian.
The other disks are full of additional software packages.

---

### Post by DarkSwordmaster on 2013-05-06
It isn't necessary to download the DVD's, that's only if you want to have basically a lot of things you won't even use in your whole life.
Here are the live CD's for the last released debian: [http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)
I think is better to install from a Live CD or a tiny Netinstall, you are aware of what you install beside the basis for the OS to work, but that is up to you.

---

### Post by sid0972 on 2013-05-06
so that means from this page [here]("http://cdimage.debian.org/debian-cd/7.0.0/amd64/iso-cd/"), if i install cd1 that should be enough??
and @darksword i dont know how that installation works

---

### Post by CharlesA on 2013-05-06
The netinstall? It's pretty sweet, especially if you have a fast net connection. That is the only way I install Debian.

---

### Post by deadflowr on 2013-05-06
> **sid0972 said:**
> so that means from this page [here]("http://cdimage.debian.org/debian-cd/7.0.0/amd64/iso-cd/"), if i install cd1 that should be enough??
and @darksword i dont know how that installation works

From debian:
> [FONT=sans-serif]The [/FONT]**first**[FONT=sans-serif] CD/DVD disk contains all the files necessary to install a standard Debian system.[/FONT]
[FONT=sans-serif]To avoid needless downloads, please do [/FONT]**not**[FONT=sans-serif] download other CD or DVD image files unless you know that you need packages on them.[/FONT]

Of course if you have a nice stable internet connection, a netinstall is always an option.

---

### Post by sid0972 on 2013-05-06
the procedure for network install looks a little complicated to me
i already have several distros on my computer
is it safe to do a network install, i mean it wont format the whole drive would it?

also, does a simple guide for net install exists?

---

### Post by CharlesA on 2013-05-06
> **sid0972 said:**
> the procedure for network install looks a little complicated to me
i already have several distros on my computer
is it safe to do a network install, i mean it wont format the whole drive would it?

also, does a simple guide for net install exists?

The install process is the same as the regular install, you just pull the packages from the repos instead of the cd/dvd.

---

### Post by kiyop on 2013-05-06
> **sid0972 said:**
> the procedure for network install looks a little complicated to me
i already have several distros on my computer
is it safe to do a network install, i mean it wont format the whole drive would it?
Do you have empty part and/or empty partition which you can format in some media?
If you have, select "manual partitioning" at partitioning step. You can select something like "use empty part" either.
Don't do a mistake in selecting the partition (or empty part) to which you install debian.

> **sid0972 said:**
>  also, does a simple guide for net install exists?
Before seeking a **simple** guide, read the release note of wheezy: [http://www.debian.org/releases/stable/releasenotes](http://www.debian.org/releases/stable/releasenotes)
Furthermore, install guide is: [http://www.debian.org/releases/wheezy/installmanual](http://www.debian.org/releases/wheezy/installmanual)

I think that newbies who have not read the release note nor the installation guide of debian may have unrecoverable troubles after installing debian.

Debian is not so easy to manipulate as Ubuntu. If you do not want to read the release note or do not have time to read the release note, using Ubuntu instead of debian is better choice.

---

### Post by deadflowr on 2013-05-06
If you don't feel comfortable installing it with netinstall then don't.

The overall procedure for installing is mostly the same as with the others you've installed.
Just pay attention to which partition you install it to, and watch out where any bootloaders are set to.

---

### Post by sid0972 on 2013-05-06
ok thanks currently i am downloading just 1st cd, and i'll install it report back
shame there's no live cd for wheezy yet...

---

### Post by iamkuriouspurpleoranj on 2013-05-06
Just enjoy the journey. If you want easy Debian, that's Ubuntu.

---

### Post by excollier on 2013-05-06
There is a live dvd available now here [http://live.Debian.net](http://live.Debian.net)

---

### Post by buzzingrobot on 2013-05-06
Don't think version 7 livecd's are available yet.  They'll be along later, I guess.  This seems to be something of a Debian tradition.

Be aware that there are no -- nada, none, zero -- proprietary goodies provided in a Debian install.  That means if you need a proprietary driver to get something like wifi working, Debian will politely stop while you go elsewhere to find and install the driver. 

As mentioned, if you have no experience with Debian, reading the docs is a very good thing to before jumping into the pool.

---

### Post by sid0972 on 2013-05-07
> **excollier said:**
> There is a live dvd available now here [http://live.Debian.net](http://live.Debian.net)

well thank you, exactly what i was looking for, i already have downloaded 1st cd, but will download gnome live cd too, much more comfortable with it.

> **buzzingrobot said:**
> Don't think version 7 livecd's are available yet.  They'll be along later, I guess.  This seems to be something of a Debian tradition.

Be aware that there are no -- nada, none, zero -- proprietary goodies provided in a Debian install.  That means if you need a proprietary driver to get something like wifi working, Debian will politely stop while you go elsewhere to find and install the driver. 

As mentioned, if you have no experience with Debian, reading the docs is a very good thing to before jumping into the pool.

Thanks for the heads up, but i'll install debian and learn on the fly

---

### Post by excollier on 2013-05-07
The Gnome live dvd only works in fallback mode for me, but the KDE version works ok. Thinking of wiping Ubuntu 12.04.2 for it (gasps of horror!!)

---

### Post by excollier on 2013-05-07
> **buzzingrobot said:**
> Don't think version 7 livecd's are available yet.  They'll be along later, I guess.  This seems to be something of a Debian tradition.

Did you not check the link and actually* see* the live/install dvds? *And* a separate list with non-free firmwares included?

---

### Post by mips on 2013-05-07
> **buzzingrobot said:**
> Don't think version 7 livecd's are available yet.

Open your eyes, read & comprehend the thread again, it's not hard :biggrin:

See [http://live.debian.net/](http://live.debian.net/)

Or to simply it even more see
[LIST]
[*]**Download releases:** [oldstable]("http://live.debian.net/cdimage/release/oldstable/") [stable]("http://live.debian.net/cdimage/release/stable/") [stable+nonfree]("http://live.debian.net/cdimage/release/stable+nonfree")
[/LIST]

---

### Post by deadflowr on 2013-05-07
^Yes. Debian doesn't call it a release until every last nook and cranny is ready, including the various downloadables.

---

### Post by buzzingrobot on 2013-05-07
> **excollier said:**
> Did you not check the link and actually* see* the live/install dvds? *And* a separate list with non-free firmwares included?

No, actually.  

It's nice that Debian supplies links to non-free firmware.  It'd be even nicer if they just rolled it all into the install.

---

### Post by Erik1984 on 2013-05-07
> **buzzingrobot said:**
> No, actually.  

It's nice that Debian supplies links to non-free firmware.  It'd be even nicer if they just rolled it all into the install.

That's against the spirit of Debian. They promote FOSS, that's why non-free and contrib are not part of your sources.list by default. Sure, having all the proprietary firmware and codecs by default would make Debian more convenient and 'noob-friendly' but I don't think that's their goal ;)

---

### Post by sid0972 on 2013-05-07
either ways i dont think if there's any need for me to use proprietary drivers, i'm cool with open source, and this is just for learning purpose

---

### Post by excollier on 2013-05-08
> **buzzingrobot said:**
> No, actually.  

It's nice that Debian supplies links to non-free firmware.  It'd be even nicer if they just rolled it all into the install.

**They do**. I downloaded the iso with non-free included.

[http://live.debian.net/cdimage/release/stable+nonfree/amd64/iso-hybrid/](http://live.debian.net/cdimage/release/stable+nonfree/amd64/iso-hybrid/)

---

### Post by buzzingrobot on 2013-05-08
> **Euroman said:**
> That's against the spirit of Debian. They promote FOSS, that's why non-free and contrib are not part of your sources.list by default. Sure, having all the proprietary firmware and codecs by default would make Debian more convenient and 'noob-friendly' but I don't think that's their goal ;)

I know.  I've just lost patience with developers not wanting to dirty their hands for prissy ideological reasons but then foisting this work onto their users. It's forcing users -- not asking them -- to inconvenience themselves for reasons that are important to developers but may not at all be important to any given user. I don't see how that promotes FOSS. If you can't run Debian on your hardware without non-free code, then what you have learned, in fact, is that FOSS is inadequate to your needs. 

I'd rather see every non-free driver, etc., that can legally be in an install package be included and be treated during the install just as another piece of code. (Same thing applies to Ubuntu and those "restricted" packages of codecs, Flash, and fonts. If it's legal to put it in an install package, that's where it belongs.)

---

### Post by buzzingrobot on 2013-05-08
> **excollier said:**
> **They do**. I downloaded the iso with non-free included.

[http://live.debian.net/cdimage/release/stable+nonfree/amd64/iso-hybrid/](http://live.debian.net/cdimage/release/stable+nonfree/amd64/iso-hybrid/)

I see those are "unoffical".  Does that have a bearing on how Debian supports them?

Are the non-free bits handled in the same way as everything else by the installer, or does the user need to accomplish the installation of non-free firmware independently and then return to the installer?

---

### Post by sid0972 on 2013-05-08
i dont think if its huge that they are unofficial, if i can run them live, why the hell not?
even if they might or might not have one or two proprietary drivers/software, dont think if it makes much of a difference

---

### Post by mips on 2013-05-08
> **buzzingrobot said:**
> I know.  I've just lost patience with developers not wanting to dirty their hands for prissy ideological reasons but then foisting this work onto their users. It's forcing users -- not asking them -- to inconvenience themselves for reasons that are important to developers but may not at all be important to any given user. I don't see how that promotes FOSS. If you can't run Debian on your hardware without non-free code, then what you have learned, in fact, is that FOSS is inadequate to your needs. 

I'd rather see every non-free driver, etc., that can legally be in an install package be included and be treated during the install just as another piece of code. (Same thing applies to Ubuntu and those "restricted" packages of codecs, Flash, and fonts. If it's legal to put it in an install package, that's where it belongs.)

Listen up, you're looking a gift horse in the mouth. What developers decide to do is their prerogative, if you don't like it move on!

If you don't like then switch to a different distro, Windows or OS X. You have choices.

---

### Post by monkeybrain2012 on 2013-05-08
> **buzzingrobot said:**
>  I don't see how that promotes FOSS. If you can't run Debian on your hardware without non-free code, then what you have learned, in fact, is that FOSS is inadequate to your needs. 


I know that the reason given by Fedora is that hopefully you would learn the lesson that you should purchase hardware that doesn't require non free codes to run. I think Debian's reason would be similar. :P However, if you do have such hardware it does provide the means to get it to work hence the non free codes are available if you really need them.

I have both Debian and Ubuntu, for different reasons. I use Ubuntu as my main OS because it just works, I like the convenience and the stability (Well I use Debian sid, not Debian stable with the stale software so Ubuntu is actually more stable). But I also like to use Debian to learn. In Debian I do a lot of things manually which in Ubuntu would have been taken care of out of the box. I think it is worthwhile to acquire those skills. I actually also like Debian's philosophy, even though it may be hard to adhere to all the time, but I think we shouldn't lose sight of idealistic visions while being pragmatic to get things done (for the same reason I have lots of respect for the FSF and RMS even though I can't, in all honesty adhere their way in practice)

---

### Post by buzzingrobot on 2013-05-08
> **mips said:**
> Listen up, you're looking a gift horse in the mouth. What developers decide to do is their prerogative... 

Couldn't agree more. FOSS is a developer's game.  

I have no issue with developers and FOSS.  What I think is pretty purposeless is keeping non-free code out of the primary install routine because the developers have ethical issues with that, but then helping the user install the same non-free files.  If, for example, a distro opposes non-free code on an ethical basis, why then push that "sinful" work off an users? It's as if the developers don't want to dirty their hands, but don't mind or care if users have to do that.

The entire approach assumes that the users know about FOSS, know why the developers harbor those ethical objections, and are willing to inconvenience themselves as the price to be paid for using FOSS.  In the case of Linux newcomers, I don't think that is an accurate assumption. New users are as likely to be ticked off by what they see as developer arrogance as they are impressed with developer virtue.  We should not assume that every Linux user cares about FOSS.

---

### Post by buzzingrobot on 2013-05-08
> **monkeybrain2012 said:**
> I know that the reason given by Fedora is that hopefully you would learn the lesson that you should purchase hardware that doesn't require non free codes to run. I think Debian's reason would be similar.

People have been hoping that for 20 years and it still really hasn't happened.  The only people who buy hardware specifically to avoid running non-free code are firm and enthusiastic FOSS adherents.  For them, the "free" aspect of software takes top priority over everything else.  Like RMS, they are willing to limit their digital capabilities so long as they feel good about keeping the faith.  The vast majority of computer users don't care.

I have no issues with FOSS. I understand why FOSS developers want their code to be free.  I just happen to think that pushing work off on users, and inconveniencing users, because developers are averse to packaging someone else's non-free files in their installation routines is counter to everyone's interests.  Specifically, it does not turn new users into FOSS converts. I suspect in many, many instances new users just see a Linux distribution that doesn't work right after the install, get frustrated, and go back to Windows.

---

### Post by monkeybrain2012 on 2013-05-08
> **buzzingrobot said:**
>  I suspect in many, many instances new users just see a Linux distribution that doesn't work right after the install, get frustrated, and go back to Windows.

Not really, that's why you have 'easy' distros like Ubuntu or Mint for beginners. But your complaint is about Debian, which is not  intended  for inexperienced users (much less handholding in general) and I suspect that the Debian people don't really care about market share.

---

### Post by CharlesA on 2013-05-09
Less hand holding? I suppose that is true, but the install processes is pretty much the same as Ubuntu.

---

### Post by iamkuriouspurpleoranj on 2013-05-09
^Funnily enough, the expert install would enable new users to get more easily a kind of sudo-included Ubuntu-like experience. However, the options can be intimidating - even though you can mostly go with the defaults. But like something like Slackware or FreeBSD, the expert install is mostly just enter, enter, enter.

---

### Post by excollier on 2013-05-09
> **monkeybrain2012 said:**
> Not really, that's why you have 'easy' distros like Ubuntu or Mint for beginners. But your complaint is about Debian, which is not  intended  for inexperienced users (much less handholding in general) and I suspect that the Debian people don't really care about market share.
It's a pity that some distros have to be "difficult". After all what is a computer OS for ultimately? To actually ***do*** stuff with, like office type work, gaming, web browsing, HTPC et al? If so then it should be as simple to use and supported as possible.
If, on the other hand,the target is development and how to learn the workings of an OS, then the user should be made to work a little harder.
The user, coming from Windows, who wants a working system is quickly going to drop something that he cannot just boot up and do his/her work with, what's the point of that? Most computer users are that person. Steer them to Mint, Ubuntu etc. keep them onside.
What I'm getting at here is hurrah for the likes of Mint and Ubuntu (I have both myself) and for others hurrah for the "difficult distros". I fall  somewhere between the two.
Most windows users are utterly unaware of the existence of Linux,(my friend, on seeing me boot a computer with Mint asked "What version of Windows is that??") and maybe even think Apple OSx is just a Windows variant.
In much the same way as satellite tv viewers in the UK and Ireland mostly think that Sky are the one and only provider of satellite tv, and that all such must be paid for with hard earned cash, when it's simply untrue, there's plenty of free stuff out there. The parallels with Windows/Apple and Linux are striking. Such is the penetration of large commercial providers.
If you want to win over users from Windows, Linux has to work with ease and not break easily, it's the only way. Maybe later they will delve a little deeper, maybe not, but once they see they can achieve the same result without being out of pocket every few years, they will never go back.
Says me, a convert to Linux of only six months or so!
PS sorry for drifting off topic.

---

### Post by iamkuriouspurpleoranj on 2013-05-09
^Woah - hold your horses. Debian doesn't deliberately set out to make your life difficult.

A couple of points:
- What seems difficult at first gets easier over time. For many Debian users, what seems difficult to you, seems quite easy to them. I sweated over partitioning once upon a time but it happened a couple of weeks ago that I went out for a drink and woke up in the morning with SolusOS perfectly installed on my main PC. Not sure how it got there but it's clear that some skillz have already passed into my subconscious(unconscious?).
- It's not difficult. It has options, that's all. When you don't know what to choose, choice is a burden. The fact that it prompts you for a hostname is taxing for a new user and I aborted my first install attempt because of it. But all you need to do is hit [enter].
- It has options because it positions itself as a universal operating system. The idea is that you can do whatever with it, wherever you want, more or less. There are instructions.
- The free thing is not easily summed up. Basically, not every jurisdiction allows them and there may be licensing issues if using them in production. Therefore, Debian saves you this hassle by leaving them out. Debian is often used for servers etc. and needs to be configurable for this, not cuddly and user-friendly out of the box.
- Debian is sometimes described as a meta-distribution, which simply means that other distros (including Ubuntu) are based on it. The fact is that there are plenty of easy Debian-based distributions for those who want the software but not the confusing array of options or the cautious/conservative approach to codecs etc.

Debian is a very good tool and a doddle to set up correctly once you know how. But if it's not for you, it's not for you. Personally, I think the Debian forums could be a friendlier place but alas a small cabal of active users seems to have squatted it and I really don't find it a pleasant to be.

---

### Post by excollier on 2013-05-09
I think you missed my point, and I never said Debian was difficult.
What I am trying to say is that anyone coming straight from Windows will be expecting or hoping that everything "just works" as with Windows. Sometimes with Linux certain things don't "just work" and some work is needed to make it work. Sometimes a different distro is required because the initial choice just will not work easily with certain hardwares. If you want people to migrate from Windows, then it must be as seamless as possible, or they will just give up and pay money for an easy time.
Six months ago I was a Windows user of 20 years, I knew practically nothing of linux or all the attendant extra knowledge that comes with it after a short time. Now I dual boot two computers, have a Raspberry Pi with the option of several os, and constantly download and try new distros, you know the form I'm sure, because I had time to sit down and break a few set ups before I got it right. Many users just want to "use" their computer for it's installed apps, not fiddle about with stubborn hardware drivers.
Don't misunderstand me, I am very pro Linux in all it's variants, but the fact is some "just work" some need a lot more input, and like me it's better to start with the likes of Mint or Ubuntu if you want a smooth transition.
Here's my present set up: Not bad for six months of learning from scratch. I'll shut up now.
**Acer Aspire 5535** /  [COLOR=#FF0000]**Windows**[/COLOR] [COLOR=#008000]**Vista**[/COLOR] [COLOR=#0000FF]**Home**[/COLOR] [COLOR=#FFBF00]**Basic**[/COLOR] 32 bit / **[COLOR=#0040FF]LM 13 KDE 64 bit[/COLOR]** *dual boot* 
**HP Pavillion DV5 1111EA** / **[COLOR=#40BF00]LMDE Cinnamon 64 bit[/COLOR]** / [COLOR=#FF4000]**Ubuntu ****12.04.2 32 bit** [/COLOR]*dual boot*
***Puppy Linux on a usb stick*.**
[B]Raspberry Pi(Debian Wheezy ARM, PiBang, xbmc, RaspRazor)

[/B]

---

### Post by buzzingrobot on 2013-05-09
> **monkeybrain2012 said:**
> Not really, that's why you have 'easy' distros like Ubuntu or Mint for beginners. But your complaint is about Debian, which is not  intended  for inexperienced users (much less handholding in general) and I suspect that the Debian people don't really care about market share.


It's not a complaint so much as a judgement that the practice does not advance FOSS.  If it doesn't, why annoy users?

For example, music players are a dime-a-dozen in Linux.  Few of them will work unless a variety of codecs, drivers, etc., have been installed. Dependency resolution schemes -- apt-get, yum, etc. -- are supposed to locate and install dependencies.  But, they don't install *these* dependencies. Those non-free files, may be hosted in another of the distribution's repos, or they may not. 

But, either way, the hapless user is left to resolve this, usually with no information about what's needed having been provided. I have never seen an installer or a dependency resolving tool that actually lists the specific non-free dependencies its developers have chosen to forbid it from installing.

How, then, does compelling users to chase around the net looking for the files that their distribution did not install for allegedly ethical reasons actually benefit FOSS? Does it help developers write better software?  Does it attract more people to FOSS? Obviously, the answer is no.

How many posts have we seen over the years from newbies who weren't able to boot a livecd because they use an ATI or NVidia card? Nouveau still crashes a booting kernel on certain Nvidia cards. Users are left to muddle about trying to deal with this issue so they can actually install the distribution, and then find and install the non-free Nvidia driver. Why not use the Nvidia driver on on the liveced to ensure the thing will actually work on as much hardware as possible?  Let the user choose Nouveau during the install, rather than shipping livecds that do not work at all for some users?

("Easy to use" distributions are obviously better for inexperienced users.  But, after 18 years of Linux experience, I'm quite happy to let someone else's software handle as many of the routine, boring, and mundane tasks as possible, so long as it gets me to the same place I'd get by pecking around in vi.  Wanting to avoid doing things the hard way does not mean you don't know what you're doing.)

---

### Post by mastablasta on 2013-05-09
> **excollier said:**
> The user, coming from Windows, who wants a working system is quickly going to drop something that he cannot just boot up and do his/her work with, what's the point of that? Most computer users are that person. Steer them to Mint, Ubuntu etc. keep them onside.


true. 

Linus explained it well. The linux desktop market share is low because computers simply do not come preloaded with it. 

he goes on to explain how normal people do not want to install their OS on mashcine. no one wants to buy a phone and then have to chose and instal the OS on it. so all phones come preloaded with some version of an OS. be is symbian or Android, iOS or windows phone.

and then you have RPi. where debian proves just how difficult it is to use  - small kids use it and not just use it they create content on it and programme it.... again that Debian verison was modified to fit perfectly with hardware. so there is basically no fuss on install.

if only there were drivers (be it opensoruce or closed ones) on linux and that they are as easy as 2 button install, then people switching from windows would have much less to worry about

lets face it windows is not easy for true beginners and computer illiterate to install. especially if you want multiple partitions and some other things. but on the other hand it never needs nomodeset and such just to boot. or their updates won't make sound stop working or change system time without any optionto change it back.

as for the netinstall it's like ubutnu minimal iso isn't it?

---

### Post by buzzingrobot on 2013-05-09
> **mastablasta said:**
> true. 


if only there were drivers (be it opensoruce or closed ones) on linux and that they are as easy as 2 button install, then people switching from windows would have much less to worry about...

Some non-free code isn't included in distribution installs for legal reasons.  But, if it's not installed simply because it's non-free, then that does both users and FOSS a disservice. Hence, my rants.

> ...windows... never needs nomodeset...

Would really like to see cards that need nomodeset be detected so that option can be applied automatically, especially in the case of LiveCD's and LiveDVD's. Normal people who go to the effort of burning a LiveDVD, and then see nothing but a black screen when they boot off it have every reason to say, "Broken!", not "nomodeset".


> ...as for the netinstall it's like ubutnu minimal iso isn't it?

The file sizes of the two images seem to be a wee bit different, but the mini.iso *is* a network install image. I've used it a number of times; it's a good way to avoid that nomodeset problem at the install.

---

### Post by sid0972 on 2013-05-09
ok guys i just finished downloading and trying debian gnome live cd
to be honest there was nothing much impressive to catch my attention

> **mastablasta said:**
> true. 
if only there were drivers (be it opensoruce or closed ones) on linux and that they are as easy as 2 button install, then people switching from windows would have much less to worry about


main reason i didnt install it, cause my qualcomm wifi-catching device isnt working there.
with most distros it does.......

---

### Post by monkeybrain2012 on 2013-05-09
> **buzzingrobot said:**
> It's not a complaint so much as a judgement that the practice does not advance FOSS.  If it doesn't, why annoy users?

For example, music players are a dime-a-dozen in Linux.  Few of them will work unless a variety of codecs, drivers, etc., have been installed. Dependency resolution schemes -- apt-get, yum, etc. -- are supposed to locate and install dependencies.  But, they don't install *these* dependencies. Those non-free files, may be hosted in another of the distribution's repos, or they may not. 




There are licensing and legal issue to distribute non free codecs, this is not just the result of  some free software fanaticism. Mint installs the codecs by default but Mint is based in France where many software patent laws don't apply and it is too small so it can slip under the radar easily. I think that some music players such as Rhythmbox do advise you about missing codecs and where to find them in some distros.

Actually even in Windows not all codecs are installed by default, WIndows mediaplayer doesn't play many formats out of the box. That's one reason why vlc is popular on Windows as well.

---

### Post by buzzingrobot on 2013-05-09
> **monkeybrain2012 said:**
> But you do know that there are licensing and legal issue to distribute non free codecs...

Yes, as I've acknowledged.  But, the issue involves more than music player codecs. If there is no legal reason not to include non-free code in a distribution's initial install routine, it ought to be there. 

I don't want to belabor this.  I've just grown tired of being told that something I need isn't there when it could be there. 

I have to wonder, too, if push came to shove, if there is really any legal difference between putting a restricted non-free file on a repository server and pointing people to it, versus making it available during the initial install. You might argue the file gets installed only at the user's discretion, but the entire distribution gets installed only at the user's discretion.

---

### Post by iamkuriouspurpleoranj on 2013-05-09
^Don't use it, then. I don't agree with Arch Linux and the "Arch way". So I don't use it. Problem solved.

---

### Post by sid0972 on 2013-05-09
all these long, detailed and enlightening discussions about debian and FOSS
come to think of it, i just asked a simple question about which iso to download!!!!!

---

### Post by buzzingrobot on 2013-05-09
> **iamkuriouspurpleoranj said:**
> ^Don't use it, then. I don't agree with Arch Linux and the "Arch way". So I don't use it. Problem solved.


It's not a matter of agreeing or not agreeing.  It's just that on the rather narrow and specific point I posted about, I would do things in a different way because I think it turns people off FOSS. 

It's certainly not going to influence what I install and use. The results are a lot more important than any distribution's so-called "way".

---

### Post by Rukiri on 2013-05-09
> **sid0972 said:**
> all these long, detailed and enlightening discussions about debian and FOSS
come to think of it, i just asked a simple question about which iso to download!!!!!

Debian 7 ISO 1 is what you want to download, if you have a fast connection install from a netinstall cd (I have a 120MBPS connection so I go with net install but even a lower 20MB or even 10MBPS will suffice). 

This is the one time I'm probably going to say this but, RTFM!

The ISO includes pretty much everything, I don't like that infact I hate that!  But it's there I guess for an OFFLINE install, if you have a stable connection install from the net this way you install what you need and nothing more similar to arch or gentoo or I guess even ubuntu-server.

---

### Post by odiseo77 on 2013-05-09
I really don't get why all the fuss about Debian not including non-free drivers and software in a default install. After all, all this non-free software is in the repositories (and I believe, in the complete set of CDs and DVDs, too). If you have some piece of hardware that needs some non-free driver, simply install the deb of the driver in question after you install Debian. Problem solved. I have a nVidia card and Debian offers a method for installing the nVidia driver that is cleaner than the official nVidia installer and integrates perfectly with the package management system. 

Also, though I'm not a free software purist, I do understand the concern about non-free software: the day that a given hardware manufacturer decides to drop Linux support for their hardware (for whatever reason), every Linux user with some hardware from this manufacturer will be left with a piece of useless junk. Of course, in an ideal world hardware manufacturers would release open source drivers, but since we don't live in an ideal world I buy hardware that I simply know is supported by Linux -- either with open source drivers, or with closed source drivers.

---

### Post by iamkuriouspurpleoranj on 2013-05-10
1. You can get it all (except deb-multimedia) via the expert install.
2. Ubuntu with the tick-box for flash during installation and the need to manually install medibuntu afterwards is hardly more user-friendly in this respect. I am happy with Ubuntu and Debian's handling of this. If you are not, maybe you should use the Linux Mint edition with codecs included. Just remember that you are - correct me if I'm wrong - breaking the law in the US and Japan if you do.

One of the reasons mainstream distributions are moving away from MySQL and towards MariaDB is a concern that Oracle is becoming less open with its MySQL development, which is a security risk. Ok, that and maybe the fact that Red Hat doesn't want to encourage a company that is f****** ** ** *** **s(e).

Systems of convenience, which by their nature are ambivalent regarding the inclusion of non-free software, nurture within us a general sense of indifference to important issues, including non-ideological ones such as security.

It is a *security* concern and not an ideological one that makes it important for us to know and understand what it is that is being installed on our computers. This is not about the summer of free love. Debian was born out of a practical need and it survives precisely because it continues to meet that practical need.

In our natural desire for FOSS to grow, we need to be careful not to neglect a fundamental requirement, which is for it not to die or become so diluted that it becomes meaningless.

_Remember_: the strategy of those who would see FOSS fail is "embrace, extend, extinguish". Any expansion of FOSS needs to be managed and monitored (by us - for *we* are the company) to make sure it is growing healthily and according to *our* interests and is not merely *being grown* as part of someone else's corporate strategy.

---

### Post by sid0972 on 2013-05-10
> **Rukiri said:**
> Debian 7 ISO 1 is what you want to download, if you have a fast connection install from a netinstall cd
I have downloaded and tried debian live, read my previous post.
> 
 (I have a 120MBPS connection so I go with net install but even a lower 20MB or even 10MBPS will suffice). 
i have a 512 kilo bits per second connection, RTFM on that

---

### Post by CharlesA on 2013-05-10
> **sid0972 said:**
> i have a 512 kilo bits per second connection, RTFM on that

No need to get upset. :)

The only difference a slow connection would make with a netinstall would be that it takes longer to complete.
If you don't have a great connection, installing with the full install cd is the way to go.

---

### Post by sid0972 on 2013-05-10
which is what i did :)

---

