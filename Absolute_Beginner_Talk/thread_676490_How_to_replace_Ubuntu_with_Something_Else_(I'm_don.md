---
title: "How to replace Ubuntu with Something Else (I'm done with it)"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by techroach on 2008-01-23
So, I've been playing with Ubuntu for the last 4 months. And in the end I took the decision which I should've done 4 months ago. I know its not meant to be asked here but I think you guys need to know why not just me, but any other guy would prefer quitting Ubuntu.

I know how to install new OS. Thats not what I want. I'm looking for alternatives. I currently run Ubuntu 7.10. Here are my problems :

**1)** **My bootup is dead slow** (1st "logo" bootup takes about 10+ sec and after login, may take 15+ sec) while my WinXP boots up completely in 11sec. 
**2)**** Firefox interface as well as browsing is slow**. Changing tabs is a nightmare. And don't get me started with this **** I call the "**_Black-Out Effect_**" lol. Screenshot at bottom.
**3)** KDE is cooler. Ubuntu is Gnome, isn't it ?
**4)** In windows, I get lightning fast Firefox and bootup and all the software. So, my friends always ask why I still hang out with Linux.

I'm fed up of "mods" by ultra-users since its a pain in the *** to implement and its not permanent. Is this the way Hardy Heron is gonna be ? Then I'm bailing out. So, please help me.

[[IMG]http://img244.imageshack.us/img244/4240/screenshotjw0.th.png[/IMG]](http://img244.imageshack.us/my.php?image=screenshotjw0.png)

---

### Post by Arthur Archnix on 2008-01-23
Fedora 8 is nice. But it uses gnome too. Opensuse is good, I hear, and that's KDE. For faster distributions that are still easy to use you might try Sabayon or Zenwalk (that's slack based I think though, so it might be a little more advanced).

You can find these at [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by jaytek13 on 2008-01-23
Yeah, Fedora and OpenSuse are the next two most common Linux distrubutions to install on your computer. Unfortunately their downloads are HUGE. Both require 6 cd's/1 DVD. At least with Fedora you can download 1 live cd and install a minimal installation with that... OpenSuse, however, does not let you install from their livecd for whatever reason. 

Either way, just to let you know what you're getting into if you switch from Ubuntu to another distro... They are going to require much more time and effort in learning how to do things. Fedora, for instance, is notorious for refusing to include anything considered "non-free" with their distribution... so, manual installs to play mp3's, dvd's, flash, java, etc... That said, they do have their advantages. Both Fedora and OpenSuse are more commonly used in the business environment, so learning them could teach you the technical skills needed to be able to become a redhat or Suse administrator, if you were interested in such a thing.

Additionally, OpenSuse has actually split up their efforts now and are developing/supporting both KDE and Gnome. I'm not sure if this means they took their KDE resources and divided them up, but who knows.

And as far as speed is concerned, honestly Gnome 2.x vs. KDE 3.x, Gnome wins by a large margin. KDE is trying to resolve this with KDE4, but most people consider it unusable at this point in time. 


Anyways, I understand your frustration and there's certainly no harm in trying out other distributions. It's a personal preference, and that's what Linux is all about.

---

### Post by macogw on 2008-01-23
The "blackout effect" is Compiz notifying you if a program freezes.  Sometimes Firefox only pretends to freeze, but I can tell you for sure that Firefox 3 beta 2 (which I got by adding ```
# Firefox 3 Gutsy update
deb http://ppa.launchpad.net/fta/ubuntu gutsy main restricted universe multiverse
deb-src http://ppa.launchpad.net/fta/ubuntu gutsy main restricted universe multiverse
``` to my /etc/apt/sources.list and installing firefox-3.0 from there.)

I know logging into GNOME on Gutsy is really really really too slow.  I have no idea why.  It was fast on Feisty.  *shrug*  I've never heard of XP not waiting a while after login to load up all the startup stuff, though (guessing you tweaked your msconfig?  if you don't, iTunes, QuickTime, Real Player, etc all want to look for updates at boot, and that's really annoying and slow).  Anyway, that's only in GNOME, so if you use KDE (since you said you like it better), that should be fine.

Have you tried Kubuntu?  A lot of my friends like it.  OpenSuSE's KDE is actually *very* neat.  It has a "reboot to other OS" option in the shut down screen, which I think is really cool.  You can just pick which OS you're going to want then, so you can walk away without worrying about missing GRUB's timeout.

Arthur, I don't know what kind of computer you have, but Sabayon makes Vista look fast.

---

### Post by SunnyRabbiera on 2008-01-23
Give mandriva a shot, kde based and much faster then ubuntu for me.

---

### Post by asmoore82 on 2008-01-23
> **techroach said:**
> **1)** **My bootup is dead slow** (1st "logo" bootup takes about 10+ sec and after login, may take 15+ sec) while my WinXP boots up completely in 11sec. 
**2)**** Firefox interface as well as browsing is slow**. Changing tabs is a nightmare. And don't get me started with this **** I call the "**_Black-Out Effect_**" lol. Screenshot at bottom.
**3)** KDE is cooler. Ubuntu is Gnome, isn't it ?
**4)** In windows, I get lightning fast Firefox and bootup and all the software. So, my friends always ask why I still hang out with Linux.

