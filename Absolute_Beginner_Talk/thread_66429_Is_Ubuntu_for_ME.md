---
title: "Is Ubuntu for ME?"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by theosib on 2005-09-17
I'll apologize up front for asking the same question a thousand others have already asked.  Hopefully I'm different enough to make it no so boring for you.

I'm not really new to Linux, but this seemed the right forum to post in.  In fact, I've been using Gentoo for quite a while.  Gentoo's the sort of Linux distro that you use if you love working with OS admin details, or you want to learn them.  Well, I've reached a point where I've learned as much about admining a box as I can stand and want to get on with my life.  Now, I want a distro that will make things automatic for me, as often as possible, but I don't want something designed for people who have never used anything but Windows before.

In the extreme case, I'd like something that has the openness of Linux combined with the userfriendliness of MacOSX.  My problem with Gentoo is that while I understand OS concepts (and aced the course in college), I have no memory for the details.  So while I can set up the OS the way I like if I have a menu of choices, I have no hope if I have to read a 100-page manual to find out an obscure keyword I have to put into a config file burried deep under /etc.  At least, I don't have the patience for it anymore.  I'm a chip designer, not a sysadmin, so I want to get down to chip design and stop fooling around with admining my computer.

That boringly said, I'm told by some users that Ubuntu may be right for me, and that Ubuntu people are extra friendly in the forums and actually answer questions.  So I was hoping some of the experts could give it to me straight.  While I've encountered a number of problems with the LiveCD (and reported them on Bugzilla), so far, I'm encouraged.

There are a number of requirements I have in mind for an OS, and I was hoping the experts would help me to evaluate them and see how well Ubuntu fits.

(1) UI-based configuration.  I want to avoid hand-editing config files, unless I'm working around a bug.  If there's an app or a system facility, it should have a config tool.  It doesn't have to be a NICE one.  I just don't think I should have to hand-edit text files for basic stuff.  Sure, if I'm installing a more obscure tool, fine.  But if it's a basic thing like setting screen resolution, adding a user, partitioning a drive, setting up software RAID, etc., it should come with a config tool.

(2) Config should automatically survive upgrades.  The last time I updated my Gentoo install, I ended up with 140 config files that needed updating.  When etc-update got through with the trivial ones, there were 90 left.  90.  90 files that I had to sift through because the things is too stupid to figure out that in THREE of those files, I made a trivial change, like setting PHP to make GET and POST vars available as globals.  If I configure something using a GUI config tool, my settings should stick with me forever unless something becomes obsolete.  I can understand it being a little harder to deal with manual changes, but with a GUI config tool, there's no excuse.  

My Samsung laser printer comes with a Linux driver, and the installer basically just stomps on the CUPS config and puts in whatever it wants.  I am hopeful that that won't get obliterated every time CUPS is updated.

(3) Huge software library.  One really nice thing about Gentoo is that Portage is just vast.  I'm told apt-get is equally or more vast but that you often have to hunt around for a server to find what you want, and it's not always obvious which package you need to install for the program you want.  I'm also told that Ubuntu has their own servers, but I can't figure out if it has what I need.  There are two tools that I MUST have.  They are NOT optional.  They are iverilog and gtkwave.  Actually, I'm told that there are better signal viewers than gtkwave, so I'm willing to try something new.  But iverilog is the only open source Verilog simulator I know about.  Resolving to never again manually install an application, if I can help it, iverilog needs to be available through your usual apt-get service.  Is it?  I'm SURE you have most of the tools I want, but one other app that I really don't want to live without is nedit.  I also like to use gtkrellm2 for monitoring system stuff.  Oh, and I use the Trebuchet/Tk MUD client.  Do you have those?  How do I find them?

(4) Plug-and-play.  Actually, this is something that Ubuntu seems to be designed to do well.  The LiveCD automatically identifies my hardware, and I assume the regular install does the same.  It really irritated me that I was never able to get hotplug to work under Gentoo.  Two days of fighting with it, and I was eventually able to MANUALLY mount my USB flash drive.  Funny enough, I have had some trouble with Ubuntu and my flash drive.  5.04 has kded crash when unmounting the device, and 5.10 gives me a bizarre error when I insert the device into the slot.  I have reported these problems on your Bugzilla.  Hopefully they will be resolved.  

