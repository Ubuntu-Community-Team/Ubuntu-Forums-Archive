---
title: "Thinking of trying out Arch"
date: 2008-08-06
forum: Arch and derivatives
---

### Post by karellen on 2008-08-06
so any suggestions and advices from the more experienced (in distros like Arch, Slackware, Gentoo and so) would be welcome. I've been a Linux user since 2003, but I've always used the so-called user friendly-painless to install&use distros like opensuse (suse back in 2003), Fedora, Ubuntu or Mandriva. I've played a little with Slackware, but I found it too "barebone" (no package manager!!) for my needs. but the last yeas I heard only good things about Arch so I'm considering installing it in order to see for myself that the hype is all about (many members of these forums say, in one thread or another, that they are Arch user and they'd never use something else)...
thoughts? :)

---

### Post by kpkeerthi on 2008-08-06
Arch is a fine distro. I migrated from Ubuntu 8 months back and never looked  back. 

To help you get started...
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
[http://wiki.archlinux.org/index.php/Post_Installation_Tips](http://wiki.archlinux.org/index.php/Post_Installation_Tips)
[http://wiki.archlinux.org/index.php/Configuring_network](http://wiki.archlinux.org/index.php/Configuring_network)

**EDIT:** Most new users struggle a bit to configure 'X'. The easiest route to work this around is to use the xorg.conf from Ubuntu Live CD and copy it over Arch's.

---

### Post by RiceMonster on 2008-08-06
You've been using Linux longer than me; you can definitely tackle it. If your only complaint with Slackware was the package management, then you should like arch. It's got a really good package manager.

Just remember, you start off with just a command line, and you have to install and configure everything else yourself (with the package manager, of course). All the packages are vanilla. Just follow the beginners guide in the wiki and everything will go smoothly.

---

### Post by karellen on 2008-08-06
thanks for the quick responses. I saw that Arch has a pretty neat documentation, I should be able to have a hassle-free installation and post install configuration :)

---

### Post by kpkeerthi on 2008-08-06
You seem to be pretty experienced with Linux. I'm sure you'll be able to appreciate Arch's philosophy and Arch's way of doing things. My only suggestion to you is spend some time reading Arch's wiki. That's the best documentation I could suggest. Do read about [pacman]("http://wiki.archlinux.org/index.php/Pacman"). You can do some neat things with it. I find Arch's [forum]("http://bbs.archlinux.org/") very helpful, friendly and experienced. Good luck.

:)

---

### Post by handy on 2008-08-06
If I can set up Arch & Openbox you can.

I expect that you will be really pleasantly surprised by how excellent the Beginners Guide documentation is, & once installed you will say to yourself, "hey, that was so much easier than I thought it would be!".  The simple Arch design, in combination with the excellent documentation are the factors that make it easier.

It is highly likely that you are really going to love the Arch way! :-)

Another thing that is nice, is that apart from the fantastic Arch Wiki/forum, there is a growing number of Ubuntu forum users that are now Arch users, or use both distro's.  So you can find great support (though naturally more limited) right here.

---

### Post by kelvin spratt on 2008-08-06
Arch is very good once setup they use a slightly different approach to other distros in their philosophy, with the K.I.S.S. principle they don't mess with software code for any software ie, xyz, is not patched to work in Arch as they believe the developer knows best. This approach really seems to work with Arch, most of the time. Sidux is also very good and can be as simple or hard all depends on you, Their are scripts for most things for the normal user, or bare bones for the really experienced but no security updates but that does not pose problems for most as it always uses the latest Sidux coding. Gentoo to me is just to much labour intensive, but can be really good if you have time to constantly adjust things. Then their is my personal favourite Parsix set-up and forget basically uses Debian testing, they all suffer a breakage from time to time, but Sidux,Arch,Parsix, really do work at fixing things in the shortest possible time or give workarounds if its a upstream problem. I think the wait till the next release to fix things is not the way to go, all the above are rolling release systems, but Parsix does it slightly different as it uses snapshots that, all you do is change the distro name ei, Ramon, to Viola,, and distro upgrade, that's it the latest is boss it just builds on from viola, slowly building up to the official Boss nova release later in the year. The devs are allso always checking the forums for problems and very helpful In Sidux,parsix,  The Arch wikki is exellent.

---

### Post by K.Mandla on 2008-08-06
Take a second to look at the internal workings of your Ubuntu system -- find out which modules are installed, what hardware is in use, what network settings are in place, and write them down before you try installing Arch. It might help you troubleshoot something in the future, if you find it doesn't work quite right.

That's the only suggestion I have offhand, anyway. :roll:

---

### Post by karellen on 2008-08-06
:) well there seems to be a considerable number of Arch users here on ubuntuforums, judging from the replies. I'll read carefully the wiki and then give it a try. it may sound odd, but I became bored by all those dull installers "next->next->..." and maybe I need something else to put me to work
thanks everybody :)

---

### Post by CJ56 on 2008-08-06
Well I've been trying out Arch for the last few weeks and I have to say that it's an interesting challenge installing (but, like they say, just follow the instructions to the letter & it works) & very satisfying when you get it set up just how you like it. The only things that stop me from going all the way are

