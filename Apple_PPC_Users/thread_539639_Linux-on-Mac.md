---
title: "Linux-on-Mac"
date: 2007-08-31
forum: Apple PPC Users
---

### Post by senuxis on 2007-08-31
I am talking about an implementation that is similar to Mac-on-Linux; a separate and native installation of Gnu/Linux being executed from a window within Mac OS X PPC. What I want to know are:

1) How easy would it be to implement?
2) Is an effort to achieve this existent?

---

### Post by stmiller on 2007-08-31
For x86 emulators inside OS X PPC check out, Windows Virtual PC 7, or Qemu ( [http://www.kju-app.org/kju/](http://www.kju-app.org/kju/) )

Any software doing this will be slow due to the very nature of what the emulator is doing. (Translating x86 code to PowerPC)

---

### Post by very_japi on 2007-08-31
I don't know why anyone using mac would want to try a different OS. I mean, Mac has somehitng no other OS has. Your Software is optimized for your hardware.... not only compatible... optimized. That's something you never get on Unix, Microsoft, ... and definetely not in linux, where hardware compatibility (specially with Mac users) is something people complain about on a daily basis.

---

### Post by jacob01 on 2007-08-31
yea but somtimes that hard ware optomization messes up and locks up the computer

---

### Post by stmiller on 2007-08-31
> **very_japi said:**
> I don't know why anyone using mac would want to try a different OS. I mean, Mac has somehitng no other OS has. Your Software is optimized for your hardware.... not only compatible... optimized. That's something you never get on Unix, Microsoft, ... and definetely not in linux, where hardware compatibility (specially with Mac users) is something people complain about on a daily basis.

Linux on PowerPC is extremely optimized, and hardware support for PowerPC is excellent in Linux, especially for ATI based iBook/Powerbooks, and all G3-G5 Powermacs. You can watch youtube videos of iBooks demonstrating Beryl/Compiz under Ubuntu, etc. 

There are many choices of operating systems, and people use what they like. :KS You would probably get a different answer from every person you ask this question to on this forum.

---

### Post by Lord Illidan on 2007-08-31
> **very_japi said:**
> I don't know why anyone using mac would want to try a different OS. I mean, Mac has somehitng no other OS has. Your Software is optimized for your hardware.... not only compatible... optimized. That's something you never get on Unix, Microsoft, ... and definetely not in linux, where hardware compatibility (specially with Mac users) is something people complain about on a daily basis.

Sure, Mac has only Mac hardware..Linux has to deal with PC and Mac hardware at the same time..wonder why it is so difficult to do so.

---

### Post by Auria on 2007-09-01
very_japi : this is a linux forum... if you don't see why people would want to use linux what are you doing on this board in the first place?

stmiller : i don't think the OP was asking for an emulator, just for a way to boot linux in a frame instead of rebooting... (OP : is that right?)

OP : mac-on-mac (the mac port of mac-on-linux) was supposed to get there eventually. not sure about its status. i *think* it was merged with mac-on-linux but don't quote me... if you are on intel you can also look at parallels desktop

---

### Post by EuroCity on 2007-09-01
Here, BTW, is the the mac-on-linux FAQ:

[http://mac-on-linux.sourceforge.net/wiki/index.php/FAQ](http://mac-on-linux.sourceforge.net/wiki/index.php/FAQ)

... where they say that a MOM port will be available in the future.

Talking about Virtual PC 7 (recently updated to version 7.0.3, but it's only a security patch), it's not that bad: good enough for testing purposes, even if of course it is slow. For example, personally I have Ubuntu Feisty PPC on a real partition (together with Fedora and OpenSUSE, and of course Mac OS X), while I use VPC for Gutsy x86 and other unstable distros (and Windows).

Qemu and Q, OTOH, are so slow that they are practically unusable on a PowerPC Mac, at least for emulating a "heavy" Linux distribution.

MOM (mac-on-mac, and thus also linux-on-mac) would be great, indeed! :) 8)

---

### Post by jso2897 on 2007-09-03
> **very_japi said:**
> I don't know why anyone using mac would want to try a different OS. I mean, Mac has somehitng no other OS has. Your Software is optimized for your hardware.... not only compatible... optimized. That's something you never get on Unix, Microsoft, ... and definetely not in linux, where hardware compatibility (specially with Mac users) is something people complain about on a daily basis.
 I'll give you an example. it's important to remember that Mac software is NOT Apple's product. Their product is hardware, and their software is calculated to quickly go obsolete and make you buy new hardware. A guy gave me an old Tangerine case IMAC the other day, and it had OS8.5 on it. Even if I had wanted to buy a bunch of software, it's very iffy to try to upgrade those machines to OSX. I've never tried, but many have told me it can't be done, and the few that claim it can have described a process that makes the Spanish Inquisition pale by comparison.
Well, with OS 8.5 on it, this machine was, for all intents and purposes, worthless. It wouldn't do anything, and what it did was slower than mud.
 SoI loaded Xubuntu onto it. It now surfs the net with Firefox 2.0, runs Openoffice, plays Diablo 2, and, in short, does about a thousand more things about 500% better.  It has gone from being a brightly colored doorstop to being a real, usable computer.
OS is just another locked-down, proprietary operating system designed to take your money and protect the makers intellectual property, and I have always failed to see how it sucks any less than Windows.

---

### Post by Afishionado on 2007-09-03
> **jso2897 said:**
> 
OS is just another locked-down, proprietary operating system designed to take your money and protect the makers intellectual property, and I have always failed to see how it sucks any less than Windows.

It has fewer viruses? :)

You really have Diablo II running on Linux/PPC? I'm very curious how that works.

---

### Post by bam1234567 on 2007-09-03
Ive had few expirences with it, but sometimes it takes a lot of work to use it. So i think even if you like Linux, Mac OS is faster on it (obviously) and it takes less time to get it up and running.

---

### Post by jso2897 on 2007-09-04
> **Afishionado said:**
> It has fewer viruses? :)

You really have Diablo II running on Linux/PPC? I'm very curious how that works.

 In emulation with QEMU. And no, it does not run fast, but it's playable. My point was that older macs that are no longer functional with the version of OS they can run can run well and have a second life with Ubuntu. All OS is to me is another commercial OS that is inferior to Linux - just like Windows. Perhaps it is a little less inferior. Cow dung probably tastes better than pig dung, too. I prefer not to dine on either.
This is a forum for Ubuntu users who have mac hardware. It doesn't seem like an appropriate place to argue the merits of OS. If we wanted to use OS, we wouldn't be in this forum.
And now, I'm through troll-feeding.
Goodbye.

---