I would also like to find out how much trouble I would have to go through if I were to plug in a new scanner, for instance.  Will Ubuntu find it and automatically set up the right drivers?  Will KDE see it? Will SANE get setup correctly?  Will GIMP automatically see it?

(5) Firewall.  I was never able to get ipchains or iptables to work under Gentoo.  I hope they're available and easy to configure under Ubuntu.  With Red Hat, I could get it to work, but I had to manually open port 80 in a config file.  Can I avoid that fuss with Ubuntu?

(6) Upgrades.  I've already mentioned the config issues.  But I also want to be able to upgrade my whole system to the latest versions without having to worry that it's all going to break, taking me a week to fix it because that's how long it takes to get the questions answered.  Red Hat, when I last used it, suffered from dependency hell.  Gentoo handles dependencies just fine, but every time I would update, something major would break.  Most recently, I got a complaint from the x11-drm package about my kernel not having DRM configured as a module.  Come to find out that that module was only for 2.4 kernels, but no one would help me to figure out how that module got selected or how to remove it.  Oh, and I would like obsolete packages to be cleaned up automatically too.

(7) Kernel versus userspace dependencies.  One of my biggest complaints about Gentoo was that there were few dependency checks across the kernel boundary.  On occasion, something would check (like with the x11-drm issue above), but selecting a kernel option would never result in the correct userspace daemons to be installed, and userspace tools, if they bothered to check, would only produce errors if the kernel wasn't configured right (if at all) but would never actually just fix the problem.  Does Ubuntu have this stuff worked out pretty well?  IIRC, one good example is one of the facilities to populate /dev dynamically.  I don't remember the names, but one was kernel-based, while the other required a daemon to monitor things and create the right device nodes.  One was called udev, I think.  Anyhow, this is an example of something that has to be handled right, and should Linus change his mind again how it should be handled, an upgrade needs to make sure the right kernel and userspace configurations and tools are installed and configured properly.

(8) TCP/IP QoS.  This is just a pipe dream, wish-list item.  I would like to be able to set up the kernel network QoS JUST to give ACK packets priority so that uploads on my asymmetric broadband service don't choke the downloads.  Does Ubuntu have a tool that will help me set this up?

Ok, I think I've bothered you enough with my ranting, and I apologize.  Really, while I pick on Gentoo, really, there's nothing wrong with it.  A friend of mine swears by it, and he manages to get things to work that I could never figure out.  Obviously, I just don't have an aptitude for admining a Linux box.  I'm hoping I can get another distro, maybe Ubuntu, that will do most of that work for me.  I bought this machine to do my bidding, and I'm tired of baby-sitting it.  At the same time, I can't stand coding for anything other than Posix/GNU.

So, give it to me straight -- Will Ubuntu give me what I need?

It doesn't have to be perfect.  It just needs to strive for excellence.  It's okay if something doesn't work, as long as it's SUPPOSED to work, and there's someone there who can help me get it fixed.  (That's why I'm not too bothered by the USB problem... yet.)


I humbly thank everyone reading this for their infinite patience with my babbling and selfish demands.

---

### Post by npaladin2000 on 2005-09-17
You want either Ubuntu or BLAG (a version of Fedora Core).  Ubuntu's got the community, but some things can be a bit tricky, and will involve using the command-line.  BLAG has built-in MP3 support and a couple of other odds and ends to make getting off the ground REALLY easy.  Both use apt, which completely eliminate the so-called "dependency hell."  Actually, Fedora/Redhat don't suffer from it anymore either, thanks to the "yum" frontend, which works similarly to apt. 

Blag will have the advantage of being 100% compatible with Fedora 3 packages (TONS of Fedora3 packages around the net).  Ubuntu, since it differs from Debian a bit, is only about 90-95% compatible with Debian packages; you'll find some that won't work quite right, or will not be able to fill dependencies without a LOT of tweaking. 

You could also try Fedora Core 4, but it's a rather big install for a first timer (4 CDs, or a hard-to-use net installer).

---

### Post by UbuWu on 2005-09-17
To answer a few of your questions:

