---
title: "Source Distros worth it these days?"
date: 2012-09-29
forum: Any Other OS
---

### Post by Rukiri on 2012-09-29
I'm not really new to linux as I've used it since windows 2000/me were being shipped with PCs. However I've always gone back and forth and with Steam and other goodies coming, but some do not plan to port to other distros or release the source just a release for a ubuntu.

So here's my question, are source distro's still relevant in today's world? I have a really high end machine, GTX geforce 680 + one of the newer quadros, 64GB of DDR3 1600MHZ worth of ram (can go up to 128GB), Sandy Bridge E Xeon 4GHZ X2.

I've spent roughly close to 5K on the machine but that does include 3X monitors, mechanical keyboard(corsair is awesome! bought the MMO version as it's backlit), mouse, and planning on a studio quality speaker system sometime next year.  I don't need 5.1 to be honest.. but I do have a 5.1 setup.

So to me I really saw no difference between Funtoo(what I'm currently using) and Arch Linux with my setup, but ask that question when someone has a run of the mill Dell or HP, you would see a difference as the packages could be compiled for your hardware.  Still can but the difference is so small is it worth it anymore?

Can't say I'm getting bored with the Gentoo echo system as I've used Gentoo as my main OS along side windows for 5 years and just recently dropped windows all together with my fresh install of Funtoo.

But I am getting bored with ebuild and portage issues that are constantly either breaking or a package has an issue..  Use and Cflags are useful but is there really a difference anymore?

Also I have noticed Wine lately seems to work better with Ubuntu lately than any other distro, reason being Photoshop.  I can get version cs6 running without issues in ubuntu but can't even with the same settings in Gentoo.  What's up with that?

---

### Post by slooksterpsv on 2012-09-29
Personally I think Source Distros are relevant to those that only want to install what they need. In a server operation this could work out for the benefit if you need specific compilation on the hardware you're using. Other than that for the general user there is no need. Personally I don't care to compile unless its an app thats not avail as a deb or that. Either way its your choice. Ubuntu does stable releases they don't always have the latest and greatest they stick with whats stable and push security updates. If you want a constantly changing distro try Debian or Linux Mint Debian Edition where you always get the latest and greatest and don't have to wait for a new release every 6-12 months.

---

### Post by Crafty Kisses on 2012-10-03
Yes, they are still worth it. Very relevant.

---

### Post by LiamOS on 2012-10-07
I'm not sure what sort of ebuild issues you're having, and all I can say is that I'm not having any... And there's always a text editor for any dodgy ebuilds. ;)

I think that now, more than ever, source distros are worth it. My main laptop can emerge -e world in only a few hours, and it's only an i3 with 3GB of RAM; compile times are not an issue anymore. You're also given a *ludicrous* level of customisation. USE flags on their own are pretty incredible, but the ability to specify CFLAGS, use the Intel compiler, use a gcc from the toolchain overlay, etc. just spoil me for choice. (I like my system half-broken)

As far as all that being noticeable goes, my Gentoo netbook(gcc-4.7.2, xmonad, generally minimal) boots thrice as fast than it did under Ubuntu, and runs much faster too(Firefox opening in ~2 secs as opposed to ~10). I've also found Python seems to run like a cheetah with -O3. On your machine, I'm not sure you'd notice anything for regular use, but if you're doing some high-performance computing, I think Gentoo would benefit you significantly over Ubuntu.

Ubuntu has the advantage that it just works almost all of the time. That said, when something goes wrong with Ubuntu, it's nightmarish to fix, whereas in Gentoo, revdep-rebuild/reemerging something will usually fix it, and you know what the system's up to, since you wrote half of the config files for it. I also do not use Wine or Virtualbox, but I've heard that they're a bit sketchy under Gentoo.