a) pacman (the package manager) seems to have a mind of its own - when I update the system I tend to get worryingly vast downloads of stuff, now including 100s of Mbs of Kde apps, which is odd since I thought I was running a Gnome-only environment. I guess I must have a Kde-related application in there somewhere, but I'm getting the feeling that things are now not quite under my control & do I really want to spend time weeding out the problem? Which leads me to 

b) The tweaking & tinkering is very absorbing but it's in danger of turning a working tool into a hobby, which I can't really afford to do

c) I tried out Ubuntu 8.04.1 the other day & to my slight annoyance it delivered a better-looking & more polished system than the one I spent so long building up with Arch. And you can install Ubuntu in your sleep, in comparison with Arch

So now I'm not sure what I think...and am using Ubuntu 8.04.1 right now

That said, it's definitely worth trying Arch out. I preferred it to Debian & OpenSuse by a mile, you do learn a bit about the underlying structure of a Linux distro & it would still be my no.1 distro if it wasn't for point c) above...

Erm...

Hope this helps... ;)

---

### Post by karellen on 2008-08-06
> **CJ56 said:**
> Well I've been trying out Arch for the last few weeks and I have to say that it's an interesting challenge installing (but, like they say, just follow the instructions to the letter & it works) & very satisfying when you get it set up just how you like it. The only things that stop me from going all the way are

a) pacman (the package manager) seems to have a mind of its own - when I update the system I tend to get worryingly vast downloads of stuff, now including 100s of Mbs of Kde apps, which is odd since I thought I was running a Gnome-only environment. I guess I must have a Kde-related application in there somewhere, but I'm getting the feeling that things are now not quite under my control & do I really want to spend time weeding out the problem? Which leads me to 

b) The tweaking & tinkering is very absorbing but it's in danger of turning a working tool into a hobby, which I can't really afford to do

c) I tried out Ubuntu 8.04.1 the other day & to my slight annoyance it delivered a better-looking & more polished system than the one I spent so long building up with Arch. And you can install Ubuntu in your sleep, in comparison with Arch

So now I'm not sure what I think...and am using Ubuntu 8.04.1 right now

That said, it's definitely worth trying Arch out. I preferred it to Debian & OpenSuse by a mile, you do learn a bit about the underlying structure of a Linux distro & it would still be my no.1 distro if it wasn't for point c) above...

Erm...

Hope this helps... ;)

considering that right now I'm using Mandriva 2008.1 I definitely know what you mean ;). but I guess I just want a challenge :)

---

### Post by mips on 2008-08-06
It really is a nice distro and not hard when you follow the beginners guide wiki.

Just something I remembered that might be of use to you. When asked what editor to use during the install select vi instead of nano. At some stage you are going to be represented with some config files like fstab, grub etc. I always add vga=795 to my kernel line in grub to get a higher resolution in cli when I boot up. Nano somehow screwed up my grub menu. I googled the issue and noticced some other people also experienced this issue so I now use vi during the arch setup. This does not happen to everyone but it did to me and a few others.

I would also recommend the FTP install iso cd if you are installing with a WIRED LAN connection. Why? If you install with FTP you get the latest packages as opposed to the cd which will be a bit older and require you to do another biggish upgrade after install in order to be up to date.

---

### Post by handy on 2008-08-06
> **CJ56 said:**
> 
Well I've been trying out Arch for the last few weeks and I have to say that it's an interesting challenge installing (but, like they say, just follow the instructions to the letter & it works) & very satisfying when you get it set up just how you like it. The only things that stop me from going all the way are

a) pacman (the package manager) seems to have a mind of its own - when I update the system I tend to get worryingly vast downloads of stuff, now including 100s of Mbs of Kde apps, which is odd since I thought I was running a Gnome-only environment. I guess I must have a Kde-related application in there somewhere, but I'm getting the feeling that things are now not quite under my control & do I really want to spend time weeding out the problem? Which leads me to 

This problem could be self created, no offense intended. ;-)

> **CJ56 said:**
> 
b) The tweaking & tinkering is very absorbing but it's in danger of turning a working tool into a hobby, which I can't really afford to do 

The benefit of the rolling release system, is that once you have tweaked your system, which, by the way, you are doing with everything you choose to install or not install, you don't have to do it again until a major hardware problem causes it.

Also, you may not have thought about the benefits of creating a backup of all the required .conf files that matter, to use as a reference if you ever have to do a reinstall of Arch, in the future.

> **CJ56 said:**
> 
c) I tried out Ubuntu 8.04.1 the other day & to my slight annoyance it delivered a better-looking & more polished system than the one I spent so long building up with Arch. And you can install Ubuntu in your sleep, in comparison with Arch 

Having such a HUGE range of Linux distro's is an absolute blessing.  It is how Linux & to a lesser degree the BSD's satisfy the great variety of users extant.

Long live freedom of choice & the huge variety of products that are sourced from individual creativity. :KS

---

### Post by handy on 2008-08-06
> **mips said:**
> 
It really is a nice distro and not hard when you follow the beginners guide wiki.

Just something I remembered that might be of use to you. When asked what editor to use during the install select vi instead of nano. At some stage you are going to be represented with some config files like fstab, grub etc. I always add vga=795 to my kernel line in grub to get a higher resolution in cli when I boot up. Nano somehow screwed up my grub menu. I googled the issue and noticced some other people also experienced this issue so I now use vi during the arch setup. This does not happen to everyone but it did to me and a few others. 

I did not have that problem...

& that is how it is with Linux/BSD, eh!?