1. A lot of non-essential services are enabled on all "Easy to Install/Use" "Desktop" Linux
systems, Open "System->Administration->Services" and turn off what you don't need.
I noticed also that a lot of new user-space startup stuff was added in 7.10. Open
"System->Preferences->Sessions" and turn off what you don't need.
2. Is it really firefox or is your configuration and Add-Ons? Run the firefox profile manager
by running `firefox -P` from a Terminal(and that must be a capital "P"), then, create
a fresh new profile to browse on and see if it's "fixed." If so, you either need to clean
up your old profile or migrate your bookmarks over to the new profile and keep it clean.
3. ```
sudo apt-get install kubuntu-desktop
```
4. "Your Mileage May Vary" but obviously you know what you are doing in Windows and
can keep it running smoothly. This makes you the exception to the rule and your
experiences are not typical. Your system specs may also be limiting your enjoyment of
Linux and moving from anything else to a good nVidia video card will make Linux 10 times
"zippier" and *feel* much faster. Also, Linux seems to absolutely hate "cheap" CPUs
with skimpy L1 Caches such as Intel Celerons and AMD Durons.

> **techroach said:**
> I'm fed up of "mods" by ultra-users since its a pain in the *** to implement and its not permanent. Is this the way Hardy Heron is gonna be ? Then I'm bailing out. So, please help me.
I don't follow this at all:confused:

---

### Post by buntunub on 2008-01-23
Well, its completely hardware dependent. You need to cross reference your hardware with a suitable Distro/WM. Ubuntu may not be right for you because no matter what version of Buntu you load, it still has the same underpinnings which slow it down. My advice would be to go with base Debian minimal install/XFCE. I think you would experience one massive boost to your systems performance going that route, but it will be a bit harder to setup/configure. A worthy tradeoff in the long run.

---

### Post by dummyhead3 on 2008-01-23
I suggest Gentoo. This requires alot of work to install, but works very fast.

---

### Post by sumguy231 on 2008-01-23
Your friends have a point, why *are* you still using something you hate?

MEPIS is a nice KDE-based distro, by the way.

---

### Post by Kilz on 2008-01-24
> **techroach said:**
> So, I've been playing with Ubuntu for the last 4 months. And in the end I took the decision which I should've done 4 months ago. I know its not meant to be asked here but I think you guys need to know why not just me, but any other guy would prefer quitting Ubuntu.

I know how to install new OS. Thats not what I want. I'm looking for alternatives. I currently run Ubuntu 7.10. Here are my problems :

