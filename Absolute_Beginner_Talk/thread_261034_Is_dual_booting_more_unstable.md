---
title: "Is dual booting more unstable?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Tux Aubrey on 2006-09-19
Hi all. My second post here after 2 months of dual booting XP and Ubuntu.  

I love Ubuntu but it has been far from easy for me to setup and maintain all the functions I need (wireless SAMBA networking, shared printing etc.) on one desktop and two laptops.

While most issues have been solved with much (incompetant nooby style) tweaking, I still have problems with unstable sessions, especially on my main desktop PC that serves as a family computer. It is rebooted several times a day so that family members can do whatever it is they "need" Windows for (teenage addiction to Ultima Online mainly).  This SEEMS to result in the next session of Ubuntu either not booting properly or being particularly unstable - apps closing or locking suddenly or being logged out of the desktop.

My "expert" son (the one addicted to UO) informs me this is because I am dual booting from a single hdd and that other "experts" he knows (presumably other teenage boys) insist that Windows and Ubuntu should be installed on separate HDDs because dual booting off a single is inherently unstable.

Any views?

Aubrey snr

---

### Post by DiJEH on 2006-09-19
I'm no expert on this but I've heard of so many people who dual boot with no issues what so ever. If you're the type of person who even knows what Ubuntu is then you probably know more than most kids. I'd ignore the kid personally, he seems to just be wanting to complain... alternatively you could just nuke Windows and go "get a job and you can play UO when you like", you get extra PC time that way too ;)

---

### Post by xpod on 2006-09-19
Anything in life that is added to becomes more complicated.
Twice OS`s equals twice the potential for disaster.

Thats not to say that if you dont be careful and try do stuff beyond your means that it cant all run perfectly because it can..

I got 4 os`s on 3 pc`s so try calculate THAT..lol.OH and then i have to multiply THAT by 4 girls and 1 boy....I need einstein!!!

The more you add the more you compliate ANYTHING

EDIT:..THIS install of xp\ubu runs like a dream........for now!!.

---

### Post by MWAAAHAAA on 2006-09-19
> I still have problems with unstable sessions

What exactly do you mean by 'unstable'?

> It is rebooted several times a day so that family members can do whatever it is they "need" Windows for.

> apps closing or locking suddenly or being logged out of the desktop

This really sounds strange, especially being logged out of the desktop. You might want to check your RAM. If you install memtest86+ Ubuntu should create an appropriate GRUB boot option for you automatically, just press ESC when GRUB starts loading and select the test. This can take a while though.
 
> because dual booting off a single is inherently unstable.

In my *humble* opinion this is horse manure. If you boot into Ubuntu, all your windows stuff is considered just some more data lying around on your hard disk, while Ubuntu should hapilly go about its business.

On a general note I have to admit that I only dual booted win98 from the same hard disk. I decided to put XP on its own HD, which I can only recommend BTW.

What exactly is your setup?

---

### Post by Mime on 2006-09-19
I've had XP and Ubuntu dual booted on my laptop for quite a while now and I've never had any trouble caused by it.  I don't think that's the cause of your problems.

A good course of action might be to rule out any hardware problems(like testing your ram as mentioned previously),then if everything checks out there you can be pretty sure that the source of trouble is something specific to one particular OS.

---

### Post by Tux Aubrey on 2006-09-19
Thanks for the quick replies.

1. Yes, my preferred option is to get rid of Windows (and the child) completely.  Note for parents: Never get broadband if you want your children to leave home.  He told me the other day that he had accumulated over $2 million in gold on UO. I told him to buy an appartment a Sydney and move out.

2. My desktop system is a P4 about two years old.  1 Gb of RAM and 80Gb and 60Gb hard disks.  I have a Dlink wireless router connected to broadband. I'm running Dapper on the -686 kernel.

3. The flakiness is multifaceted - often the boot hangs checking filesystems or configuring network devices (its fairly random and I have a large collection of error messages).  If I can boot to the desktop, apps like firefox will open but close within a few seconds.  

4. Sounds bad, but is really just an annoyance because a reboot (or two) will always result in a stable session (until the next exciting session of UO).

5. I am considering a re-install of Ubuntu onto the second HDD to see whether I can get things perfect.  Just wondering whether others had experienced this issue - the computer stuff,not the stay at home teenager. (I have often wondered why they don't run away to join the circus anymore.  They are such clowns anyway.)

Aubrey snr

---

### Post by bodhi.zazen on 2006-09-19
[color=red]Windows, by design, is unstable. Dual booting to windows is therefore unstable.[/color]

It should not affect your ubuntu partition unless you've been trying to access Ubuntu via windows.....

---

### Post by nickpaton on 2006-09-19
you need to eliminate hardware problems.

As well as using Memtest 86 to check your memory is OK (instability can often  be traced to a faulty chip), try passmark which more thoroughly tests the other PC components:

[http://www.passmark.com/products/bitlinux.htm]("http://www.passmark.com/products/bitlinux.htm")

---

### Post by xpod on 2006-09-19
So how do I eliminate MY problems nick??
Keeping in mind that my hardware is all fine....
Bar the dodgy graphics card of course but kassi`s sorting that for me!
:confused: :rolleyes: :p