> **mips said:**
> 
I would also recommend the FTP install iso cd if you are installing with a WIRED LAN connection. Why? If you install with FTP you get the latest packages as opposed to the cd which will be a bit older and require you to do another biggish upgrade after install in order to be up to date.

On the above I agree with mips, with the proviso that you know what you are doing in *that* regard.  If you don't, do it the other way, & pay a little time & bandwidth while it does the upgrade thing, it has worked for me.

The simplicity of Arch, in many, but not all, areas, makes it easier to get to where you are going. That may sound arrogant?  After you use Arch for a while please tell me where I am wrong? :lolflag:

---

### Post by karellen on 2008-08-06
thanks for the tip mips, I'll keep that in mind ;)

---

### Post by andrek on 2008-08-06
I've got some experience from Ubuntu and Debian and I can say that Arch isn't that hard. Actually, it's very straightforward.
During installation, it automatically detects all the needed modules ( hwdetect ). Installing xorg is very easy and xorg.conf is being configured automatically by hwd.

Pacman seems to be great, except the fact it is a bit slower than apt-get. AUR seems to be a wonderful feature to me - lots of -git packages, voting system..

Arch made me surprised only once - when I tried opening xfce's terminal by typing 'xfce4-terminal' ( just like on ubuntu or debian ). It turned out that the correct name of it is just 'terminal' :)

---

### Post by cardinals_fan on 2008-08-06
Arch is really quite easy.  Follow the beginner's guide and "pacman -S" everything you need.  Once you're set up, the system is very easy to maintain.

---

### Post by Pogeymanz on 2008-08-06
> **andrek said:**
> 
Pacman seems to be great, except the fact it is a bit slower than apt-get. AUR seems to be a wonderful feature to me - lots of -git packages, voting system..


This shouldn't be true. You're are the only person I've heard say that pacman is slower than apt. What filesystem are you using for the partition that has /var? Are you sure your mirrorlist is ordered correctly?

---

### Post by mips on 2008-08-07
> **Pogeymanz said:**
> This shouldn't be true. You're are the only person I've heard say that pacman is slower than apt. What filesystem are you using for the partition that has /var? Are you sure your mirrorlist is ordered correctly?

Have to agree with you. Regardless of the file system I still think it is faster than apt as I have tried ext3, xfs and currently using reiserfs for /var and will all of these I found it faster than apt.

---

### Post by kpkeerthi on 2008-08-07
I don't want to start pacman / apt war. My /var is on ext3 and pacman is definitely faster than apt.

Both are great package managers, though, I find pacman superior ;) in every aspect.

---

### Post by darrenn on 2008-08-07
I will wait until I read the posts that say im leaving ubuntu for arch. Then I will be interested in trying it out.

---

### Post by mips on 2008-08-07
> **darrenn said:**
> I will wait until I read the posts that say im leaving ubuntu for arch. Then I will be interested in trying it out.

I do not think that will EVER happen as they target different audiences. So don't waste your time waiting, just continue using Ubuntu.

Edit: Many people here have actually left Ubuntu for Arch but I really cannot see everybody leaving Ubuntu for Arch.

---

### Post by powerpleb on 2008-08-07
> **mips said:**
> 
Edit: Many people here have actually left Ubuntu for Arch but I really cannot see everybody leaving Ubuntu for Arch.
I've been using Linux for 6 months now and I'm in the process of leaving Ubuntu for Arch. I still have Ubuntu on my desktop, because it's a more powerful computer than my laptops, but I imagine if anything happened to it and I was required to reinstall I'd use Arch.

Don't get me wrong I think Ubuntu is brilliant and I think it's an excellent springboard from OSs like Windows and OSX into Linux. I just like to be able to learn more about my OS when I install/configure/maintain it and Ubuntu simply doesn't offer that. Ubuntu was great when I was a newbie, now I know what I'm doing I find using Arch a much more satifying experience.

---

### Post by sultanoswing on 2008-08-07
+1 another Arch user. I've only just moved to Arch from Ubuntu (Gentoo and Fedora before Ubuntu) a few weeks ago and it looks like I'll stay with it for the following reasons:

1) up to date packages and binary package management via pacman
2) rolling release
3) Arch Build System (when dipping into source is needed)
4) It really is simple to set up and configure through /etc/rc.conf (and strictly, it's not a text installer, but a ncurses one!)
5) Minimal bloat
6) The customisability without the hassle of compiling everything from source a la gentoo
7) the wiki and forum is excellent and fiendly (like here!)
8) The elegant simplicity

While I still give big props to Ubuntu and the team, and am continuing to use Hardy x64 on my laptop, Arch is a great distro and I recommend it!

---

### Post by handy on 2008-08-07
> **powerpleb said:**
> I've been using Linux for 6 months now and I'm in the process of leaving Ubuntu for Arch. I still have Ubuntu on my desktop, because it's a more powerful computer than my laptops, but I imagine if anything happened to it and I was required to reinstall I'd use Arch.

Don't get me wrong I think Ubuntu is brilliant and I think it's an excellent springboard from OSs like Windows and OSX into Linux. I just like to be able to learn more about my OS when I install/configure/maintain it and Ubuntu simply doesn't offer that. Ubuntu was great when I was a newbie, now I know what I'm doing I find using Arch a much more satifying experience.