**1)** **My bootup is dead slow** (1st "logo" bootup takes about 10+ sec and after login, may take 15+ sec) while my WinXP boots up completely in 11sec. 


While you may be on your way to another os, please take a look at this in your next distro. The bootup on windows is an optical illusion. When you boot up windows it does appear to boot up faster. But you cant do anything for a long time after the desktop shows. When running linux, when the desktop shows an application can be started right away.
Is it really faster if you cant use it?

---

### Post by jblackhall on 2008-01-24
Have you considered reinstalling Gutsy without any desktop effects?  I know my computer is a not-so-great system and when I starting playing around with Compiz-fusion, it started going extremely slowly.  I did notice a considerable difference on start-up, among other things.  I never fully uninstalled CF before reinstalling, but so far since I haven't messed with it, my system is running great.  My thought is that desktop effects are causing at least #1&2.  As others have pointed out, Kubuntu is available if you'd like to try KDE.

My concern is that you're comparing XP to a version of Ubuntu with Compiz-fusion desktop effects enabled.  If you're planning to use those, best compare with Vista or another OS with more significant hardware requirements.  Otherwise it's like apples an oranges.  Of course XP seems faster (although as the above user says, I doubt it really is)

---

### Post by housam on 2008-01-24
I agree with Kilz , you cann't start an applications in win-xp before at least 25 sec from start booting . and also compare between vista and gutsy , you'll see the difference.

---

### Post by rockstar on 2008-01-24
I've loved Ubuntu since Edgy and slowly customized things little by little.  I had things the way I wanted with Gusty and Beryl and all kinds of added effects but a my own re-partition error caused a totally wiped hard drive.  my newest re-install caused all kinds of slow boot times and black windows.  One of my forced shutdowns (holding the power button) cause a major malfunction with Gnome and automatically disabled most of the rendering affects which solved my problems.  I'm going to try to update my video drivers and see if that keeps the black boxes away.  I'll probably switch to KDE too, I'd like more control and slimmed down design.

---

### Post by Ex-windows on 2008-01-24
There s also "Fiesty" And in the "Kubuntu" version.
Windows is not faster I have Xp and Vista and the only reason Vista loads fast is the dual core processor and ddr ram lol.But I jsut ran a quick test  againts Feisty in  my older compact and only 4 sec difference. I I also had problem trying to play with some of the Special effects toys on my compaq and had to remove them. Some times it's not the os but the resources available to run it. I ran the l"ive cd "on this new system and it runs faster than Vista and the xp. IBut if you r sure you can also try  knoppix.Yopers (which is kde)  DSL and even Puppy linux And many many others.

---

### Post by maniac_X on 2008-01-24
Win XP boots in 11 secs??? No way!!....YouTube it or it didn't happen. 

Win XP can't even boot that fast on fresh install with nothing else on the drive.

---

### Post by grinias on 2008-01-24
Linux distros are strongly hardware related and your problems may not be solved with another distro. Windows is not a solution at all, as you probably know. Why do not try the suggestions made here for package upgrades, or ubuntu downgrade?

---

### Post by barbedsaber on 2008-01-24
While one distro will work perfectly for one person it just won't for aonother, which is why I recomend [this]("http://www.zegeniestudios.net/ldc/index.php?lang=en") it is by no means perfect, but a hell of a lot better than trying every single distro.

---

### Post by techroach on 2008-01-24
Thansk guys for all the response. But, the thing which bothers me the most is Firefox which is really really really slow. Slow boot-up is another story. 

Anyway, I checked Distro Watch and so a lot of flavors of Linux (they all look the same). I'm hesitant to leave Ubuntu (only if I'm going to stay with Linux that is) since it has the best documentation, support and community.

I tried "Linux Distribution Chooser" and got Ubuntu, OpenSUSE, PCLINUXOS, Mandriva etc. I have to say, I'm confused and a little lazy too (installing another OS is a so shitty). Why does Linux have to be this tough and un-userfriendly ?