---

### Post by Tux Aubrey on 2006-09-19
I shall do as you suggest and investigate my hardware a little more thoroughly.  I did upgrade my RAM soon after installing Ubuntu and that may be the source of this frustration.

Thanks

---

### Post by xpod on 2006-09-19
> Never get broadband if you want your children to leave home. He told me the other day that he had accumulated over $2 million in gold on UO. I told him to buy an appartment a Sydney and move out.

My tennager aint interested in pc`s(thankfully)
And the rest can have the broadband all day if they want while im at work..
Shame their at shool:twisted: ..

I`ll buy them a router when their more interested.....mabey:D

---

### Post by Frak on 2006-09-19
> **Tux Aubrey said:**
> Hi all. My second post here after 2 months of dual booting XP and Ubuntu.  

I love Ubuntu but it has been far from easy for me to setup and maintain all the functions I need (wireless SAMBA networking, shared printing etc.) on one desktop and two laptops.

While most issues have been solved with much (incompetant nooby style) tweaking, I still have problems with unstable sessions, especially on my main desktop PC that serves as a family computer. It is rebooted several times a day so that family members can do whatever it is they "need" Windows for (teenage addiction to Ultima Online mainly).  This SEEMS to result in the next session of Ubuntu either not booting properly or being particularly unstable - apps closing or locking suddenly or being logged out of the desktop.

My "expert" son (the one addicted to UO) informs me this is because I am dual booting from a single hdd and that other "experts" he knows (presumably other teenage boys) insist that Windows and Ubuntu should be installed on separate HDDs because dual booting off a single is inherently unstable.

Any views?

Aubrey snr
Actually booting from the **SAME**HDD is safer because it doesnt have to power up extra drives; its all centralised
I tried that once with my parents not to long ago to get more space when I was 14 I'm 15 now, been using ubuntu for as long as I can remember, I think it was october 2004.
I dual boot from XP to Vista to K/X/Ubuntu all the time w/no issues.

---

### Post by Sonic Alpha on 2006-09-19
> **Tux Aubrey said:**
> My "expert" son (the one addicted to UO) informs me this is because I am dual booting from a single hdd and that other "experts" he knows (presumably other teenage boys) insist that Windows and Ubuntu should be installed on separate HDDs because dual booting off a single is inherently unstable.

I dual boot without any issues.  Both Windows XP and Ubuntu are on the same hdd (with their own decently sized partitions).  The only problems I've seen with people trying to dual boot, is when they install XP onto a Ubuntu system (as opposed to Ubuntu on an XP system), as it messes up the GRUB loader (which isn't too hard to fix).