I agree with you completely, Ubuntu is in my opinion the best jumping off point with regard to leaving the Windows & OSX platforms.  Especially Windows as OSX is so much more closely related. (Even if those users don't know it!)

---

### Post by grndrush on 2008-08-07
Mips wrote:

> Just something I remembered that might be of use to you. When asked what editor to use during the install select vi instead of nano. At some stage you are going to be represented with some config files like fstab, grub etc. I always add vga=795 to my kernel line in grub to get a higher resolution in cli when I boot up. Nano somehow screwed up my grub menu. I googled the issue and noticced some other people also experienced this issue so I now use vi during the arch setup. Interesting. I've been using Arch for over 2 years and never TOUCHED vi (yes, I use sudo, even). Nano is MUCH more intuitive (relatively speaking, for sure) for most people coming from a Windows environment. And nano has never screwed up a single file of mine, to my knowledge. *I* have, but not nano, LOL.

FWIW, I have a VERY hi-end (CRT) monitor (Samsung SyncMaster 955DF, 19-inch, 350MHz pixel clock), and vga=794 is it's limit (although X gladly runs it at 24-/32-bit color, 1024x768@100Hz, 1792x1344@60Hz; go figure...). vga=795 locks the machine in GRUB.

...and...

> Edit: Many people here have actually left Ubuntu for Arch but I really cannot see everybody leaving Ubuntu for Arch.Well, I'm one in the process. I'm not planning to REMOVE my Arch install (it seems that having 2 distros installed can be quite handy sometimes, so you can fix one from the other). Why add Ubuntu? Stability and community are big draws, but imagine my jaw hitting the floor when, using an IDENTICAL xorg.conf file (and no hidden tricks***), Ubuntu ran glxgears *30%* faster, gltron 20% faster, and several other graphical tests I ran showed similar results, for the most part. Might be my hardware, I don't know, but while Ubuntu is so as heck to boot, it seems FASTER (to ME) while running. I'll trade an extra minute to boot 3x a week for 20%+ faster graphics all week long ANY day!

***Ubuntu was running x86_64, and Arch i686; but Arch's scores for the listed benchmarks in the 2 modes were virtually identical.

I'll keep both distros on my machine, but my suspicion is that Ubuntu will be my primary platform.

---

### Post by voteforpedro36 on 2008-08-07
Go for it man, but be prepared to screw up somewhere. I installed it twice this week (the first time I couldn't configure X, but I was trying to use a different driver than I should have), and the second time it only took about 20 minutes. Have fun!

---

### Post by handy on 2008-08-07
> **grndrush said:**
> Mips wrote:

Interesting. I've been using Arch for over 2 years and never TOUCHED vi (yes, I use sudo, even). Nano is MUCH more intuitive (relatively speaking, for sure) for most people coming from a Windows environment. And nano has never screwed up a single file of mine, to my knowledge. *I* have, but not nano, LOL.

FWIW, I have a VERY hi-end (CRT) monitor (Samsung SyncMaster 955DF, 19-inch, 350MHz pixel clock), and vga=794 is it's limit (although X gladly runs it at 24-/32-bit color, 1024x768@100Hz, 1792x1344@60Hz; go figure...). vga=795 locks the machine in GRUB.

...and...

Well, I'm one in the process. I'm not planning to REMOVE my Arch install (it seems that having 2 distros installed can be quite handy sometimes, so you can fix one from the other). Why add Ubuntu? Stability and community are big draws, but imagine my jaw hitting the floor when, using an IDENTICAL xorg.conf file (and no hidden tricks***), Ubuntu ran glxgears *30%* faster, gltron 20% faster, and several other graphical tests I ran showed similar results, for the most part. Might be my hardware, I don't know, but while Ubuntu is so as heck to boot, it seems FASTER (to ME) while running. I'll trade an extra minute to boot 3x a week for 20%+ faster graphics all week long ANY day!

***Ubuntu was running x86_64, and Arch i686; but Arch's scores for the listed benchmarks in the 2 modes were virtually identical.

I'll keep both distros on my machine, but my suspicion is that Ubuntu will be my primary platform.

You find Ubuntu to be faster than Arch?

This seems impossible to me, but I am open minded on the subject.

Please give us lots of details?

---

### Post by mips on 2008-08-07
> **grndrush said:**
> Mips wrote:

Interesting. I've been using Arch for over 2 years and never TOUCHED vi (yes, I use sudo, even). Nano is MUCH more intuitive (relatively speaking, for sure) for most people coming from a Windows environment. And nano has never screwed up a single file of mine, to my knowledge. *I* have, but not nano, LOL.


I myself never use vi. This issue was very specific to the grub menu file. To the eye it looked fine in nano but on reboot you got grub errors. I found references of this happening to a 'few' others as well and the solution was to use vi instead of nano. One of those obscure things in life I suppose.

As for Ubuntu running faster than Arch I find that very hard to believe but I am more than willing to look at comparative benchmarks.

---

### Post by handy on 2008-08-07
The only time I have had need to use vi is when setting up sudo.

Under such circumstances the ***visudo*** command calls vi loaded with the sudo config file ready for editing.

Actually the other time I may need to use vim is when merging .conf files after a pacman -Syu where I may have to use the following command:

***vimdiff file.conf file.conf.pacnew ***

---

### Post by Lod on 2008-08-07
> **mips said:**
> I myself never use vi. This issue was very specific to the grub menu file. To the eye it looked fine in nano but on reboot you got grub errors. I found references of this happening to a 'few' others as well and the solution was to use vi instead of nano. One of those obscure things in life I suppose.

As for Ubuntu running faster than Arch I find that very hard to believe but I am more than willing to look at comparative benchmarks.I had similar troubles with nano myself a few years ago. I read once on a site (I believe it was the unofficial Ubuntu startersguide) that it has something to do with the word wrapping of nano. You have to start nano with the -w option:
```
nano -w <<file>>
```
-w means disable word wrap. Ever since I use this I have no problems at all. Hopefully it's helpfull.

Ontopic: I find Arch very interesting. On the other hand, I like an OS to work as is, I'm not very into tweaking or building myself. So I'm not so sure if I'm fit to use Arch. Nevertheless I think I'm going to give it a try someday soon.

---

### Post by grndrush on 2008-08-07
Mips wrote -
> I myself never use vi. This issue was very specific to the grub menu file. To the eye it looked fine in nano but on reboot you got grub errors. I found references of this happening to a 'few' others as well and the solution was to use vi instead of nano. One of those obscure things in life I suppose.Any idea *what* nano did wrong? A null char, or a CR/NL, or something? It's been my faithful companion - except for when I borked /etc/sudoers with it, LOL. Bless Live/Rescue CD's!
> As for Ubuntu running faster than Arch I find that very hard to believe but I am more than willing to look at comparative benchmarks.Again, as previously stated, MY jaw hit the floor! This COULD be an equipment configuration issue; I have a sortof weird motherboard (an ASUS that not too many of ever got sold), Ath64 XP3500+, only 512MB, and, worst, an ANCIENT GeForce2 MX/400 AGP 4x video card (and, of course, I was benchmarking graphics, not the processor).

Using the 2.6.24 kernel and the nvidia-glx v. 96.43.05 drivers (installed via the relevant package managers), I clocked the folllowing (I know they are pathetic numbers, but they are apples-to-apples comparisons):

Test/FPS-Arch-Ubuntu
glxgears/300-390  !!!
gltron/40-48
lbreakout2/895-1075

I would've thought any of these tests on either setup would be limited by the video hardware completely. To have THREE benchmarks turn out as above was as head-turning to me as to you, I assure you!

Handy wrote:
> The only time I have had need to use vi is when setting up sudo.There ARE ways around that...   :)
> Under such circumstances the ***visudo*** command calls vi loaded with the sudo config file ready for editing.I'm sure you're familiar with the EDITOR visudo variable? You CAN actually, legally, supportedly, use nano as your sudo editor! Visudo syntaxes the result before saving just as it would were vi/m the editor being used.
> Actually the other time I may need to use vim is when merging .conf files after a pacman -Syu where I may have to use the following command:
***vimdiff file.conf file.conf.pacnew***AUR: pacdiffviewer   :)

