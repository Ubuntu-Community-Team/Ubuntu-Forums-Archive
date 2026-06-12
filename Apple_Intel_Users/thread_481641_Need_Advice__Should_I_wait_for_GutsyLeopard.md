---
title: "Need Advice:  Should I wait for Gutsy/Leopard?"
date: 2007-06-22
forum: Apple Intel Users
---

### Post by neatokino on 2007-06-22
Hello all--

I've been running Feisty with VMWare Fusion on my macbook pro 2.16 Ghz core duo (the model before the core 2 duo);  I wanted to get a sense of linux, both to compare it with OSX and to learn how to use the operating system.  I'm still a linux newbie, to say the least, but I do have everything up and running well with Fusion, and I like ubuntu quite a bit.  I know that, sooner or later, I'll want to have a dual boot machine (only dual, no need for windows ever).

I'm trying to decide if it makes sense to wait for Gutsy and Leopard (newer, better?, built-in non-beta bootcamp?) before leaving vmware fusion behind and installing ubuntu to run independently of OSX.

My computer gets very hot when I run vmware fusion.  Will this also be a problem if I install Feisty now?  Will  temperature issues most likely be addressed with Gutsy?  I also would like to be able to suspend/sleep, and I would like full use of the touchpad, both of which I get with fusion.

I am chomping at the bit to install Feisty in a dual boot configuration with OSX Tiger, but I'd love some advice on whether it's worth waiting.  Oh, and are fixes to the various issues likely to come along in updates to Feisty over the next couple of months?

I can, by the way, get by with just OSX-- I think OSX is a great OS, and it meets my needs, but I love the ideas behind linux/open soure, and I'd like to gravitate there eventually.

TIA
Michael

---

### Post by HermanAB on 2007-06-22
It is very easy to re-install or upgrade Linux.  Go ahead and install the present version.  Enjoy!

Herman

---

### Post by incubus on 2007-06-22
I agree with Herman.  But if you're going to take the route of partitioning your hard drive, do back up your files.  That's the best advice I can give you.

With Ubuntu installed you can control the CPU throttling profile.  If you keep it down, it won't get hot.  Battery life is, unfortunately, not as good as in Mac OS itself -- probably because Apple does a lot of optimization that we don't have access to.  Suspending usually works out-of-the-box for newer Macbooks.  And the trackpad is a little more involved, but you can get it working.  If I may, I suggest that you don't try to solve all the problems in one day.  Make sure you get the basic stuff working, then work on the issues incrementally.  One of the cool things about Linux is that you learn a lot.

incubus

---

### Post by ronocdh on 2007-06-23
> **incubus said:**
> I agree with Herman.  But if you're going to take the route of partitioning your hard drive, do back up your files.  That's the best advice I can give you.

With Ubuntu installed you can control the CPU throttling profile.  If you keep it down, it won't get hot.  Battery life is, unfortunately, not as good as in Mac OS itself -- probably because Apple does a lot of optimization that we don't have access to.  Suspending usually works out-of-the-box for newer Macbooks.  And the trackpad is a little more involved, but you can get it working.  If I may, I suggest that you don't try to solve all the problems in one day.  Make sure you get the basic stuff working, then work on the issues incrementally.  One of the cool things about Linux is that you learn a lot.

incubus
Well said. Most important thing is to back up all data. Beyond that I say download Feisty and enjoy. Search this forum for information on PowerTop to increase your battery life and MadWiFi to get wireless up and running. Hopefully all your needs will be met. And besides, if you're thinking about waiting for 7.10 (Gutsy), why not just wait for 8.04, 8.10, etc.

---

### Post by thully on 2007-06-23
I will say that there is some improvements coming in Gutsy as far as MacBook support from my experience with the pre-release version.  For one thing, suspend on my MacBook (first generation) works out-of-the-box without severe kernel hacking (as was needed in Feisty).  I've heard the wireless support on some later MacBooks may work better as well.  Also, the system tends to run cooler thanks to the laptop tweaks in the newer kernel revisions.

If those things would make a difference, I may wait.  If not, go ahead and install.  Or if you are truly adventurous (like me), install the pre-release version (download the Tribe 1 alpha release ISO and enjoy).

---

### Post by ivesjd on 2007-06-23
You had to hack the kernel for suspend with fiesty? Was that the actual release version? Cause it works fine on my 1st gen.

---

### Post by tgalati4 on 2007-06-24
Dual finger scroll is something I use a lot in Tiger, but can't seem to get in Dapper Ubuntu (the last time I tested it.)  Edge scroll is fiddly and not consistent.

---

### Post by thully on 2007-06-24
ivesjd: yes, I had to hack the kernel for suspend in Feisty.  Evidently this effects many - but not all - first-generation MacBooks.  I have the base model (1.83GHz Combo drive) purchased about a month after release, and this is the case for me.  Gutsy suspend works beautifully, though.  (maybe the devs fixed this in a feisty kernel update...)

tgalati4: I have dual finger scroll in Gutsy pre-release - and it works.  It is more erratic than OS X, though.  Edge scroll is slightly more reliable, but annoying when compared to two-finger.  I've also got three-finger tap as right-click.  Overall, it works almost as well as OS X with tweaks.  I can post the xorg.conf if you want...

---

### Post by ivesjd on 2007-06-24
It might be something with the very first macbooks two. I got mine in september. So something might have changed. I was really lucky and suspend works great. /me knocks on wood :p

---

### Post by 3rdalbum on 2007-06-25
The reason why your computer is getting hot when running VmWare is not because of Ubuntu - it's because virtualisation of operating systems does tend to use quite a lot of CPU time. VmWare Fusion is especially hungry for processing power.

When you install Ubuntu it will use about as much CPU as Mac OS X, possibly less, so your computer won't get too hot.

---

### Post by entangled on 2007-06-25
Just a small point on power consumption. I have a power meter on my intel mac mini (1GB, core mono) and can see how many watts are going in real time. I use average of 58-60w (inc monitor) without vmware. When vmware runs there is a surge to 70w for a few seconds  (starting or restoring guest - windows 2003) and then it drops to 60w, as before. I have run several progs inside Windows and the power usage doesn't really change, other than for a few seconds. I don't see any real difference in power consumption when vmware is running a guest.
One thing though; OSX does not sleep when vmware is running, even when the guest is stopped or suspended.
I would like to get ubuntu to suspend my mac mini, but no luck yet. The latest kernel at least tells me it won't work, rather than trying and freezing the machine.

---

### Post by ronocdh on 2007-06-25
> **entangled said:**
>  would like to get ubuntu to suspend my mac mini, but no luck yet. The latest kernel at least tells me it won't work, rather than trying and freezing the machine.
Did you see [Azathoth's recent post]("http://ubuntuforums.org/showpost.php?p=2908906&postcount=5") about suspend?

---