To be perfectly honest, your "expert" needs to read up a little on the finer points of running a dual boot system.

---

### Post by mongooseman1128 on 2006-09-19
you also might want to run a HDD test, there's a chance that coincidentally (or because of the repartitoning) you got some bad sectors on the XP partition. The tool I use at work primarily is DFT (drive fitness test) by Hitachi, it's easy to find on google so just download and burn it to a bootable disc  then boot to it and run advanced test.

---

### Post by Tux Aubrey on 2006-09-20
I ran Memtest and it shamed me!  Thousands of errors on the first pass.  I have replaced the 1 Gb chip with my old 512 Mb one, ran Memtest and it was clean(again, just one pass) and my machine booted smooth as silk.

I suspect I made a stupid error with the type of RAM I purchased (hey, it was a bargain).

I will run the HDD tests as well to be sure, but it certainly looks like neither Windows nor Ubuntu were responsible for this one.  I will log it as pilot error.

Many thanks for all your help.

Happier and happier with Ubuntu all the time!

Aubrey

---

### Post by nickpaton on 2006-09-20
Excellent news and thanks for the feedback!

---

### Post by nickpaton on 2006-09-20
> **xpod said:**
> So how do I eliminate MY problems nick??
Keeping in mind that my hardware is all fine....
Bar the dodgy graphics card of course but kassi`s sorting that for me!
:confused: :rolleyes: :p

A sledgehammer??;) 

I thought you'de (sorry I mean Kassie had!) got everything going.  Where are you at with that PC?

---

### Post by Frak on 2006-09-21
And to all a happy ending,
I think we can put this Thread to rest.

---

### Post by az on 2006-09-21
> **Tux Aubrey said:**
>  insist that Windows and Ubuntu should be installed on separate HDDs because dual booting off a single is inherently unstable.


For the record, that is untrue.  Completely false.

---

### Post by bobpur on 2006-09-21
If your hardware and software checks out, grab the kid and work his fingers over with a ballpeen hammer and see if that helps:)
I have three daughters and a wife that are most of my computer problems.
BTW, I dual boot off two hard drives.

---

### Post by Tux Aubrey on 2006-09-21
Thanks all.  

BTW

I tried this a few years ago:

```
sudo apt-get remove teenage.son
```

but nothing happened and things just got more and more unstable.  So I then tried

```
sudo mv /mainhouse/teenage.son /garageappartment/
```

And things did settle down for a while.  Broadband problems have created further instability, so am trying:

```
sudo mv -f /garageappartment/teenage.son /out/
```

but there is no response.  

Perhaps another parent could check my code and advise.  If there is a way to turn off verbose when I run the command, I'd like to know.  Perhaps I should just disable his sound card?  There does appear to be a dependency problem and I think the mother daemon is interferring with the commands.

Aubrey

---

### Post by madcow72 on 2006-09-21
If I can make a suggestion:  I'm somewhat of a newbie at Linux, but I've managed to solve my dual boot problems by installing Windows XP as a virtual machine inside Kubuntu.  My machine is a P4 2.4GHz w/ 1.5GB RAM and has no problem running both operating systems simultaneously.  What's even cooler, is that when running dual monitors I can keep Windows on one side and Linux on the other, while the mouse is able to move happily in between both.  If you're interested, I think this is a good HowTo:  [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

Note that VMWare has now made their Server Software free so you can create your own windows virtual machine.  You'll get the stability of Linux without the insecurities of Windows, and best of all, no more rebooting!  (I should say though, every time that I do reboot, I have to re-configure VMWare using: ```
sudo vmware-config.pl
```  Haven't figured out how to get around that yet.

---

### Post by Tux Aubrey on 2006-09-21
Thanks for the VMWare suggestion.  I have been pondering whether or not to go that way to accommodate residual (recidivist) windows users.  Now that I have ditched my problem RAM, I will upgrade properly and give VMWare a try.  Sounds like fun.

Aubrey

---