I think that package is "just a bit" smaller than vim.   :) :) :)

Blue Skies...K

---

### Post by grndrush on 2008-08-07
> I had similar troubles with nano myself a few years ago. I read once on a site (I believe it was the unofficial Ubuntu startersguide) that it has something to do with the word wrapping of nano. You have to start nano with the -w option:GMTA, LOL - see my response above. I'd bet dollars to donuts that was the culprit - I've seen it listed as a gremlin more than once in the past. With a 143-column-wide screen, word-wrap RARELY matters to me...
> Ontopic: I find Arch very interesting. On the other hand, I like an OS to work as is, I'm not very into tweaking or building myself. So I'm not so sure if I'm fit to use Arch. Nevertheless I think I'm going to give it a try someday soon.Give it a try when you have some free time - it's an efficient, interesting, and easy-to-install O/S. However, it's NOT an Ubuntu - there are sysadmin tasks that take some time (IMX, usually unexpected, and when you have the least amount of time to fix the problem - hence the desireability to have 2 distros available).

You spend more than a bit of time at the CLI (since "real" geeks can't spell GUI), and they really do mean "bleeding edge" - I've had a number (I DON'T want to come across as sounding like this is routine, because it ISN'T) of times I rebooted after a system update ('pacman -Syu') to either a blank screen or a cryptic message. Note Arch has been my ONLY O/S for at least 2 years now. It ain't all bad, by a long shot, LOL. Indeed, I think that, *ATM*, it's Linux' best-of-breed.

---

### Post by cardinals_fan on 2008-08-07
> **grndrush said:**
> 
Interesting. I've been using Arch for over 2 years and never TOUCHED vi (yes, I use sudo, even). Nano is MUCH more intuitive (relatively speaking, for sure) for most people coming from a Windows environment. And nano has never screwed up a single file of mine, to my knowledge. *I* have, but not nano, LOL.

You must leave the path of evil and come to the goodness that is Vim :)

---

### Post by rsambuca on 2008-08-07
When installing Arch, I was getting frustrated trying to set up sudo with Visudo since I had never used it before.  I am sure it has it's uses, but I am also sure no one will argue that it is not an intuitive program to use!  After 25 minutes, I just wanted to get the machine up and running, so I ended up just editing the /etc/sudoers file with nano, which worked, and only took me about 45 seconds.

---