My friend told me to use Mac since its also UNIX based. Is he right ? And, I hate to admit it, Windows is really cool man. Its easy and has huge community. I have one big question for you. IS HARDY HERON GOING TO BE THIS WAY ?

---

### Post by techroach on 2008-01-24
> **maniac_X said:**
> Win XP boots in 11 secs??? No way!!....YouTube it or it didn't happen. 

Win XP can't even boot that fast on fresh install with nothing else on the drive.

About this, I currently don't have a cam right now. I think its more than 11 sec but really fast. Really fast, I can say that really safely. 

Hey, Ubuntu Developers, if you're reading this. This is what anyone new to this whole thing would want :
[LIST=1]
[*]Fast Bootup
[*]Average Eye-Candy (Linux is so plane !!)
[*]Less Terminal Usage
[*]Faster Firefox (I know you can't do much since its Mozilla who's being a bitch... but you're requests would carry more weight)
[/LIST]

---

### Post by Kilz on 2008-01-24
> **techroach said:**
> About this, I currently don't have a cam right now. I think its more than 11 sec but really fast. Really fast, I can say that really safely. 

Hey, Ubuntu Developers, if you're reading this. This is what anyone new to this whole thing would want :
[LIST=1]
[*]Fast Bootup
[*]Average Eye-Candy (Linux is so plane !!)
[*]Less Terminal Usage
[*]Faster Firefox (I know you can't do much since its Mozilla who's being a bitch... but you're requests would carry more weight)
[/LIST]

1. It does boot fast if you take into consideration that the windows xp desktop is useless when you see the desktop for a length of time. Ubuntu is ready to go when the desktop shows. Try timing it to first launch of application.
2. Linux is customizable in ways that Windows is not. Every icon, window border, and color is changeable. If you want fancy, you can have it.
3. The terminal is a strength, new users shy away, after 6 months you will wonder why you did. 
4. One solid answer [Swiftweasel]("http://swiftweasel.tuxfamily.org")!

---

### Post by techroach on 2008-01-24
Hey, does Mandriva have good community-backing like Ubuntu. Backing as in, Ubuntu has a big forum and you can get a lot of tutorials and articles about it on the internet. That kinda backing.

Just wanted to know. As you can see, I'm in a state of utter confusion. :(

---

### Post by Taboo Mirage on 2008-01-24
Recommend trying out Debian Lenny line.  If you don't like GNOME, you don't have to use it on pretty much any distribution.  The desktop environment isn't permanent, just like with everything else it is an application and can be uninstalled and replacements reinstalled.  Just because something starts out as GNOME, this doesn't mean you're stuck with GNOME for all eternity. =P  Just install the KDE package and you're away.

I recommend Debian as it's more stable than Ubuntu and the Lenny (or "testing") line is a rolling release of the latest software.  You'll often find it is more up to date than the Ubuntu repositories and you don't have to upgrade your entire OS every 6 months with a new release like you have to do with Ubuntu.

Hope you take my advice under consideration. =P

Take care.

---

### Post by Kilz on 2008-01-24
> **techroach said:**
> Hey, does Mandriva have good community-backing like Ubuntu. Backing as in, Ubuntu has a big forum and you can get a lot of tutorials and articles about it on the internet. That kinda backing.

Just wanted to know. As you can see, I'm in a state of utter confusion. :(

There is no distro that has as much community support as ubuntu. Mandrivia isnt a bad choice, neither would be pclinuxos.

---

### Post by quickshade on 2008-01-24
I use PCLinuxOS. And I love it. Personally it's just a good distro. It runs fast, is well put together and has tons of great software. Your not going to get the easy install of drivers or updates, but it's not really that much harder. (you use synaptics) Personally I would recommend it.

---

### Post by AndyCooll on 2008-01-24
> **techroach said:**
> Hey, does Mandriva have good community-backing like Ubuntu. Backing as in, Ubuntu has a big forum and you can get a lot of tutorials and articles about it on the internet. That kinda backing.

Just wanted to know. As you can see, I'm in a state of utter confusion. :(

It surprises me that Ubuntu is proving sluggish for you. As you can tell from some of these responses, it normally isn't the case. Though I had an ageing laptop that ran fine with Feisty but was virtually unuseable with Gutsy. 

I know you mentioned being "lazy" about installing OS's, however there are alternative ways of looking at other distros without actually replacing Ubuntu at this point.
You could always download a few Live CD's of alternative distros first. Many load as a Live CD (i.e. run in your memory) with an option to install if you like them (Ubuntu, Mepis, PCLinuxOS for instance).
Alternatively you can have a look at them as "virtual" OS's by installing VirtualBox or VMware. I think both of them have versions available for both Linux and Windows.
It would be a shame for you to leave. However, if you did decide to choose an alternative distro it might be worth you choosing one that is Debian based. That way, the help advice received in these forums (and what you've learnt so far) is likely to be easily transeferable (since Ubuntu itself is a Debian based distro).

Someone mentioned that it is Compiz that causes the "fading" effect. You can turn Compiz off if you wish (Preferences > Appearance > Visual Effects).

:cool:

---

### Post by lespaul_rentals on 2008-01-24
Try openSUSE 10.3 KDE before you go.  It's the best distro for new/intermediate users.  Also, Firefox is dang slow on Linux.  You might want to try Opera.  And I totally agree with you, Gnome is horrible while KDE is a dream.  Try a KDE distro (such as the aforementioned openSUSE 10.3 KDE) and I think you will be much happier.

---

### Post by _Azrael_ on 2008-01-24
> **techroach said:**
>  Why does Linux have to be this tough and un-userfriendly ?

Try not to think of Linux  as tough -but rather as a learning curb. I encourage you to stick with it and expand your computer knowledge by continuing to use Linux. If you really dislike the tech (which is what many of us love :)) at least make a contact who would be happy to help you out. But if you're patient, you stand  to gain so many skills just by playing with Linux. 

> 
My friend told me to use Mac since its also UNIX based. Is he right ? 

Your friend isn't right about Mac because it's UNIX based. He's right because it's well designed for the hardware it operates on. Also the software is generally cheaper than Microsoft's (take iWork vs Office 2007 for example). Nothing wrong with a Mac -but it still costs.

> 
And, I hate to admit it, Windows is really cool man. Its easy and has huge community. I have one big question for you. IS HARDY HERON GOING TO BE THIS WAY ?:confused:
I have to disagree with you on this. What is cool about windows? Virus protection hogging your resources? Huge price tags on productivity software? General difficulties when integrating with other OSs? Maybe the games? It's easy to use yes, but very uninspired -and it's monotonous. With windows, you're not really part of a community -rather you are very literally being viewed as a commodity. No amount of next-gen games can make up for that I'm afraid. 

I would advise you do the following:

1) Write down the reasons *why* you want a computer *in the first place.*  (office/info/communication/games) 

2) Take the initiative and try as many OSs as you can to see *how* they can meet your needs. Fortunately this is very easy to do with Linux because it's freely distributed. (The only way you'll know about Hardy will be to try it! ;))