[QUOTE=theosib]
(1) UI-based configuration.  I want to avoid hand-editing config files, unless I'm working around a bug.  If there's an app or a system facility, it should have a config tool.  It doesn't have to be a NICE one.  I just don't think I should have to hand-edit text files for basic stuff.  Sure, if I'm installing a more obscure tool, fine.  But if it's a basic thing like setting screen resolution, adding a user, partitioning a drive, setting up software RAID, etc., it should come with a config tool.[/QUOTE]

Most things can be done through gui tools, not sure about RAID though... fro partitioning, install gparted

> 
(2) Config should automatically survive upgrades.  The last time I updated my Gentoo install, I ended up with 140 config files that needed updating.  When etc-update got through with the trivial ones, there were 90 left.  90.  90 files that I had to sift through because the things is too stupid to figure out that in THREE of those files, I made a trivial change, like setting PHP to make GET and POST vars available as globals.  If I configure something using a GUI config tool, my settings should stick with me forever unless something becomes obsolete.  I can understand it being a little harder to deal with manual changes, but with a GUI config tool, there's no excuse.  

When upgrading you are asked if you want to keep the old file or replace it with a new one. You can also view the differences at that moment. But this will almost never happen except when you upgrade to a new Ubuntu version.

> 
(3) Huge software library.  One really nice thing about Gentoo is that Portage is just vast.  I'm told apt-get is equally or more vast but that you often have to hunt around for a server to find what you want, and it's not always obvious which package you need to install for the program you want.  I'm also told that Ubuntu has their own servers, but I can't figure out if it has what I need.  There are two tools that I MUST have.  They are NOT optional.  They are iverilog and gtkwave.  Actually, I'm told that there are better signal viewers than gtkwave, so I'm willing to try something new.  But iverilog is the only open source Verilog simulator I know about.  Resolving to never again manually install an application, if I can help it, iverilog needs to be available through your usual apt-get service.  Is it?  I'm SURE you have most of the tools I want, but one other app that I really don't want to live without is nedit.  I also like to use gtkrellm2 for monitoring system stuff.  Oh, and I use the Trebuchet/Tk MUD client.  Do you have those?  How do I find them?

Ubuntu has a huge software library (around 16.000 packages). Gtklog and nedit are in it, iverilog is not (yet). You can search for packages available on [http://packages.ubuntu.com](http://packages.ubuntu.com) . If you need something that is not available, you can make suggestions for it to be inculded here: [https://wiki.ubuntu.com//UniverseCandidates](https://wiki.ubuntu.com//UniverseCandidates) . If you really need some exotic programs you can always compile them for yourself.

>  
(5) Firewall.  I was never able to get ipchains or iptables to work under Gentoo.  I hope they're available and easy to configure under Ubuntu.  With Red Hat, I could get it to work, but I had to manually open port 80 in a config file.  Can I avoid that fuss with Ubuntu?
You could install firestarter which makes it very easy to configure your firewall.

> 
Oh, and I would like obsolete packages to be cleaned up automatically too.
There are programs that can do this for you (e.g. debfoster) and there is work going on to have that happen automatically in future Ubuntu versions.

>  
So, give it to me straight -- Will Ubuntu give me what I need?

It doesn't have to be perfect.  It just needs to strive for excellence.  It's okay if something doesn't work, as long as it's SUPPOSED to work, and there's someone there who can help me get it fixed.  (That's why I'm not too bothered by the USB problem... yet.)

Nothing is supposed to be broken ;-)

---

### Post by theosib on 2005-09-17
> When upgrading you are asked if you want to keep the old file or replace it with a new one. You can also view the differences at that moment. But this will almost never happen except when you upgrade to a new Ubuntu version. 

So, what you're saying is that Ubuntu is no better than Gentoo about handling config files?  Neither keeping the old file nor replacing it with the new one is the correct answer.  The right thing to do is to incorporate older changes, if possible, into the new version.  Is the Ubuntu thing at least graphical?  The Gentoo one is terrible for making merges.  Not resolving configuration changes is one of my biggest pet peeves about Gentoo.  Is there no Linux distro that does it well?

And you make it sound like Ubuntu doesn't have intermediate package upgrades.  Gentoo would make new packages available individually as they were tested, and then periodically, they'll take a snapshot for a release.  Does Ubuntu not do this?  

I suppose I might have to give this up if I don't have a better way to get certain things to work that don't work with Gentoo.