### Post by cardinals_fan on 2008-08-07
> **rsambuca said:**
> When installing Arch, I was getting frustrated trying to set up sudo with Visudo since I had never used it before.  I am sure it has it's uses, but I am also sure no one will argue that it is not an intuitive program to use!  After 25 minutes, I just wanted to get the machine up and running, so I ended up just editing the /etc/sudoers file with nano, which worked, and only took me about 45 seconds.
I've never used Visudo - I don't see any use for sudo in general.  Su to root, complete your business, and exit to a normal user.

---

### Post by RiceMonster on 2008-08-07
I use sudo because I'm just used to using it. Plus, I don't like switching back and forth between users. With sudo, I can string super user and regular user commands together (with &&). It's really just a matter of preference. Neither is better.

---

### Post by grndrush on 2008-08-07
> **cardinals_fan said:**
> You must leave the path of evil and come to the goodness that is Vim :)

LOL - thanks! The fact that I'm basically a bigot against vi(m) got a bit of attention when I borked  /etc/sudoers  and had to ask for help on their forums.

But I wrote my 1st program on a 100-instruction-capacity, 10-memory-location TI-52A calculator around 1976 (it calculated 500000! by adding base 10 logs; it actually ran to completion after 11 hrs, presenting me with a logarithm which admittedly contained a huge rounding error - but it ran!); I've plugged 1's and 0's into mainframe front panels with toggles. We've come a LONG ways since then - I open the man page for vi(m), and immediately feel like someone ordered me to learn WordPerfect or MultiPlan in 2008!!!  IMO, nano, which I know well, is horribly cryptic for a text editor in 2008 (disclaimer: admittedly, good on-line documentation is instantly available, and, besides, I'm old and going senile, LOL).

Maybe if I break a leg and am laid up with only a laptop for 4 months...

---

### Post by sub2007 on 2008-08-07
> **RiceMonster said:**
> I use sudo because I'm just used to using it. Plus, I don't like switching back and forth between users. With sudo, I can string super user and regular user commands together (with &&). It's really just a matter of preference. Neither is better.

I'm quite happy using su or sudo. I only have sudo because it was a dependency for one of my packages (can't remember which one now) and as I'm used to sudo from Ubuntu I nearly always end up using it in preference to su. But if I have to do a lot as root then I prefer to log in with su.

I'm trying to get used to using vim at the moment. I'm not saying it's easy and there's definitely a steep learning curve but the more I use it the more useful it becomes.

---

### Post by grndrush on 2008-08-07
> **handy said:**
> You find Ubuntu to be faster than Arch?

This seems impossible to me, but I am open minded on the subject.

Please give us lots of details?
Well, I posted the benchmarks that so wowed me.

It IS hard to tell. Faster at some things, slower at others. I remember when I was running 64-bit Arch that the system didn't really *benchmark* faster, but *felt* smoother. Those benchmarks I posted (more like observations, really) were from 32-bit Arch. I also haven't re-installed the NVidia drivers in Arch yet (there's a reason), although they WERE in place when I did my timings, of course. I'm looking forward to getting both installs filled out, and maybe running some more vigorous tests.

---

### Post by sub2007 on 2008-08-07
I haven't done any formal tests but I know Arch definitely loads faster for me than Ubuntu. Ubuntu from GRUB to desktop (Xfce with Compiz Fusion and AWN) takes at least two minutes. My setup of Arch (which is identical - Xfce, Compiz and AWN) takes 50 seconds.

Once it's up and running I think I find it impossible to find any speed difference. I would definitely not say that Arch is slower and I never break into my swap in Arch which for some reason even with 1.5 GB of RAM I end up doing on Xubuntu (although it's only a few MB).

---

### Post by K.Mandla on 2008-08-07
> **sub2007 said:**
> I'm quite happy using su or sudo. ... But if I have to do a lot as root then I prefer to log in with su.
I'm embarrassed to say it, but I do this too. :oops: I drifted away from using sudo when I stopped using Ubuntu all the time and I realized how much I preferred just switching to root and giving the commands I want. Of course, you can do that in Ubuntu too, but I'd have to give myself and infraction if I explained how. :lolflag:

Point being, I still install sudo and set it up, but for one reason only: I prefer a [right-click shutdown in Openbox]("http://kmandla.wordpress.com/2007/10/27/howto-shut-down-linux-from-the-openbox-right-click-menu/"). :roll:
> **rsambuca said:**
> When installing Arch, I was getting frustrated trying to set up sudo with Visudo since I had never used it before.  I am sure it has it's uses, but I am also sure no one will argue that it is not an intuitive program to use!  After 25 minutes, I just wanted to get the machine up and running, so I ended up just editing the /etc/sudoers file with nano, which worked, and only took me about 45 seconds.
Thank goodness! Here and I thought I was the only one who edited sudoers with nano. Comrade!
> **sub2007 said:**
> I haven't done any formal tests but I know Arch definitely loads faster for me than Ubuntu. ... Once it's up and running I think I find it impossible to find any speed difference. 
Hmm. For my money, Arch systems are noticeably faster than Ubuntu ones, and not just in startup. It's hard for me to measure though, so I have to just point in the general direction of a perceived performance increase, I guess.

---

### Post by sultanoswing on 2008-08-08
Let me do it for you then ;)

```

sudo passwd root

```

---

### Post by powerpleb on 2008-08-08
> **K.Mandla said:**
> 
Hmm. For my money, Arch systems are noticeably faster than Ubuntu ones, and not just in startup. It's hard for me to measure though, so I have to just point in the general direction of a perceived performance increase, I guess.

