---
title: "Installing Ubuntu 7.10 Gutsy on a broken iBook g3: let's make it work"
date: 2008-04-07
forum: Apple PPC Users
---

### Post by lordfly on 2008-04-07
Hi all,

Let's start off with me. I'm a newbie Linux user. I installed 7.10 on my old Toshiba laptop a few months ago, very nice. Took some fiddling, but it's a nice OS. I don't know the first thing about linux, any command-line commands, any of that, but I did grow up on DOS machines, so I know my way around a command line if I know the commands and/or what they do. I'm a Windows guy, so my knowledge of Apple PCs is specious at best, and limited to a properly running Tiger install.

My fiance has an old 900mhz iBook G3 running, in theory, an "upgrade" version of Tiger that was installed on top of OS 9.

Here's where the problems start. When she got her new laptop, she somehow managed to completely cannibalize the system. I don't just mean a few files are missing; I mean the control panels no longer work, the USB ports are non-functional, Safari hangs, I can't change date & time, and so on. Basically, the iBook can boot to her background screen, and I can select "reboot" from the Apple menu. Everything else is broken.

When I pulled it out of our closet, I guess I got that awesome "date and time" bug that large "easy PPC install" thread was talking about. I "reset" the machine with command-apple-P-R, but the date and time are set to Jan 1, 1969 still. Even better, I can't connect to the internet because I can't access the network port.

I don't have any OSX cds to work from.

I downloaded the community-supported 7.10 cds, and burned them from my Windows box (well, I'm downloading the alternate install cd now, but I reckon I'll get the same problems I'll detail below.)

Holding down C, the computer boots to the shell. I hit enter, it does some loading and hangs on a pure black screen. Reboot.

Hold down C, type "live-nosplash-powerpc video=ofonly", enter... Runs to a black screen with a CURSOR, then hangs. Reboot.

Reboot, get to the BusyBox shell, enter

"modprobe ide-core
exit"

Laptop loads a bit, then complains about various folders not existing. Can't do anything else, so I reboot.

Adding "break=top" to the command line does nothing. Same problem.

That's as far as I've gotten. I have no idea how to troubleshoot this, as I'm essentially installing a Klingon operating system on a broken Death Star - that is, I don't understand either system. :)

Help? Assume I can't reset date & time from the Apple GUI, and the OSX install is completely hosed.

---

### Post by tubasoldier on 2008-04-07
You do have the PPC version of Ubuntu don't you? not the x86 version?

---

### Post by BladeMelbourne on 2008-04-07
The busybox shell implies that it was a PPC install disk.

I would recommend downloading 7.04 (Feisty) alternate install disk. It seems fewer people report video/display issues than with 7.10.

---

### Post by tangibleorange on 2008-04-07
Hmm. There are a couple of things you could try:

[LIST]
[*]Download an earlier version, as suggested above.
[*]Download Ubuntu 6.06 - it's still officially supported and will be so for a year.
[*]Download debian for powerpc.
[/LIST]

like you i know very little about macs in general, but those are just a few things I've come across.

Also, about the clock, can't it be changed from the BIOS?

---

### Post by stream303 on 2008-04-07
> **lordfly said:**
> Let's start off with me. I'm a newbie Linux user. I installed 7.10 on my old Toshiba laptop a few months ago, very nice.

Well, Ubuntu or any variant should do nicely on that ppc machine, but it will be somewhat of a project if you are new to Linux, although if you aren't afraid of getting your fingers-wet with a bit of command line editing, you should be ok.

First, gather up all the information you can about your machine.  I suggest picking it out from here and saving all the relevant information.

[http://www.everymac.com/systems/apple/ibook/stats/ibook.html](http://www.everymac.com/systems/apple/ibook/stats/ibook.html)

It sounds like your OS9 and OSX are completely gone.  If so, that will make your install even easier by devoting the whole thing to Ubuntu - just use the "alternate" install image, and check the partitioning options to "use the whole disk".  That will automate all the partitioning, formatting etc for you, so you can usually get by that with no problems.  I'm not particularly good at restoring custom mac-os installs, so bear that in mind if you don't have the original Apple install disks, experience etc.

Like BladeMelbourne said,  I'd recommend Feisty 7.04 for your first attempt at install.  If all goes well, and your confidence builds, you can try your hand at installing Gutsy, or better yet, by that time the latest Hardy should be fully released.

You can grab the Feisty Ubuntu 7.04 image here.  Alternate recommended:

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

While we are glad to help out, be sure to have looked over this faq first:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

It should help you get past the time-date bug, and is good to have if you opt for Gutsy at the outset etc.

This is also a good faq:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Hopefully things will go well, but there could be a small amount of tweaking necessary from the terminal or from a rescue-mode - I'm sure we're all glad to help out any way we can.

Be aware that fancy 3d graphics and flash are not up to par with the x86 architectures - but they are coming along.  For some of us it isn't an issue.

---

### Post by VCF on 2008-04-07
I installed the Hardy liveCD (dated April 5) alpha (beta?) on my iBook G3/900, worked right out of the box, no problems :) You can get it at:

[http://cdimage.ubuntu.com/ports/daily-live/](http://cdimage.ubuntu.com/ports/daily-live/)

---

### Post by lordfly on 2008-04-11
Hi, sorry for the lack of updates, I've been swamped with other things.

Tried the 7.10 alternate cd, and installed it overnight. Rebooted, and now it'll show an ugly Ubuntu logo (maybe 256 colors? Display drivers or something?), and will proceed to one pixel, and then hangs, and then after about 3-4 minutes silently fails to the busybox shell.

According to this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337)

I have to "modprobe ide-core", which I do, which makes the g3 make some grinding noises, and then the shell just makes another appearance (silent fail?). I have no idea what modprobe ide-core is supposed to do, nor do I know how to make it do it automatically (the link above talks about doing some hacking about to get it into the boot sequence, but there's no step by step).

As for using this thing, it's main existence will be as an internet appliance, something I can surf the 'net with on the couch or in the kitchen while cooking.

---

### Post by lordfly on 2008-04-11
Well, I'm getting there.

Apparently you can type "exit" and the damn thing will continue booting ^_^

However, now I've hit the stupid ubuntudatebug. Log in, bunch of errors, brown screen of death.

Ctrl-Option-F1 makes the screen go screwy, rather than dropping me at a prompt.

Next course of action? :)

---

### Post by stream303 on 2008-04-12
Gotta' have guts to hang in there with Gutsy. :)

You are hitting a few bugs for sure, but they can be worked out.  I hate to say it, but you may want to investigate using Hardy-Beta "alternate", especially now that it is in feature-freeze state and so close to actual release.

[http://cdimage.ubuntu.com/ports/daily/](http://cdimage.ubuntu.com/ports/daily/)

Still, I looked up your machine on
[http://www.everymac.com](http://www.everymac.com)

and it appears that you are using an ATI rage mobility card.  The following thread may help out a lot, especially when you get to the second-stage boot at the yaboot prompt - you can enter kernel parameters specific to your card, and when you find a combo that works, you enter that into the /etc/yaboot.conf file:

[http://ubuntuforums.org/showthread.php?t=749715&page=2](http://ubuntuforums.org/showthread.php?t=749715&page=2)

Gutsy's modprobe-ide bug is well known, and it looks like you are past it temporarily.  To make this permanent, you'll need to follow these directions in "post install"
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Once we can get to a terminal with a good set of kernel parameters, we can edit that file with:

```
sudo nano -w /etc/initramfs-tools/modules
```

to make it permanent.

The Date bug issue is described and fixed here:
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

And then to top it off, you may be looking at editing your /etc/X11/xorg.conf file possibly.

Whew!  At this point I'd really be tempted to go with either the older Feisty or the latest Hardy-Beta daily image rather than Gutsy if you find yourself tearing your hair out. :)

---

### Post by shields on 2008-04-13
I spent forever trying to make this work on an iBook G4.

Here's the procedure I used:
[http://techtalk.shieldsgroup.com/2008/04/12/how-to-boot-an-ibook-g4-with-ubuntu/](http://techtalk.shieldsgroup.com/2008/04/12/how-to-boot-an-ibook-g4-with-ubuntu/)

Good luck.

---

### Post by lordfly on 2008-04-24
Hi all,

As far as I can tell my issue is with the iBook being unable to save time in its battery. Searching on Apple's support forums seems to conclude that there is no internal bios battery? It's simply refusing to keep the time on reboots, reverting back to 1904.


Again, sorry, I'm not a Mac guy, just a PC user who's used to the archaic inner workings of computers, not the voodoo apple stuff. :)

---

### Post by avtolle on 2008-04-25
I've a G4 Cube that needs its battery replaced, and had similar problems with the date. Being a bit swamped right now, I have elected to keep it powered up 24/7. So, a battery replacement sounds in order for you. Something that worked on the Cube before I figured out the battery needed replacing was to reset the PRAM on  boot up from a power off state, which on my machine is accomplished by : turning the machine on and immediately holding down the Command, Option, P and R keys (it helps my hand span is large) until the start up sound plays a second time; then release the keys, and it boots. HTH.

---