> Ubuntu has a huge software library (around 16.000 packages). Gtklog and nedit are in it, iverilog is not (yet). You can search for packages available on [http://packages.ubuntu.com](http://packages.ubuntu.com) . If you need something that is not available, you can make suggestions for it to be inculded here: [https://wiki.ubuntu.com//UniverseCandidates](https://wiki.ubuntu.com//UniverseCandidates) . If you really need some exotic programs you can always compile them for yourself. 

Well, I can't do without iverilog.  Someone told me that they found it on a Debian server somewhere.  I'm sure I won't be able to fill out the information they need for me to add the suggestion.  What should I do?  Anyhow, compiling a program myself would be a step backwards from Gentoo, because none of the dependencies would be taken care of... none of the package management or anything.  That's not good.

---

### Post by bsussman on 2005-09-17
I won't go into minute detail, as the crucial stuff is macro - not micro.

I used linux before it had a whole number. When there was Slackware and some upstart called InfoMagic. And a couple I forgot like 

I have good unix skills.

Gentoo has a very compelling model - it custom builds itself to your configuration. By definition, this HAS to be more efficient, faster, yadda, yadda, yadda.

At the heavy price of making it more manageable by propellerheads (like you and me).

Ubuntu starts at the other end of the spectrum - it doesn't even ask you to size your partitions and swap. It is almost a no-brainer to install (almost means room for pneubeez (I'm bored with the other spellings) needing assistance).

It is brilliant that it installs with the assumprion that sudo will be the main tool for attaining root privs when needed. Brilliant that it does not even solicit a root password. Too bad it is so easy to put one in anyway. How many 'rm -rf' threads does ubuntu cause? Too many but not as many as some distributions.

Technically, I believe it is the very best 'for the masses' distribution (I do not like that other word that begins dist... - don't like Rap neither) yet made.

Yet it does have all the doors (locked or open) to the technical stuff, if needed). But I gotta tell you - every time I have given wrong advice, it is cuz the best answer lurked in a non-technical presentation. I have been a little too quick to open 3 terminal windows, when kcontrol (I do not like gnome a lot) would have been better and safer and more effective.

What's the price?  A less efficient (less fast, less small) system.

So what - mine is fast enough for me and my friends. Miles better than anything Microsoft ever dreamed of, because it still aims t please the user, technican, sysadm, not the accounting department and shareholders.

ubuntu is for you. Just stop, every time you are about to open a commandline tool and look for another way. You will not find one in every case but you will in many.

Sorry this is so long.  I forgot how much I like kubuntu.

---