I have an Arch laptop with a 2ghz Celeron and the standard Intel onboard Video card running Arch and a Core 2 Duo 2.4Ghz with a pretty decent nVidia 8400GT 512mb graphics card with Hardy (both have 2gb RAM).
Arch is considerably faster in every task except playing DVDs, running Compiz and Google Earth.

---

### Post by mips on 2008-08-08
> **rsambuca said:**
> When installing Arch, I was getting frustrated trying to set up sudo with Visudo since I had never used it before.  I am sure it has it's uses, but I am also sure no one will argue that it is not an intuitive program to use! 

Definately not intuitive. I have learned that all I need to know is "i" for insert, "Esc" to exit insert mode and ":wq" to write and quit. As a general rule I stick to nano though.

---

### Post by RiceMonster on 2008-08-08
After I learnt to use Vi/m properly, nano just feels inefficient, and it wastes screen space. Just take the time to learn it by typing vimtutor in a terminal, or for even more detail, open up vim and type :help. You'll never go back :D.

---

### Post by Barrucadu on 2008-08-08
I edit sudoers with emacs - is that a sin? :p
I don't even have (g)vi(m) or nano installed.

---

### Post by powerpleb on 2008-08-08
> **RiceMonster said:**
> After I learnt to use Vi/m properly, nano just feels inefficient, and it wastes screen space. Just take the time to learn it by typing vimtutor in a terminal, or for even more detail, open up vim and type :help. You'll never go back :D.

I agree, and I am by no means a vi guru. It's got a steep learning curve, but once you become instinctive with a few vi commands editing text files becomes a lot faster and easier. Vimtutor is the way to go, I've even got vi on my browser now with the vimperator plugin, I can navigate the web and never have to touch a mouse.

---

### Post by Patogen on 2008-08-08
> **powerpleb said:**
> I agree, and I am by no means a vi guru. It's got a steep learning curve, but once you become instinctive with a few vi commands editing text files becomes a lot faster and easier. Vimtutor is the way to go, I've even got vi on my browser now with the vimperator plugin, I can navigate the web and never have to touch a mouse.

+1
Once you've learned the basic about vi(m) you never want to go back. Same with vimperator!

---

### Post by RiceMonster on 2008-08-09
I use vimperator too. It rules :D.

---

### Post by basenvironment on 2008-08-09
> **RiceMonster said:**
> I use vimperator too. It rules :D.

vimperator may rule but [conkeror]("http://conkeror.org/") rocks! :lolflag:

---

### Post by handy on 2008-08-09
vim, emacs & the like are great if you do lots of scripting & coding.

If like me you do very little scripting, then is seems to be a waste of time to learn such powerful & unintuitive software.

Simplest & most efficient handling of the .conf .conf.pacnew problem is what I have been looking for in [***_this thread_***]("http://ubuntuforums.org/showthread.php?t=881270").

---

### Post by mips on 2008-08-09
> **Lod said:**
> I had similar troubles with nano myself a few years ago. I read once on a site (I believe it was the unofficial Ubuntu startersguide) that it has something to do with the word wrapping of nano. You have to start nano with the -w option:
```
nano -w <<file>>
```-w means disable word wrap. Ever since I use this I have no problems at all. Hopefully it's helpfull.


Thanks! I will keep "-w" in mind next time.

---

### Post by cardinals_fan on 2008-08-10
> **basenvironment said:**
> vimperator may rule but [conkeror]("http://conkeror.org/") rocks! :lolflag:
Emacs-loving heretic! :twisted:
> **handy said:**
> vim, emacs & the like are great if you do lots of scripting & coding.

If like me you do very little scripting, then is seems to be a waste of time to learn such powerful & unintuitive software.

Simplest & most efficient handling of the .conf .conf.pacnew problem is what I have been looking for in [***_this thread_***]("http://ubuntuforums.org/showthread.php?t=881270").
Aside from some recreational Ruby/Perl, I don't do much scripting.  Once you learn the Vim keybindings, they make things much faster.  I use Vim to write all my school reports - the keyboard control is very useful to me.

---

### Post by Pogeymanz on 2008-08-10
I use both Emacs and Vim! I will bring peace to these rivaling families. They are both wonderful editors.

I'm actually just learning Vim using the tutor, so I can edit basic stuff, but my programming is still done in Emacs.

A lot of vi/m commands are very inuitive. Just keep in mind that you can't just start typing where the cursor is, or else chaos ensues. Type "i" for insert-mode, then you start typing away. Type "dw" for delete word, "u" for undo, "r" for replace, "p" for put (or paste, to most of us). It's actually way more logical than ctrl-v for paste, and ctrl-z for undo.

And I'll admit, none of Emacs key-bindings are intuitive, but I still like it anyway.

---

### Post by Barrucadu on 2008-08-10
> **Pogeymanz said:**
> And I'll admit, none of Emacs key-bindings are intuitive, but I still like it anyway.
Actually, I'll have to disagree. I can think of exactly *one* that is - Ctrl+S to search.

---

### Post by powerpleb on 2008-08-10
> **Barrucadu said:**
> Actually, I'll have to disagree. I can think of exactly *one* that is - Ctrl+S to search.

And / isn't exactly the most obvious choice. But it's a lot faster.

