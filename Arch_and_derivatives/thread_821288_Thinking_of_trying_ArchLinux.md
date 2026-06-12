---
title: "Thinking of trying ArchLinux"
date: 2008-06-07
forum: Arch and derivatives
---

### Post by Methuselah on 2008-06-07
Former FreeBSD user who switched to Ubuntu as my main system relatively recently. One piece of hardware was the problem but I couldn't do without it.

Ununtu is working out quite well but I'm not as sure of what I can 'touch' if you know what I mean. I also miss the convenience of the ports system. Building things on ubuntu doesn't seem as streamlined and sometimes you do have to build (like right now virtualbox won't work with the updated kernel and the corresponding binaries aren't in the repositories). Still, I plan to learn how these things are done in the Ubuntu world.

However, I have also been thinking about Arch, Slackware and Gentoo (listed in order of likeliness to install). Are there any Arch users here who used ubuntu in the past (or not)? Why did you choose it and how is it working out?

---

### Post by Barrucadu on 2008-06-07
There are lots of post-Ubuntu Arch users here, in fact, we even have [our own subforum here](http://ubuntuforums.org/forumdisplay.php?f=321).

---

### Post by Methuselah on 2008-06-07
Cool, Thanks.

---

### Post by melrom on 2008-06-07
I'm thinking about trying it too. I was going to put it on my external hdd though... my laptop hdd is only 100 gig and it's got ubuntu, linux mint, and windows xp on it right now.

---

### Post by red_Marvin on 2008-06-07
If you like to tinker and are able to spend some time on setting it up, it might be for you. The install and setup is straightforward and theres wiki documentation on most things (I) needed, and when not, the help in #archlinux on freenode is kind to newcomers.

Personally I went back to ubuntu as I felt that I didn't have the time and/or dedication to tailor it to my needs on my main computer, got x and sound working but antialiased fonts were a tough cookie, since I didn't install gnome/kde.

For a distro that after install dumps you at a bash prompt with a minimum of packages installed, I still would call it almost newbie-friendly.

---

### Post by cardinals_fan on 2008-06-07
I have used Arch and it's a very good system.  The community is great and Pacman is just awesome.  With that said, it wasn't as fast as I expected, and I prefer Slack.  Arch is still very good though.

---

### Post by frenchn00b on 2008-06-07
> **Methuselah said:**
> Former FreeBSD user who switched to Ubuntu as my main system relatively recently. One piece of hardware was the problem but I couldn't do without it.

Ununtu is working out quite well but I'm not as sure of what I can 'touch' if you know what I mean. I also miss the convenience of the ports system. Building things on ubuntu doesn't seem as streamlined and sometimes you do have to build (like right now virtualbox won't work with the updated kernel and the corresponding binaries aren't in the repositories). Still, I plan to learn how these things are done in the Ubuntu world.

However, I have also been thinking about Arch, Slackware and Gentoo (listed in order of likeliness to install). Are there any Arch users here who used ubuntu in the past (or not)? Why did you choose it and how is it working out?

Slackware is sure a hit, as Debian and Fedora. I'd give a try slackware, that would recall ya a bit Unix...

---

### Post by K.Mandla on 2008-06-07
Moved to Arch Linux discussion forum.

---

### Post by Dr Small on 2008-06-07
> **Barrucadu said:**
> There are lots of post-Ubuntu Arch users here, in fact, we even have [our own subforum here](http://ubuntuforums.org/forumdisplay.php?f=321).
+1
I myself just very recently moved to Arch from Ubuntu. I could still be considered an ArchLinux newbie, but I definetely have a solid system. I use Arch mainly because I love to tinker and build things my own way.

---

### Post by Myriad on 2008-06-08
My path into Linux went something like FC3->Debian->Ubuntu->Gentoo->Arch plus a handful of distros I just dabbled in.  My favourite out of all them is easily Arch.  I love being able to build my system up from the core components so it only has what I want and no extraneous bloat.  It's also very (new)user friendly with documentation really only surpassed by Gentoo's in my experience.  Arch has been working great for me with the only problems being caused by me doing something stupid (isn't it always?).

---

### Post by Barrucadu on 2008-06-08
> **Myriad said:**
> Arch has been working great for me with the only problems being caused by me doing something stupid (isn't it always?).

I know, great isn't it? I've even enabled the testing and unstable repos and nothing has gone wrong yet!

---

### Post by chucky chuckaluck on 2008-06-08
as an end user nototrious for pulling a tl/dr when it comes to reading documentation, i can earnestly say that arch's documentation is brief, to the point and complete. installing arch was a pleasure, especially as its "nothing but what i want" approach was exactly what i wanted.

---

### Post by Rumor on 2008-06-08
> **Methuselah said:**
> Are there any Arch users here who used ubuntu in the past (or not)? Why did you choose it and how is it working out?

Well, as you have no doubt seen there are many current Arch users who came by way of Ubuntu. 

To your question, I chose Arch because I like the fact that there is nothing running on my machine that I did not choose to install. I like that the base installation leaves me at a command prompt and that i can build my system from that point. 

The Pacman package manager was another factor along with the Arch user Repository and the Arch Build System. The ABS makes building and maintaining your own packages simplicity itself and the AUR gives you a place to share them with other users.

Arch puts you fully in control.

And even Chucky can use it! :-P

---

### Post by smartboyathome on 2008-06-08
I am an Arch user on my desktop, and use Ubuntu on my laptop. The reason I go arch is because it only does what I want, but my laptop is mission critical and thus I want a stable setup on it, and it was already configured to my liking when I came to Arch.

---

### Post by handy on 2008-06-08
The Arch rolling release system is great too.  You will spend extra time setting up you Arch system, learning how to do some new things, but once it is setup, you will only have to do it again if you have to recover from a hardware failure.  The rolling release model keeps your system up to date & it is as easy as typing: 

***sudo pacman -Syu***

If you do it weekly or so, it takes little time to have the latest & greatest version of your Arch installation, which turns out to be a huge time saver in the long run.

---

### Post by Barrucadu on 2008-06-09
> **handy said:**
> ***sudo pacman -Syu***

If you do it weekly or so, it takes little time to have the latest & greatest version of your Arch installation, which turns out to be a huge time saver in the long run.

Or, if you install things from AUR...

***sudo yaourt -Syu --devel --aur***

---

### Post by handy on 2008-06-09
> **Barrucadu said:**
> Or, if you install things from AUR...

***sudo yaourt -Syu --devel --aur***

Actually I use tupac, but I didn't want to over complicate my post. ;-)

---

### Post by Dr Small on 2008-06-09
> **handy said:**
> The Arch rolling release system is great too.  You will spend extra time setting up you Arch system, learning how to do some new things, but once it is setup, you will only have to do it again if you have to recover from a hardware failure.  The rolling release model keeps your system up to date & it is as easy as typing: 

***sudo pacman -Syu***

If you do it weekly or so, it takes little time to have the latest & greatest version of your Arch installation, which turns out to be a huge time saver in the long run.
Yeah, I should have been doing that... as it is up to 100MBs now! Oh well :(

---

### Post by handy on 2008-06-09
> **Dr Small said:**
> Yeah, I should have been doing that... as it is up to 100MBs now! Oh well :(

With 1500/256 broadband speed that takes about 10 -> 20 minutes.

It surely isn't a major drag eh!?

---

### Post by LittleLORDevil on 2008-06-09
I have been reading around on Arch.  I have used Ubuntu for awhile but feel like I haven't really gained any Unix knowledge so I think I am going to install Arch and test it out, not only for the experience of building it from the ground up but also getting to know the inner workings of a Unix based system.

---

### Post by Barrucadu on 2008-06-09
Make sure you read the beginners guide!

---

### Post by chucky chuckaluck on 2008-06-09
> **LittleLORDevil said:**
> I have been reading around on Arch.  I have used Ubuntu for awhile but feel like I haven't really gained any Unix knowledge so I think I am going to install Arch and test it out, not only for the experience of building it from the ground up but also getting to know the inner workings of a Unix based system.

i think you'd have to make yourself learn more unixy stuff. i haven't really learned anything significantly new from using arch, other than for specific configurations. i think arch's rep as being difficult is an exaggeration. it's more detail, but it's not equivalent to a transformation.

---

### Post by Methuselah on 2008-06-10
I didn't realise this thread had continued.
A lot of great input here.

Ubuntu's ambition seems to be to have everything working automatically. When it works, it impresses me (like automatically recognising my printer and scanner) but when it doesn't work, it's more unclear how to fix it compared to a distribution where you are expected to do things by hand. In fact, attempts at autoconfiguration may work against your efforts to fix a problem.

So, I have to go with a linux kernel for the hardware support but I need to understand my system so I don't feel completely lost when there are problems. So I'll need a distribution I can build from a small core.

Someone recommended slackware but Arch seems to give you some better tools to facilitate configuration of the system.
Besides it seems a bit closer to FreeBSD which was my first ever unix.

I've been tempted by slackware before though.
It's well established and documentation looks comprehensive.

---

### Post by handy on 2008-06-10
@***Methuselah***: Try them both & pick your favourite?

---

### Post by MisfitI38 on 2008-06-10
> **Methuselah said:**
> 
I've been tempted by slackware before though.
It's well established and documentation looks comprehensive.

Slack is Linux, with very basic packaging tools and very small repos.
Arch is Linux, with a package manager on steroids and huge repos.

2 different approaches. Try both like handy said.

---

### Post by cardinals_fan on 2008-06-10
> **MisfitI38 said:**
> Slack is Linux, with very basic packaging tools and very small repos.
Arch is Linux, with a package manager on steroids and huge repos.

2 different approaches. Try both like handy said.
Slack is about as close to UNIX as you can get while still using Linux - which is why I love it.  Arch's greatest value is its superb package management (don't get me wrong, I like making my own packages, but it's nice to have someone else do the work sometimes).

---

### Post by MisfitI38 on 2008-06-10
> **cardinals_fan said:**
> Slack is about as close to UNIX as you can get while still using Linux - which is why I love it.  Arch's greatest value is its superb package management (don't get me wrong, I like making my own packages, but it's nice to have someone else do the work sometimes).

I have used both and prefer Arch. I find them extremely similar. Arch is more manual to install. Slack's installer is extremely comprehensive, allowing you to install a complete DE (KDE and now Xfce in 12.1). However, Arch is easier to use and add on to because it has so many packages available, easily installable with pacman. 
Personally, I feel that adding software should be as quick, easy and expedient as possible. USING the software is what should consume my time, not searching for build scripts and compiling, etc.
The base systems of the two are very similar. I like Slack's method of simply chmodding a script to add or remove its execution on boot, but Arch's /etc/rc.conf is still more BSDish.
By UNIX you could mean any number of things, though. Slack is famous for being FHS compliant, whereas Arch reserves /usr/local for the user's own use.
Aside from very subtle differences I would say they are 2 of the most similar base systems I can think of.

---

### Post by Methuselah on 2008-06-11
> **MisfitI38 said:**
> I have used both and prefer Arch. I find them extremely similar. Arch is more manual to install. Slack's installer is extremely comprehensive, allowing you to install a complete DE (KDE and now Xfce in 12.1). However, Arch is easier to use and add on to because it has so many packages available, easily installable with pacman. 
Personally, I feel that adding software should be as quick, easy and expedient as possible. USING the software is what should consume my time, not searching for build scripts and compiling, etc.
The base systems of the two are very similar. I like Slack's method of simply chmodding a script to add or remove its execution on boot, but Arch's /etc/rc.conf is still more BSDish.
By UNIX you could mean any number of things, though. Slack is famous for being FHS compliant, whereas Arch reserves /usr/local for the user's own use.
Aside from very subtle differences I would say they are 2 of the most similar base systems I can think of.

From reading about them, that's close to my evaluation of the differences too. I don't really find pleasure in doing the repetitive tasks that a computer can easily handle. Arch's package manager with a large repository and a build system for when you need to create your own packages is a huge draw. I really appreciated FreeBSD's package management and build system.

---

### Post by Dr Small on 2008-06-11
So far, I have only needed to make a few of my own packages. The rest I found in the repositories or simply on the AUR and just made them that way. You don't have to create every package, just to use it, though.

---

### Post by fwojciec on 2008-06-11
Crux is another good option if you're looking for a hands-on Linux distro that's similar to BSD.  I've never used BSD, to be honest, but based on what I've read I'd venture a guess that Crux is the most BSD-like Linux distro out there (it uses a ports system, for example).  It's definitely worth considering.  It takes some effort to set it up initially, since it comes with plain vanilla everything, but once it's up and running it's rock-solid, predictable, transparent, and faster then any Linux distro I've tried.

If, on the other hand, your most important consideration is convenience and ease of maintenance Arch is as good as it gets, IMO.

---

### Post by ch_123 on 2008-06-11
> Arch's package manager with a large repository and a build system for when you need to create your own packages is a huge draw. I really appreciated FreeBSD's package management and build system.

Have you heard about Yaourt? Its an improved version of Pacman which by and large automates the build process for AUR packages. I was having my doubts about Arch before I found it, but I now must say that its the best package system Ive ever used.

---

### Post by kalpik on 2008-06-11
Is there any any difference in the number of packages available on i686 and x86_64? Last time i heard, x86_64 was seriously lacking packages.. That's one thing that's keeping me from trying out Arch.

---

### Post by handy on 2008-06-12
> **kalpik said:**
> Is there any any difference in the number of packages available on i686 and x86_64? Last time i heard, x86_64 was seriously lacking packages.. That's one thing that's keeping me from trying out Arch.

Yes, there is a difference, there are less packages for 64bit.

Having said that, I use 64bit Arch, & rarely have a problem, usually if there is one it is just a matter of a very simple edit (the opportunity for which is offered) in the installation process & the package works fine in 64bit.

You may have different needs than I, if it is very important you can revue the packages available, or search out your specific needs in the [***_Arch repo's_***]("http://www.archlinux.org/packages/") & in [***_AUR_***]("http://aur.archlinux.org/packages.php").

---

### Post by Methuselah on 2008-06-12
> **fwojciec said:**
> Crux is another good option if you're looking for a hands-on Linux distro that's similar to BSD.  I've never used BSD, to be honest, but based on what I've read I'd venture a guess that Crux is the most BSD-like Linux distro out there (it uses a ports system, for example).  It's definitely worth considering.  It takes some effort to set it up initially, since it comes with plain vanilla everything, but once it's up and running it's rock-solid, predictable, transparent, and faster then any Linux distro I've tried.

If, on the other hand, your most important consideration is convenience and ease of maintenance Arch is as good as it gets, IMO.

thanks for the suggestion, never heard of crux, will look into it.

---

### Post by MisfitI38 on 2008-06-12
While I think CRUX is neat, I find it *too* minimal to be practical as a desktop OS. CRUX and Slack, along with Arch, are all minimal but I find Arch can easily be expanded while the other 2 make me work a little harder to get what I want.
Arch's repos and pacman make the difference for me, while still remaining tiny and light.

---

### Post by fwojciec on 2008-06-12
> **MisfitI38 said:**
> While I think CRUX is neat, I find it *too* minimal to be practical as a desktop OS. CRUX and Slack, along with Arch, are all minimal but I find Arch can easily be expanded while the other 2 make me work a little harder to get what I want.
Arch's repos and pacman make the difference for me, while still remaining tiny and light.

Crux does make you work a bit more but the end result is worth it.  Once all is set up, it's almost as easy to maintain and keep up to date as Arch is.  In my experience Crux makes a wonderful desktop system, although it's possible that the appeal has something to do with the fact that all the effort that goes into fine-tuning everything creates a bias of sorts, and makes you appreciate it more -- in an irrational sort of way ;)

---

### Post by MisfitI38 on 2008-06-12
> **fwojciec said:**
> Crux does make you work a bit more but the end result is worth it.  Once all is set up, it's almost as easy to maintain and keep up to date as Arch is.  In my experience Crux makes a wonderful desktop system, although it's possible that the appeal has something to do with the fact that all the effort that goes into fine-tuning everything creates a bias of sorts, and makes you appreciate it more -- in an irrational sort of way ;)

Hehe. Good point.

---

### Post by kalpik on 2008-06-13
> **handy said:**
> Yes, there is a difference, there are less packages for 64bit.

Having said that, I use 64bit Arch, & rarely have a problem, usually if there is one it is just a matter of a very simple edit (the opportunity for which is offered) in the installation process & the package works fine in 64bit.

You may have different needs than I, if it is very important you can revue the packages available, or search out your specific needs in the [***_Arch repo's_***]("http://www.archlinux.org/packages/") & in [***_AUR_***]("http://aur.archlinux.org/packages.php").
Thanks. Im on Arch right now.. And im not missing anything! yaourt is great!

---

### Post by handy on 2008-06-14
> **kalpik said:**
> Thanks. Im on Arch right now.. And im not missing anything! yaourt is great!

Have a look at [***_tupac_***]("http://wiki.archlinux.org/index.php/TuPac"), it can make the process of installing packages much quicker.

---

### Post by Nessa on 2008-06-15
How is arch in a linux multi-boot setup?

---

### Post by handy on 2008-06-15
Arch uses GRUB, I can't see why it would behave any differently to any other Linux distro'?

I run Arch & Leopard on an iMac, others run Arch, Leopard & Windows on Macs, I can't see it getting anymore difficult than that with my limited knowledge.  & it is not difficult to set up, due to the fantastic installation instructions on the Arch Wiki & the additional help in the Arch Forums.

Have a look at the [***_Arch Wiki_***]("http://wiki.archlinux.org/index.php/Table_of_Contents_%28English%29") & the [***_Arch Forums_***]("http://bbs.archlinux.org/")?

The [***_Beginners Guide_***]("http://wiki.archlinux.org/index.php/Beginners_Guide") is an excellent & comprehensive Arch installation guide.

The [***_Arch How-To pages_***]("http://wiki.archlinux.org/index.php/Category:HOWTOs_%28English%29") are great too.

---

### Post by Methuselah on 2008-06-15
Just loaded it in a VM and ran through the installation to get an idea of how it works. Nice transparent system so far.

---

### Post by CJ56 on 2008-06-25
How would Arch compare in everyday use with Zenwalk? 

I'm using Zenwalk 5.2 at the moment & I love the simplicity & speed. But the thought of an even thinner OS appeals - there are probably only about 15 applications I ever use. I also like a reasonable GUI, in fact I'm a Gnome fan (yes) & even use bits of Compiz regularly when I'm on Ubuntu. 

The computer's a desktop, standalone, ethernet connection, very basic setup, although probably more brainpower than I strictly need - AMD64x2 plus 2Gb RAM.

I actually had a stab at Arch a while ago, one of those dead of night things, pretty sure I missed out a page of the instructions, got a sort of recognisable desktop but with bits missing, packed it in & forgot about it. 

So there's the challenge of getting it all working - okay, but I bet it'll take me a couple of goes (or more) to get right. Just suppose I did, though, would I be much better off in terms of speed/functionality/good looks or whatever than with the Zen? After all, I have make my living on this thing, so I shouldn't really spend hours tweaking & breaking & rebuilding...

Anyway. All comments welcomed....

---

### Post by Barrucadu on 2008-06-25
Well, I dropped Zenwalk for Arch, if only for the better package management. I remember Zenwalk was also very fast on this machine, and Arch is very fast - so speed difference may not be such a big concern.
One big advantage to you could be the rolling-release method. You wouldn't have to upgrade to a new release whenever one is finished (as with Zenwalk and most other distros), but you would just have to issue one command to get the most up-to-date system.

---

### Post by MisfitI38 on 2008-06-25
There's no longer any excuses to fail at installing Arch.....
because the Beginner's Guide is now included on the installer iso!
;)
```
cat /arch/beginnersguide.txt | less
```

---

### Post by Dr Small on 2008-06-25
> **MisfitI38 said:**
> There's no longer any excuses to fail at installing Arch.....
because the Beginner's Guide is now included on the installer iso!
;)
```
cat /arch/beginnersguide.txt | less
```
Ha! I never new that. I guess that would come in handy.

---

### Post by MisfitI38 on 2008-06-25
> **Dr Small said:**
> Ha! I never new that. I guess that would come in handy.

Since 2008-06 iso. :)

---

### Post by Barrucadu on 2008-06-25
*applauds everyone who has contributed to the Beginner's Guide*
Now all we need is a copy of the Jargon File on the installation ISO and in the base installation, and all is good in the world :D

---

### Post by Dr Small on 2008-06-25
> **MisfitI38 said:**
> Since 2008-06 iso. :)
Oh. Well I still have the 2007 iso, though.

---

### Post by handy on 2008-06-26
> **CJ56 said:**
> How would Arch compare in everyday use with Zenwalk? 

I'm using Zenwalk 5.2 at the moment & I love the simplicity & speed. But the thought of an even thinner OS appeals - there are probably only about 15 applications I ever use. I also like a reasonable GUI, in fact I'm a Gnome fan (yes) & even use bits of Compiz regularly when I'm on Ubuntu. 

The computer's a desktop, standalone, ethernet connection, very basic setup, although probably more brainpower than I strictly need - AMD64x2 plus 2Gb RAM.

I actually had a stab at Arch a while ago, one of those dead of night things, pretty sure I missed out a page of the instructions, got a sort of recognisable desktop but with bits missing, packed it in & forgot about it. 

So there's the challenge of getting it all working - okay, but I bet it'll take me a couple of goes (or more) to get right. Just suppose I did, though, would I be much better off in terms of speed/functionality/good looks or whatever than with the Zen? After all, I have make my living on this thing, so I shouldn't really spend hours tweaking & breaking & rebuilding...

Anyway. All comments welcomed....

Do what ***we*** did; try this, then try that, choose what suits YOU & your hardware the best.

There is NO such thing a the best Linux distro' for ALL.

There ARE so many choices, which of course makes all of the Linux distro's & the BSD's (to a much lesser extent only due to numbers), so much fun to be with.

Distro' hop & enjoy, that is how so many of us have found the distro' that suits us best.  

(Which is of course Arch, but I shouldn't have said that, because it is like an end game cheat!)

Sorry that was the biased part of my brain talking, I will endeavor to keep it in check in the future. :lolflag:

---

### Post by BijuMathew on 2008-06-27
I'm on Arch Linux now :). Im amazed I was able to install it . But I had lots of help from the above mention guide and the wiki covers pretty much everything :).

---

### Post by Barrucadu on 2008-06-27
It's not that hard if you follow the beginners guide - just different.

---

### Post by ntu on 2008-07-02
Is arch easy to get working on the net with dialup?

---

### Post by Barrucadu on 2008-07-02
I haven't tried this as I haven't had dialup for about 5 years now, but there is a guide on the Arch wiki that may be what you're looking for; [http://wiki.archlinux.org/index.php/PPPoE_Setup_with_pppd](http://wiki.archlinux.org/index.php/PPPoE_Setup_with_pppd)

---