Also, using Gentoo makes you cool:
[http://www.youtube.com/watch?v=VjGSMUep6_4](http://www.youtube.com/watch?v=VjGSMUep6_4)

---

### Post by Rukiri on 2012-10-07
When something goes wrong with ubuntu it's more likely a known bug, with gentoo it may not be the case.   However keep in mind I was using FUNTOO not GENTOO.

Now I see Source distro's best used on the server market but that's just me being a sysadmin.  Binary is perfectly fine and the performance can be the same in some cases.  Just depends on the type of app or what your going for.

---

### Post by 1clue on 2012-10-07
The only source-based distro i have experience with is Gentoo.

If you have some software feature you want enabled, or one you want disabled, or if you have a strong desire to control which specific software is used on your computer, then I say source-based distros are relevant.  If you have freaky hardware then you may benefit from a source-based distro.

That said, I think for mainstream hardware there is almost no benefit for compiling with different options.  Find the optimal CFLAGS somebody else found for your hardware and leave it.  I think the issue is that Intel and other chip manufacturers are optimizing their faster chips to make best use of the 'basic' code that everyone is compiling for.

---

### Post by Rukiri on 2012-10-07
Yup, the new xeons are just as zippy in ubuntu as in gentoo optimized and even arch.
You may not see a performance difference but use flags are useful and for the most part can be done with installing from source on any distro anyway.

---

### Post by 1clue on 2012-10-08
If I could amplify a bit for people who haven't tried a source-based distro yet.

If you're just making a desktop box and want to play with whatever is in the repository, then you don't need a source-based distro.

I can see three general scenarios where source-based distros make sense:

1.  Special purpose server or appliance.
If you're making a single-purpose box such as a LAMP server or an advanced router, then source-based distros make sense because you can compile everything which is NOT needed for that scenario out of the system.  You can sort of do this on a normal distro like Ubuntu server by recompiling the kernel and not installing unnecessary software, but with a source-based distro you can compile all the unnecessary options out of every software package.  It's not as complicated as it sounds, Gentoo for example has what they call USE variables which are system-wide and can be tailored to a specific task.

2.  Experimental code.
If you're playing with experimental kernel code then you can recompile the kernel with that code turned on (again you can do this in Ubuntu) but once that's done you can also recompile everything in your system which pays attention to that code in a single step.  If you're the one writing that code then to me it seems that source-based distros are more completely set up to get you going easier.

3.  Odd hardware.
If you're running hardware that's not fully supported on anything, or if you're porting to a new hardware platform, then it's probably going to be easier on a source-based distro, if for no other reason than that source-based distros seem to collect the sort of person who's doing that, and there is a whole lot of very knowledgeable forum support for that sort of thing.

---

### Post by LiamOS on 2012-10-09
> **Rukiri said:**
> Yup, the new xeons are just as zippy in ubuntu as in gentoo optimized and even arch.

Do you have any figures for that?

---

### Post by 1clue on 2012-10-09
If you Google 'gentoo speed comparison' you find a slightly old gentoo-vs-ubuntu comparison.

That said I never really got much noticeable advantage for speed, and I have seen several people on the Gentoo forum post disappointing benchmarks.  Disappointing in that they didn't see much if any improvement on their personal project.

Frankly the only time I really care about speed is during compile.  That's optimizing make.conf (in Gentoo) and making good use of tmpfs in the portage temp space, and other places when I'm compiling my own stuff.

My personal take on it is that if you know what you're doing and have a situation which can benefit by speed optimization then you can probably make that happen if you research it enough.

I don't optimize for speed since my hardware is plenty fast enough for what I do.  My Gentoo goals are to have everything I want, and nothing I don't.  If I don't use a protocol or feature I completely remove all support for it from every app on the system, or as close as I can get to that goal.

It's more of a security and simplicity approach for me I guess.

---

### Post by LiamOS on 2012-10-09
I use Gentoo largely for the same reasons. I still do see a few noticeable performance increases, though, python, boot times, etc. among them.

The benchmarks I found seem to suggest that Gentoo does make a reasonable difference.

---

### Post by Rukiri on 2012-10-09
I do have to ask, mainly cause I got cs6 working in wine with funtoo(yes, I consider Funtoo an upgrade to Gentoo). Git > Rsync anyday.

Why does wine run better with ubuntu and source distros?

---

### Post by LiamOS on 2012-10-10
> **Rukiri said:**
> (yes, I consider Funtoo an upgrade to Gentoo). Git > Rsync anyday.

Agreed. Sadly, Funtoo is a bit too conservative for me. If I was running a server, I'd Funtoo the hell out of it.
> **Rukiri said:**
> Why does wine run better with ubuntu and source distros? 	

I honestly have no clue. It might be interesting to download wine binaries(See if Ubuntu ones will work, perhaps) to see how they work in comparison, or maybe even ask in #funtoo/#gentoo to see if anybody knows there.

---

### Post by Rukiri on 2012-10-10
I just had to ask mainly because if you wanna run Photoshop you'd better be in Gentoo or Ubuntu.

Some Ubuntu users have cs6 running flawlessly, wondering if they're using XP for their dlls?

---

### Post by xravexheavenx on 2012-10-10
Source distros are definitely worth the effort if you want a highly customized machine.  I am a Gentoo guy and have been for many years.  The amount of speed gained by installing only what you want with compatibility for only what you have is unparalleled.  I highly recommend playing with either Gentoo or Arch.

---

### Post by Rukiri on 2012-10-10
> **xravexheavenx said:**
> Source distros are definitely worth the effort if you want a highly customized machine.  I am a Gentoo guy and have been for many years.  The amount of speed gained by installing only what you want with compatibility for only what you have is unparalleled.  I highly recommend playing with either Gentoo or Arch.
I've been a gentoo guy since around 2004, prior to that I used slackware and debian.

---

### Post by x-shaney-x on 2012-10-11
I have used source distros (in fact my very first experience of linux was a very l-o-n-g gentoo install (stage something it was called at the time where you literally build it from scratch).
I learnt a lot from it back then and read a lot about optimizing.
When I eventually moved onto a "pre-made" distro (knoppix) I found there was barely any noticeable difference, performance-wise.

They are worth it if you actually want to learn about the inner-workings a bit more but I wouldn't say they are worth the effort if you are just after a performance boost.

---