3) When you begin to like one of them, make your decision and be clear about why you will stick with it. 

All the best! I Hope you come to a good solution.

---

### Post by mättu on 2008-01-26
> Windows is really cool man

bye then. You're allways welcome back.

:m)

---

### Post by techroach on 2008-01-27
Actually, the only reason I love Windows is that its fast and easy. Its really really crappy and a total waste of money. It sucks badly. I know. Its just that I didn't have a choice. :(

I think I'm going to try out Hardy Heron. And hey, I love learning new things :). I'm currently learning Python. I know C++. I'm not non-technical. But for some reason, I'm finding Shell hard to learn. I mean, all the tutorials are soo long. I'm kinda busy these days with board exams and all.

Is there any easy Shell tutorials ? I mean, I don't want much deep knowledge. I need to gain some knowledge to get a start. Afterwards, I'll learn it slowly. 

Ubuntu is really slow in my system. Here are the configs :

[LIST]
[*]1.9 GHz Intel Pentium 4
[*]632 MB RAM
[*]40 GB hard drive (Only 15 GB for Linux)
[*]Don't have big music collection or anything  :guitar:
[*]Intel Standard Motherboard 
[/LIST]

And there's another problem. Some of the softwares I install straight from the "Add/Remove Programs" aren't working. For eg, I installed Eclipse and its not working properly. A lot of them. My XMMS doesn't have text in the menus. 