---

### Post by handy on 2008-08-11
I can see the logic in ctrl-v, ctrl-x, ctrl-c & ctrl-s.  Ctrl-z is stretching it some, though the logic there would have been the convenient location with regard to the others just mentioned.

---

### Post by Dr Small on 2008-08-11
> **powerpleb said:**
> And / isn't exactly the most obvious choice. But it's a lot faster.
+1
just like sed :)

You can actually use sed syntax in vim too:
```
:%s/find/replace/g
```

---

### Post by andrek on 2008-08-14
> **Pogeymanz said:**
> This shouldn't be true. You're are the only person I've heard say that pacman is slower than apt. What filesystem are you using for the partition that has /var? Are you sure your mirrorlist is ordered correctly?

I've got / ( including /var ) on a XFS partition.
My pacman.conf :
[http://pastebin.com/d2af06796](http://pastebin.com/d2af06796)

It downloads packages pretty fast but if I want to update db, it goes slow between every repo ( updating core .. long gap .. updating extra .. long gap ). Also, when trying to install something - it *thinks* about it on the start for a several seconds..

---

### Post by fwojciec on 2008-08-14
> **andrek said:**
> I've got / ( including /var ) on a XFS partition.
My pacman.conf :
[http://pastebin.com/d2af06796](http://pastebin.com/d2af06796)

It downloads packages pretty fast but if I want to update db, it goes slow between every repo ( updating core .. long gap .. updating extra .. long gap ). Also, when trying to install something - it *thinks* about it on the start for a several seconds..

Yep. Pacman and XFS don't mix well.  XFS is actually the worst possible filesystem to use for a root partition, at least in my experience.  XFS -- good with single large files, terrible with many small ones.  Root partition -- few or no large files, many many small ones.  It's just a bad tool for the job.

---

### Post by andrek on 2008-08-14
What do you suggest then? I think I'll reinstall the whole system - what filesystem would you advise me?

I'm thinking about 
/boot ext2
/var reiserfs
/home xfs
/ xfs

or perhaps
/boot ext2
/home reiserfs
/ reiserfs

?

---

### Post by fwojciec on 2008-08-14
Ext3 is a safe default, most Arch devs use it, for example.  ReiserFS is for performance, especially with pacman -- it's in class of it's own, but can be quirky and recovery of a broken reiserfs is difficult.  On a laptop JFS might be a better solution, due to its low CPU usage.  If in doubt go with ext3.  I use reiserfs as root on my desktop, ext3 configured like [this]("http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips") for data/storage partitions, and jfs on my laptop (root and home).  If you're thinking of JFS you might want to read [this]("http://http://wiki.archlinux.org/index.php/JFS") first.

---

### Post by andrek on 2008-08-14
I'm not using a laptop ( yet ) and I'd definitely go for performance. I think reiserfs will suit me best. Last question - is there any possibility to avoid wiping out the system in order to change my root partition into reiserfs?

---

### Post by mips on 2008-08-14
> **andrek said:**
> Last question - is there any possibility to avoid wiping out the system in order to change my root partition into reiserfs?

[http://gentoo-wiki.com/HOWTO_Convert_Filesystems](http://gentoo-wiki.com/HOWTO_Convert_Filesystems)

---

### Post by fwojciec on 2008-08-14
Sure there is.  I always follow [this guide]("http://inferno.slug.org/cgi-bin/wiki?Drive_Backup_And_Cloning") when I need to change the filesystem, but it's not an entirely straight forward procedure.  Basically, the "logic" of it is as follows:

1) boot using a rescue cd (rip linux suggested in the guide works great)
2) backup root to another partition (i.e. home) like the guide says
3) fire up gparted, delete old root partition, create new one with the desired filesystem
4) restore root onto the newly created partition (as the guide says)
5) rinse and repeat with any other partition you want to change
6) once all is done make adjustments in /etc/fstab and grub menu.lst, if necessary
7) reinstall grub if necessary

On the first boot you're likely to get a kernel panic, so you'll probably need to boot with either the install cd or the fallback image to regenerate the boot image using mkinitcpio.

Also, keep in mind that the guide was not written for Arch specifically, so you can't just copy things, you'll have to adjust things here and there.

---

### Post by andrek on 2008-08-14
Thanks for your help guys. However, I guess it'll be faster to set up a new installation of Arch ( it does install so fast after all :) ).

*edit:* Forget what I said before about pacman's speed - it's ultra fast now! Thanks guys for pointing me out what I had wrong.

---

### Post by grndrush on 2008-08-15
As stated a few days back, I'm moving in the other direction (I was thinking about it; I'm currently dual-booting both distros). Thought I'd give an update:

Wow. So THIS is how "out of the box" feels! And yes, I'm finding enough combo of info and savvy that I'm getting VERY CLOSE to the same overall experience (speed-wise) I had with Arch. Not fully, but close. And having codecs/drivers/documentation/plug-in wrappers just 'done' (or darned close), and, IMNSHO, I'm saving more time than I'm losing by a LONG stretch (still recovering initial investment, of course, LOL).

---

### Post by Pogeymanz on 2008-08-18
> **Barrucadu said:**
> Actually, I'll have to disagree. I can think of exactly *one* that is - Ctrl+S to search.

Hey, Alt+Shift+5 is pretty intuitive for "search and replace"... right?

---

