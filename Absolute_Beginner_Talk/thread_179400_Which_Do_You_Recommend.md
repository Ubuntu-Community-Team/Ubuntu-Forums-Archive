---
title: "Which Do You Recommend?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-19
Concerning upgrading to Dapper from Breezy on June 1st: i don't really like doing fresh installs, (backing up, reinstalling software and configurations) but i heard upgrading is tricky and can be disastrous.

---

### Post by aysiu on 2006-05-19
From what I've seen, the weird update -d command that's out there has caused problems for people.

People seem to have better luck doing it "the old-fashioned way." I certainly did: [http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by xXx 0wn3d xXx on 2006-05-19
I would do a clean install. I have seen tons of posts on "dist-upgrade gone wrong." There are still alot of problems with dist-upgrading so just save yourself some time. Backup your home folder and do a clean install

---

### Post by user1397 on 2006-05-19
[quote=aysiu]From what I've seen, the weird update -d command that's out there has caused problems for people.

People seem to have better luck doing it "the old-fashioned way." I certainly did: [http://www.psychocats.net/ubuntu/dapper]("http://www.psychocats.net/ubuntu/dapper")[/quote]
is the psychocats way fool-proof??
i would never have done the update manger -d command anyway, i was actually thinking of the psychocats one

---

### Post by Sef on 2006-05-19
**Back up** your data first before attempting an upgrade to Dapper.  Both a clean install and dist-upgrading carry a risk of a crash where you will lose your data.

A clean install is a safer way to go; however, you will have to reset your setting, codecs, etc.

An dist-upgrade will allow you to keep your codecs, settings, etc.; however, it runs a higher risk of failure than a clean install.

Best way to do a dist-upgrade is 

sudo apt-get update

sudo apt-get dist-upgrade

Once Dapper is stable, you will be offered a chance to click on a button to upgrade.  As long as you have your data backed up, I would do it that way.  At best all will go well ( and it is the most likely outcome.)  At worst, you will have to do a clean install.

---

### Post by user1397 on 2006-05-19
> **Sef]**Back up** your data first before attempting an upgrade to Dapper.  Both a clean install and dist-upgrading carry a risk of a crash where you will lose your data.

A clean install is a safer way to go said:**
> 
 i guess ill probably do the one button thing then, but ill make sure i have a working 6.06 install cd handy just in case
BTW, 
[quote=Sef] sudo apt-get update

sudo apt-get dist-upgrade
to do that you would first need to change your sources.list
simply doing dist-upgrade doesn't upgrade you to dapper

---

### Post by aysiu on 2006-05-19
[QUOTE=erik1397]is the psychocats way fool-proof??
i would never have done the update manger -d command anyway, i was actually thinking of the psychocats one[/QUOTE] No method is foolproof. A lot of it depends on how many non-standard applications you have installed and in what way and how you have things set up.

The Psychocats method does a few things to try to make things run a bit more smoothly.

First of all, it makes sure that you have the proper *-desktop* package(s) installed, as those are what's needed so you can get the "proper" default Dapper installation + extra packages instead of just upgraded versions of whatever packages you have installed.

For example, my guess is that if you don't have *ubuntu-desktop* installed, you won't get *gdebi* installed, as that wasn't part of your Breezy installation. Now, not having *gdebi* won't make your system unstable, but if there's some library you need... well, that could be trouble.

The second thing it does is log you out of your X (graphical) session so that you won't run into weird conflicts while you're updating packages and using them at the same time. Ordinarily (during regular upgrades, as opposed to dist-upgrades), updating programs while you're using them isn't an issue, but for an undertaking this large, it doesn't hurt to be on the safe side.

Finally, it kills the X server and resets it before you start using Dapper Drake. Another thing that will help to make sure there are no problems.

No guarantees, though, of course.

---

### Post by user1397 on 2006-05-19
what would you guys recommend if i have automatix installed and lots of things installed from it? fresh install? (i actually don't mind reinstalling programs, cause  i don't really have that many non-standard ones. what would be a pain from me is backing up - i hate dvd+r's!!!!!!!!)

---

### Post by Most_Wanted on 2006-05-19
Upgrading.:D

---

### Post by meng on 2006-05-19
I remember things went awry when I did the hoary to breezy dist-upgrade and I had to reinstall. Fortunately the reinstall was painless. Furthermore, by that point I had my /home on a separate partition, which was possibly the best piece of linux advice I have ever received. The failed dist-upgrade may have had something to do with the huge number of broken packages I had. Since then, I have been careful to avoid this. Nevertheless, I'll probably sit back and read about others' experiences with upgrading before I take the plunge myself.

---

### Post by aysiu on 2006-05-19
Having a separate /home partition (or at least a separate data partition) saves you a lot of upgrading/reinstalling stress.

If you don't already have one now, create one.

---

### Post by Sef on 2006-05-19
> to do that you would first need to change your sources.list
simply doing dist-upgrade doesn't upgrade you to dapper

No.  It will be done automatically.

---

### Post by aysiu on 2006-05-19
[QUOTE=Sef]No.  It will be done automatically.[/QUOTE] On the release date, you mean...?

Ordinarily if you're sources are Breezy one and you do ```
sudo apt-get dist-upgrade
``` it does not update you to Dapper.

---

### Post by user1397 on 2006-05-19
[quote=aysiu]On the release date, you mean...?

Ordinarily if you're sources are Breezy one and you do ```
sudo apt-get dist-upgrade
``` it does not update you to Dapper.[/quote] yes aysiu you were the first one to actually teach me this  little fact, and i do 
```
sudo apt-get dist-upgrade
``` all the time

---

### Post by user1397 on 2006-05-19
[quote=aysiu]Having a separate /home partition (or at least a separate data partition) saves you a lot of upgrading/reinstalling stress.

If you don't already have one now, create one.[/quote] so what would you recommend when creating new partitions if i do a fresh dapper install? maybe:
primary                          /                                         ext3
logical                             /home                        ext3
swap

i actually don't know the difference between logical and primary, please teach me!!!
btw, my breezy partitions are just:
primary / ext3
swap

---

### Post by aysiu on 2006-05-19
[QUOTE=erik1397]so what would you recommend when creating new partitions:
primary                          /                                         ext3
logical                             /home                        ext3
swap space                                                       swap

i actually don't know the difference between logical and primary, please teach me!!![/QUOTE] I'm a little if-fy myself on the difference between logical and primary. I don't even worry about that. I let the partitioning programs (GParted, QTParted, DiskDrake) worry about that stuff for me.

For different partitioning schemes, take a look here: [http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by angkor on 2006-05-19
I'd definately recommend an upgrade.

Download the install .iso and burn it on a disc, do a dist-upgrade and see how it goes. If there are problems try to fix them and if you can't fix it....Fresh install.

---

### Post by aysiu on 2006-05-19
I'm kind of surprised this many people are recommending a clean reinstall when erik1397 already expressed displeasure with it.

I say do a dist-upgrade. If it works, great. If it doesn't, you'll end up doing a clean reinstal anyway if you don't have the patience for repair...

---

### Post by user1397 on 2006-05-19
[quote=aysiu]I'm a little if-fy myself on the difference between logical and primary. I don't even worry about that. I let the partitioning programs (GParted, QTParted, DiskDrake) worry about that stuff for me.

For different partitioning schemes, take a look here: [http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")[/quote] 1)i like the ubuntu partitioner as im not familiar with those other programs
2)very good psychocats guide btw
3)i'm just sort of confused: if i have a 160 GB hard drive, how much would i make the / partition and the /home partitions???

---

### Post by angkor on 2006-05-19
[QUOTE=aysiu]I'm kind of surprised this many people are recommending a clean reinstall when erik1397 already expressed displeasure with it.

I say do a dist-upgrade. If it works, great. If it doesn't, you'll end up doing a clean reinstal anyway if you don't have the patience for repair...[/QUOTE]

Me too. It's a no risk operation (if you back-up or keep your /home on a separate partition). If the upgrade doesn't go too well, you can reinstall anyway.

---

### Post by user1397 on 2006-05-19
[quote=aysiu]I say do a dist-upgrade. If it works, great. If it doesn't, you'll end up doing a clean reinstal anyway if you don't have the patience for repair...[/quote]
this scheme is definitely the one that ill follow, as it makes the most sense.
just one question on partitioning:
would i make my / partition primary and my /home partition logical? or both primary? (this scenario would occur if my dist-upgrade did not work and i did a fresh install of dapper, using the ubuntu partitioner)

---

### Post by aysiu on 2006-05-19
[QUOTE=erik1397]1)i like the ubuntu partitioner as im not familiar with those other programs[/quote] All partitioning programs are pretty much the same in terms of interface. > 3)i'm just sort of confused: if i have a 160 GB hard drive, how much would i make the / partition and the /home partitions??? If I were you (I actually sort of am... I have a 160 GB hard drive as well), I'd partition it like this:

/ (15 GB)
/home (144 GB)
swap (1 GB)

> would i make my / partition primary and my /home partition logical? or both primary? (this scenario would occur if my dist-upgrade did not work and i did a fresh install of dapper, using the ubuntu partitioner) I don't know what the difference is, and it's never affected my Ubuntu installation adversely. Any partition Ubuntu lets you install to or mount you can use.

---

### Post by user1397 on 2006-05-19
[quote=aysiu]If I were you (I actually sort of am... I have a 160 GB hard drive as well), I'd partition it like this:

/ (15 GB)
/home (144 GB)
swap (1 GB)
[/quote]
can this configuration mess up my drive cause you know how 160GB hdd's are never actually 160GB, more like 155 or something...

---

### Post by aysiu on 2006-05-19
[QUOTE=erik1397]can this configuration mess up my drive cause you know how 160GB hdd's are never actually 160GB, more like 155 or something...[/QUOTE] A partitioning tool will never let you allocate for a partition non-existent space.

If you have only 155 GB, it won't let you create partitions that add up to 160 GB. It divides up what's there.

---

### Post by confused57 on 2006-05-19
When I finally decide to upgrade, I think I'll try dist-upgrade; but have a final version Dapper CD handy.  How do you do a dist-upgrade of Breezy, using the Dapper CD?   Breezy is working so well, I'm definitely not in a great hurry to upgrade; least it's supported for another year...
I'll probably follow the psychocats method, unless I feel comfortable doing it with the Dapper CD.

How easy is it to create a separate /home partition with your current /root + /home on the same partition?

I realize nothing's foolproof, no moneyback guarantees...

---

### Post by mlind on 2006-05-19
I'd just backup my /home prefs and start from clean table.
Safer, less odd "misconfiguration" side-effects.

---

### Post by user1397 on 2006-05-19
[quote=aysiu]A partitioning tool will never let you allocate for a partition non-existent space.

If you have only 155 GB, it won't let you create partitions that add up to 160 GB. It divides up what's there.[/quote]
alright, thanks so much aysiu for helping me the zillionth time :D

---

### Post by matthew on 2006-05-20
I've had excellent success doing dist-upgrades, both in Ubuntu (i.e. Hoary->Breezy) as well as with Debian (Sarge->Etch->Sid). Occasionally there are little niggles, mostly due to detailed hardware specific customizations. If you have really standard hardware that didn't need a lot of fiddling with to get it working originally I can't see any real reason that the dist-upgrade method shouldn't work for you. If, like me, you have a laptop...especially one with wireless internet and an ATI card, the upgrade might be a little more difficult. I would still try it first (after backing everything up...have we said this enough yet?) and if you have problems you can't handle then do the fresh install. This way you can at least attempt to keep all your customizations, etc.

---

### Post by it.henrik on 2006-05-20
upgrading in linux is a bit like upgrading in windows 

you will get stuck with lots of files on your harddrive that you either
a. leave there and lose hd space for ever.
or
b. find out how to know which files you dont need anymore.

Im the a. guy :) so as soon the finla 6.06 comes out im backing up my /home and reinstalling my ubuntu :)

---

### Post by angkor on 2006-05-20
[QUOTE=it.henrik]upgrading in linux is a bit like upgrading in windows 

you will get stuck with lots of files on your harddrive that you either
a. leave there and lose hd space for ever.[/quote]

What kind of files do you mean? It's not that HD space is very expensive nowadays anyway, and we're not talking about gigabytes here only mb's.

> 
b. find out how to know which files you dont need anymore.


Look into *deborphan,* if you'r worried about unused packages lingering on your machine after an upgrade.

---

### Post by henriquemaia on 2006-05-20
I go for the dist-upgrade. I have good experiences with this method, good enough to make me confident to use it.

With everything important properly backup up, this is piece of cake. Nothing to loose.

ps: except time.

---

### Post by skippy81 on 2006-05-20
I think a good comprimise is a seperate home partition.  That way you can safely reinstall over the root filesystem, but keep your settings safe.  If you don't have a seperate home directory, then just copy all the stuff out of your home and copy the stuff you want to keep back again once you have done a fresh install.  I'm a big fan of the linux home directory concept - for some reason it actually works unlike the stupid MS My~Documents.

I personally think it is better to do a clean install from a CD for one reason, its usually quicker.  Unless there are more than 100mb of security updates needed, the CD option will get you up and running faster and more reliably.  

Then again I installed dapper flight 3 yesterday and ran the update program.  400 mb of packages were downloaded, it would have been quicker for me to just download a more upto date CD ](*,)

---

### Post by steve.horsley on 2006-05-20
My vote is for a clean install. If you upgrade, that will keep any number of configuration settings that a fresh install might have done better and used new features and options that simply didn't exist and therefore weren't configured in the previous installation. Like perhaps using native wifi drivers instead of ndiswrapper, better sound settings etc. If you upgrade, you will never be sure it's running at its best.

Also, of two machines that I fresh installed Dapper flight 4 on, both have developed quirks during upgrades since, so upgrading isn't error free. 

On one the red "automatic updates are available" thingy can't actually install them any more although Update Manager from the manu can, so I have to launch Update Manager manually every time I see the red indicator.

On the other, the main menu ubuntu logo has myteriously turned into a footprint. Not major, but what else is going bad that I can't see?

So I actually intend to do a fresh install of both when the real thing is released, just to get rid of all the quirks.

---

### Post by angkor on 2006-05-20
[QUOTE=steve.horsley]
Also, of two machines that I fresh installed Dapper flight 4 on, both have developed quirks during upgrades since, so upgrading isn't error free. 
[/QUOTE]

But we're talking about dist-upgrading from a stable release to the next stable release. Not upgrading a development release.

I've had great success dist-upgrading Ubuntu and Debian. In Debian it used to be more tricky and sometimes it downright failed. But that was about 2 years ago and I wouldn't know how it is nowadays.

I'm running Dapper now (error free) on what used to be a Hoary system. My /home is even older and used to be Debian Sid. :)

---

### Post by user1397 on 2006-05-22
alright thanks guys with all of the helpful replies.
and yea...i dont know how to close the poll -lol

---

### Post by Clay85 on 2006-05-22
Don't close it I didn't tell you my opinion yet!

I just upgraded from Breezy to Dapper today and the only thing that freaked me out a bit was the synaptic package manager gave me an error, which I fixed in the terminal using the command it told me to.

Also does Dapper not support OpenOffice? Because they have all been uninstalled. :(

---

### Post by user1397 on 2006-05-22
can you find it in synaptic? it would make NO SENSE if Oo.org was not installed with dapper!

---

### Post by Clay85 on 2006-05-22
Haha! I didn't think if re-installing it. Doing that right now. (I'm not stupid. I promise!)...

---

### Post by user1397 on 2006-05-22
[quote=Clay85] (I'm not stupid. I promise!)...[/quote]
lol

---

### Post by az on 2006-05-22
Of course dist-upgrading to Dapper has been touchy - it's in development.

Once released, many of the dist-upgrading issues will be ironed out.  Debian/Ubuntu is *meant* to be dist-upgradable from one stable release to another.

---

### Post by infoseeker on 2006-05-28
Just my 2c :)

My Breezy installation gave me no problems at all before upgrading to Dapper.

I have been doing the regular updates (and the have been many :)) and I must say that my system has worked well 99.9% of the time.
I am going to do a clean install when the final release appears.  The reason for this is that X crashes every now and then on bootup, and also sometimes my mouse does not work on bootup.  Doing the necessary
> sudo dpkg-reconfigure xserver-xorg-core
and/or
> sudo nvidia-xconfig
ALWAYS sorts out these problems.

So, basically, I would like to do a clean install and see if the problems above are software related, or hardware.

PS.  I have a Nvidia FX5200
> 0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


---

### Post by Klaidas on 2006-05-28
i myself will do a clean install.
Upgrading will require me to download a lot of megs, right?
So what if I will need to reinstall ubuntu, or give ubuntu to a friend of mine?
Download the iso again? :) Nah ;)

---

### Post by Gustav on 2006-05-28
I'll do it the "click a button"-way.

I've had the same /home/ since I had Mandrake 9.0 (throu Mandrake 9.2, Mandrake 10, Debian (testing), Warty, Hoary and now Breezy). 

And I've dist-upgraded my way from Warty :)

---