Software installation errors + Slow Boot + Slow Firefox + Shell + Nokia Phone = SCREWED !! :mad:

Is gOS good ? Anyway, I'm planning to stay with Ubuntu as far as possible since I'm a big fan of Open Source. I have took down all your suggestions in a piece of paper. Anyway, so what could be the problem for slowness ? Should I try out the Hardy beta ? I heard its "error jungle".

---

### Post by Incense on 2008-01-27
I sped up my firefox on Ubuntu by installing firefox from the mozilla site, and getting rid of the install from the repos. The easiest way to do this is using a great script called Ubuntzilla. Find out more on the page below. 

[http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")

I noticed an increase in speed, and stability on my system, though your miles may vary. If you would like to hop to another distro, I would have to throw another vote in for openSUSE KDE. It really is fantastic! Or if you just want to go back to windows, then no worries. Do what works best for you. Gnu/Linux is not for everyone.

---

### Post by mahasmb on 2008-01-27
> **techroach said:**
> Thansk guys for all the response. But, the thing which bothers me the most is Firefox which is really really really slow.  

This really sounds like a Firefox problem to me. I use Firefox all the time and it certainly isn't slow. You can't blame how one program runs on an entire OS.

> **techroach said:**
> 
Anyway, I checked Distro Watch and so a lot of flavors of Linux (they all look the same). I'm hesitant to leave Ubuntu (only if I'm going to stay with Linux that is) since it has the best documentation, support and community.

I tried "Linux Distribution Chooser" and got Ubuntu, OpenSUSE, PCLINUXOS, Mandriva etc. I have to say, I'm confused and a little lazy too (installing another OS is a so shitty). Why does Linux have to be this tough and un-userfriendly ?



If you're hesitant to leave Ubuntu and you'd rather not have to install a whole other linux distro, why don't you just go with Kubuntu? You already said you prefer KDE to Gnome.

---

### Post by OldGaf on 2008-01-28
I would go with Debian. With what you learned from Ubuntu, switching to Debian will be easy. I gave up on Kubuntu about 6 months ago due to several issues. I am loving Debian + KDE. Going to give KDE4 a shot next.

---

### Post by techroach on 2008-02-02
I'm currently using Windows right now since I'm having some exams and I'm not in the position to do distro testing. Right now, I just need a fast OS. But, I haven't completely ignored Ubuntu. I'm monitoring its developments. I'm going to hop in for Hardy. 

I'm not much comfortable with Microsoft's philosophies and nor am I comfortable with their security problems. I will jump onto Linux as soon as these exams end. 

And hey, what about BSD ? Is it good ? How is it related to Linux ? Which is better ?

---

### Post by NoVista on 2008-02-02
Why even be concerned with boot up time?
Windows and rebooting go together like ham and cheese.
This is Linux, we don't really ever need a reboot, lol.

---

### Post by steveneddy on 2008-02-02
Sounds like you just need to adjust the "tweaks" to get a desktop that you like.

But install what you like. It's your PC.

---

### Post by Julita on 2008-02-02
I have used PC-BSD. I was positive about it, however, I had a few problems with ADSL. In general, I liked the system very much. I think it would be the best variant for those who would want to switch from Windows. It is quite easy to use, and it requires less resources than Ubuntu.

---