### Post by aysiu on 2005-09-17
I agree with paladin. Blag may be a good choice for you. It's not Linspire-automatic (hiding everything from you), but it's pretty damn automatic, including a lot of codecs and things you may want. That said, the Blag community sucks. [Look how helpful they were when I asked about numlock](http://forums.blagblagblag.org/viewtopic.php?t=1159&highlight=numlock).

Ubuntu's community is top-notch, but every now and then, if you're doing something that's not everyday use, you may have to edit a config file. This is changing a bit with Breezy, but not completely. I've found (and maybe my needs are different from yours) that the only config files I've ever had to edit are

/etc/X11/xorg.conf
/etc/apt/sources.list
/boot/grub/menu.lst

And the [Ubuntu Guide](http://www.ubuntuguide.org) is nice because it's divided into sections in one huge page.

You may also be interested in Mepis, which is all point-and-click but, like Blag, doesn't hide everything from you the Linspire does. I've generally found Mepis to be a bit slow, though.

---

### Post by bsussman on 2005-09-17
[QUOTE=aysiu]You may also be interested in Mepis, which is all point-and-click but, like Blag, doesn't hide everything from you the Linspire does. I've generally found Mepis to be a bit slow, though.[/QUOTE]

I came here from Mepis.  Mepis is good.  Certain things worked for me, OOB, like my WiFi on my laptop.

But ubuntu's release build and testing schedule (a little more current than Mepis) may be better.

---

### Post by theosib on 2005-09-17
I'm feeling more and more encouraged about Ubuntu, but that config-file-upgrade thing kinds disturbs me.  Has no one thought of it before?  With all the other things that have to be put into a package, is it too much to ask to have the package automatically find, parse, and absorb the older version of the config file?

---

### Post by aysiu on 2005-09-17
[QUOTE=theosib]I'm feeling more and more encouraged about Ubuntu, but that config-file-upgrade thing kinds disturbs me.  Has no one thought of it before?  With all the other things that have to be put into a package, is it too much to ask to have the package automatically find, parse, and absorb the older version of the config file?[/QUOTE] Well, it prompts you. You decide whether you want to say "yes" or "no." I would hate it if the upgrade would just overwrite all my config files. Sometimes I modified because I want them modified. /etc/X11/xorg.conf, for example--if that gets overwritten, my screen resolution goes back to 400 x 320... not fun.

Just answer *y* to every question, and you should be fine.

Edit: Sorry. I misread your post. Parsing and absorbing changes from one config file to a new one actually seems like quite a task! Of course, I'm not a programmer, so I don't really know. Maybe it is simple. Do you want to write that program?

---

### Post by theosib on 2005-09-17
> Well, it prompts you. You decide whether you want to say "yes" or "no." I would hate it if the upgrade would just overwrite all my config files. Sometimes I modified because I want them modified. /etc/X11/xorg.conf, for example--if that gets overwritten, my screen resolution goes back to 400 x 320... not fun.
 
 Just answer y to every question, and you should be fine.
 
 Edit: Sorry. I misread your post. Parsing and absorbing changes from one config file to a new one actually seems like quite a task! Of course, I'm not a programmer, so I don't really know. Maybe it is simple. Do you want to write that program? 

Replacing the file is obviously bad, because it loses your changes.  But keeping the old one is also bad because you end up missing new settings that are needed and keeping options that break things.  I've had a few occasions when keeping the old file completely make a program nonfunctional until I manually merged the two files.

And as for how to merge things, there wouldn't be a universal approach.  Different programs do it differently, and each would need its own merge program.  But perhaps there is a way to generalize it somewhat.  If you could describe the grammar of the config file and some rules about merging, that would work.  Maybe I should think about working on something like that.

---

### Post by UbuWu on 2005-09-17
[QUOTE=theosib]
And you make it sound like Ubuntu doesn't have intermediate package upgrades.  Gentoo would make new packages available individually as they were tested, and then periodically, they'll take a snapshot for a release.  Does Ubuntu not do this?  
[/QUOTE]

Programs/packages usually don't get upgraded after release, only when there are security problems or major bugs. And even then the changes are 'backported' to the ubuntu versions of the program. This is to give you a system that is as stable as it can be. It is always possible to run the development version, which has continuous updates until a little more than a month before release, but you can expect to experience problems every now and then.

---

### Post by UbuWu on 2005-09-17
Oh and then there are the backports: newer versions of programs in the development version are backported to the stable version.

---

### Post by theosib on 2005-09-18
Ok, I see.  Generally, if there's an update, it's because of a bugfix, and it's only a minor revision difference, so there's no need to merge new and old config files.  Right?  What if the bug fix requires a config file change?

I'm used to working with a distro that doesn't favor stability and instead favors keeping very up to date.

Say... I have an idea for how we could make config file updates work more smoothly, and all it would require is that the package maintainer supply three files:  (a) the old version, where fields contain markers, (b) the new version, where fields contain markers, and (c) the new version where the fields contain actual values.   When upgrading, these are combined with the old version with actual values, and a simple pattern-recognition engine will resolve the changes. 

I had figured that package maintainers might have to write code to do this, but this way, they just have to provide the necessary examples.

How might I submit this?  Maybe it needs to be a project in its own right, and then all distros can adopt it.  I think this config file thing is a major black mark on the way Linux handles upgrades.

---

### Post by Seth on 2005-09-18
And Ubuntu already diffs config files. If you have made a change to a stock config file, Synaptic will notify you that they are different and show you a diff between your version and the new version.

---

### Post by theosib on 2005-09-18
> And Ubuntu already diffs config files. If you have made a change to a stock config file, Synaptic will notify you that they are different and show you a diff between your version and the new version. 

Well, if it's graphical and lets you manually merge them as you like, that's okay.  Gentoo's is text-based, shows hard-to-read diffs, and has a very unintuitive merge tool.  What's Synaptic's like?

Still, I think that there might be some room for making things more automatic.

---