### Post by Michl on 2008-02-03
I juist went through 5 or six distributions, including Fedora 8 and OpenSUSE 10.3 and
I don';t see a difference in speed at all.  They all seemed pretty fast to me.  I also use
windows 2000 and XP, and they do not seem faster.  Loading is MUCH slower, not
only at boot but applications.

---

### Post by TenPlus1 on 2008-02-03
The speed of Ubuntu tends to be hardware specific, but saying that, if you have a good configuration then Ubuntu will literally fly-along faster than anything...

I have an Asus system with AMD 2400+, 768mb memory and 20gb Ubuntu partition and it boots up very quickly and performs well...  Saying that, I do use Opera for my web browser which is definately a LOT faster than Firefox...

One thing I would recommend though, if your into speed, disable the visual effects and check out BUM (Bootup Manager), Services and Session lists...  Then you can enable/disable what you dont need and that tends to give you those precious seconds... Also, disable Indexing cause that usually slows things down also (especially in Windows)...

---

### Post by dannybuntu on 2008-02-05
Hi, I have exactly the same experience with Ubuntu - slow booting. Though I have learned that *fast booting in Windows* was an illusion since you can't pretty much do anything in your Windows desktop right after it shows you the desktop - you have to wait for the other services to load. 

You might be familiar with the Right click + Refresh syndrome. 

Anyway, I have switched from Kubuntu to Debian Etch and I am pretty much happy with it. It is sufficiently faster than Kubuntu when it comes to boot time. 

The funny thing is I haven't broken a thing *yet* in Debian, whereas simple tweaking in Kubuntu caused me lots of headaches. 

I am a Debian user now but have consistently returned here for help on what to do. 

This Ubuntu phenomenon goes beyond the Ubuntu Distributions I can tell you. 

Please do update us on which distro you have chosen. It's all good. No need to Bash (no pun intended) your PC if you don't like a distro. In the end spread some Open Source lovin!

---

### Post by solitaire on 2008-02-05
techroach: i feel for you regarding Nokia support.. ;) But hopefully that will change sooner rather than later :)

You could give "Freespire" a look it is basically a Kbuntu Base with a diffrent Desktop but it's good and you are used to the type of setup.

---

### Post by hyper_ch on 2008-02-05
Bye bye...

---

### Post by maniac_X on 2008-02-09
@techroach

If you want to return to Windows, that's your option. But, as you pointed out earlier, Windows doesn't really give you a lot of choice. It's expensive(if you get it legally), it's expensive to maintain by which I mean the purchases of anti-spy/virus/trogan/etc-ware,firewall and then of course apps. And the fact that recently M$ has installed updates on people even if they didn't want them?!?....I'm sorry, M$ may own the OS but I own the computer and I sure as hell don't want some corporation deciding what I want installed on it. That right there should be a number one reason to hightail it away from Windows as fast as possible.

And no one here is saying that you need to jump into linux all at once...that's the good part. You can set up dual-boot until you feel comfortable enough in leaving Windows. I still use Windows myself but only for gaming mostly because I've been too lazy to try and set up the games I play to get them running in Ubuntu. 

As for your Firefox situation....never seen anything like that. FF works great for me both in Windows and Ubuntu and a coupla other linux distros as well. I would uninstall FF completely and do a fresh install of it. 

In ending I'll say that if you go back to Windows, consider using open source software a little at a time, Things like OpenOffice, Gimp, Pidgin,etc if those are the kind of apps you usually use in Windows. Taking little steps is better than taking no steps to regain your freedom of choice. Open source software is probably the wiser choice because it's unlikely any funny business is going to go on under the hood.

---

### Post by ashmew2 on 2008-02-09
Why dont u just use Windows ?

---

### Post by stalkingwolf on 2008-02-09
> Its just that I didn't have a choice.
You always have a choice.   How long did you use windows before you tried Linux?
should you not give Linux equal time?


On a side note.  To **DUEL** indicates a face to face conflict ( for instance, take 10 paces turn and fire).  
Where as **DUAL** as in Dualboot, indicates 2 items working side by side.  If not in concert at least
in co-existance.

---

### Post by Joeb454 on 2008-02-09
I have to agree with stalkingwolf about the **dual/duel** thing

Though it does always make me chuckle away to myself, imagining Windows/Ubuntu doing the whole 10 paces turn & fire routine :p

---

### Post by Faud on 2008-02-09
Well at least on my system Ubuntu would win, seeing as it does boot up faster.

LOL
Im sorry, couldnt help it.

---

### Post by seventhc on 2008-02-09
I've used FreeBSD and love it, the only reason I'm not using it now is that for some reason it won't install on this machine (hardware related)
But if Ubuntu is getting you frustrated then BSD is most likely not for you either.
Ubuntu is a great distro but I think people tend to forget that they didn't know anything about windows either when they first started using it. Now after years of being a slave to MS when people finally get freedom they realize whoa now I have to readjust.
It is the same with any system you use since all have their own way.
If you can accept the fact that spyware and viruses are a part of everyday life, then by all means stick with windows, if you want to be safe secure and able to customize any aspect of your machine then use ubuntu or any other distro that you like. No matter what, you will have to accept the fact that learning will be a part of it, and for me, that is  the fun part.
Either way, enjoy. ;)

---

### Post by Ghuloomo on 2008-02-09
So what would be your choice now? I as a reader read 5 pages until now, and I'm not having any more words to you. It's all about experiencing things. I personally was using Windows since I was 10 years old, and now I'm 19. I know everything about Windows. People call me up everytime and they are like: "How i get this done?" I tell them: "Go to this, then here, then there, click on that, do this, finish" . Now I'm having enough with Microsoft, isn't it fair I give the same time to Linux too?
I've been using Ubuntu for like 2 weeks now, and I have learned amazing things about it. I'm loving it to maximum extent that now I prefer 2 weeks of experience over 9 years of slavery!
It's all about learning, in a period of two weeks, now I know how to work with the Terminal, how to install tar.bz2 files, Debian packages, knowing the deference between Gnome and KDE, installing and removing applications, customizing my Ubuntu so easily, etc.. Even if I get a problem, I just Google it and It's solved with the 1st or 2nd link.

Windows:
Use Antivirus
Use Spyware
Use Firewalls (not that necessary)
Be careful of malewares, trojans.
They beg you to buy one of their exe files. All those advertisements, install this, install that, and in the end something is wrong. Get the crack, do this do that.
And after 2 month ur windows gets extremely slow, either because of a virus, trojan, too many applications, services in the background, defragmentation, or spyware.. 
Everybody know this, that's why they have started to customize windows XP, coz they are not satisfied with it. They keep making:
Windows Crystal XP
Windows 2007 Professional
Windows Wesmosis
Windows bla bla
They hear about leaked SP3 and they kill themselves to get it, like BOOM their system will magically speed up, (WAKE UP! It's Microsoft!) finding it got slower!
And no matter what u put, formatting after two month is recommended! ;)

Ubuntu:
No spyware or virus, or any other kind of attacks
Stable
Fully customizable
No need to browse for programs, just go to add/remove -> search -> sort by popularity, and u get the idea of which program is better. You install it without any interruption, and it ALWAYS works!
Installing desktop environments, put GNOME, remove GNOME, put KDE, remove KDE, use no GUI.. Can you do those with XP?
Change the panel, add panels, one on the top, one right, one left, one at bottom, change their colors, make them transparent. Can you do those with your XP start menu?

Now meanwhile u might get some challenges of things not working, why not learning and make it something joyful? Every OS has its challenges..

I've installed Ubuntu for several friends, and after that, they straightly go to their exe files to open, or download a program, and it doesn't open. Then they say: "What's this? I can't open exe files!! :S"
How retarded is that? [B]Microsoft makes retarded computer users, not Linux!
[/B]

---

