---
title: "Desktop BSD"
date: 2007-04-14
forum: BSD
---

### Post by igknighted on 2007-04-14
Ok, so I saw Desktop BSD had a new (development) release out on Distrowatch.  Having never tried BSD, and this being a live CD, I figured why not give it a shot.  So I booted it up, and WOW, I was really impressed.  The boot was smooth, everything detected perfectly (my ATI vid card that linux hates got the proper resolution and everything), and the system just looks really slick and professional.  To steal a line from a favorite show of mine (Around the Horn), do you buy or sell Desktop BSD as a serious "contender" to linux?

Personally, I am still up in the air.  But as far as first boot experiences, this is the best I have had.  Lots of little details were accounted for, documentation is readily available, and theres this awesome mounting tool in my systray... more to follow, I just installed so now I get to really play :)

---

### Post by handy on 2007-04-14
Contender?

The BSD's are an outstanding OS IMHO.

With the Linux distro's & inevitable Solaris kernel based distro's that will continue to spring up, Haiku (hopefully), & the other's out there, *we have a lot of choices to contend with!*

& they are getting better all the time, (well most of them... :wink: )

The more choices the better I say. :D

---

### Post by igknighted on 2007-04-14
> **handy said:**
> Contender?

The BSD's are an outstanding OS IMHO.

With the Linux distro's & inevitable Solaris kernel based distro's that will continue to spring up, Haiku (hopefully), & the other's out there, *we have a lot of choices to contend with!*

& they are getting better all the time, (well most of them... :wink: )

The more choices the better I say. :D

True, and I am not meaning to discount them, but I would put DesktopBSD in the range of Suse or Ubuntu usability, while my experience with FreeBSD was more like Gentoo or Arch.  I attached a screen shot of the package manager in action.  I am compiling (by choice), there is an option to only use binary packages as well, although there aren't as many.  What strikes me is the over professionalism of the system, I am stunned at how well but together it is.  Every Solaris or BSD experience before has had major holes in hardware detection for me, and then DesktopBSD gets EVERYTHING, down to the Atheros Wifi card configured.  Impressive.

---

### Post by handy on 2007-04-14
I find the difference is as though Linux is growing organically with thousands of cells, & BSD is very much more controlled, planned by a small number of developers. 

Apparently, the PC-BSD people who make another great FreeBSD based OS, which is also optimised for the KDE desktop, put it to the DesktopBSD developers to move to a Gnome desktop so that there would be 2 great, easy to use, FreeBSD's giving people an easy choice for Gnome & KDE.  Great idea, unfortunately the DesktopBSD people did not want to talk about it!

---

### Post by igknighted on 2007-04-14
> **handy said:**
> I find the difference is as though Linux is growing organically with thousands of cells, & BSD is very much more controlled, planned by a small number of developers. 

Apparently, the PC-BSD people who make another great FreeBSD based OS, which is also optimised for the KDE desktop, put it to the DesktopBSD developers to move to a Gnome desktop so that there would be 2 great, easy to use, FreeBSD's giving people an easy choice for Gnome & KDE.  Great idea, unfortunately the DesktopBSD people did not want to talk about it!

I cannot say that I mind.  Maybe if they had a gnome and KDE version (or a DVD iso with both available) that would be OK, but I like the fact that DesktopBSD uses the ports system and compiles, but in a nice easy to use way.  And I would much rather KDE than gnome.  So for me, its the perfect storm of BSD.

---

### Post by .aku on 2007-04-14
> **igknighted said:**
> Every Solaris or BSD experience before has had major holes in hardware detection for me, and then DesktopBSD gets EVERYTHING, down to the Atheros Wifi card configured.  Impressive.

I agree, the hardware support & configuration in DesktopBSD is amazing.

I would leave Linux (yep, you heard me right) for BSD in a flash, only if my USB wireless optical mouse would work with BSD.
I need a new mouse. BSD, I will be back.

I really really like what they've done with 1.6RC2, it's super nice..
(although the acpi process needs some tuning (setting the hints in /boot/device.hints), but...)

//aku

---

### Post by handy on 2007-04-14
> **igknighted said:**
> I cannot say that I mind.  Maybe if they had a gnome and KDE version (or a DVD iso with both available) that would be OK, but I like the fact that DesktopBSD uses the ports system and compiles, but in a nice easy to use way.  And I would much rather KDE than gnome.  So for me, its the perfect storm of BSD.

PC-BSD & DesktopBSD are very similar, they are both FreeBSD with an easier front end to suit  desktop users.  PC-BSD also uses the FreeBSD ports, it just has the .pbi system as well for those that prefer it that way.

It would just be nice it there was an optimised Gnome FreeBSD for those that want it.  Installing Gnome on either of these BSD's is apparently not easy & makes for a slower machine due to the lack of developer work in the BSD-Gnome direction.

It was the PC-BSD implementation that converted me to KDE.  They trimmed KDE down a bit which obviously I like.

---

### Post by floke on 2007-08-05
Installed the latest Desktop BSD last night (1.6 rc3). Here are my early thoughts.

Installation was a breeze, and far easier than Ubuntu (no select '/' here). Also very quick, at 15-20 mins from booting the liveCD to having the installation done. Took the option to leave my boot loader untouched (very considerate), but then didn't know how to boot it! A quick google search (simple: title, root, chainloader +1 - again, far simpler than ubuntu, or Linux in general) and I was away.

D~BSD uses KDE, and very nice it is too; very professional looking. It provides you with a nice opening blurb on first boot; font rendering is excellent, and hardware detection is veru good. Straight in at the right resolution (1280x800), sound WORKS (hda_intel) :), but alas my wireless doesn't (Intel Pro 3945) - there's a beta driver for this but it crapped out on me in vmware, so am now ethernetted to my wireless router. 

Speed is awesome, and package handling is relatively easy to grasp (ports system and binaries) - I don't know much about this, but AFAIK all the compiling from source makes for a far sturdier system, even if it takes a while - am currently installing gnome, which I expect will take around 3 years.

On the downside:

* There is no flash - and my efforts with gnash and Linux compatability layers have merely resulted in an endless stream of crashed firefoxes.

* My Linux partitions are not being detected properly (will try to resolve this today)

* I have a strange thing going on with my toshiba touchpad - tapping works in some things (eg firefox, opera), but not others (taskbar, window borders etc) - maybe this is a KDE thing (I use gnome usually), and is not really a big deal.

All in all, I really like it and would heartily recommend for anyone wanting to play with a new distro.

---

### Post by igknighted on 2007-08-14
> **floke said:**
> Installation was a breeze, and far easier than Ubuntu (no select '/' here). Also very quick, at 15-20 mins from booting the liveCD to having the installation done. Took the option to leave my boot loader untouched (very considerate), but then didn't know how to boot it! A quick google search (simple: title, root, chainloader +1 - again, far simpler than ubuntu, or Linux in general) and I was away..

This is not anything different than Linux.  If you had installed, say, Mandriva on another partition and chosen to leave your GRUB on the MBR intact, you could do what DesktopBSD did and install a bootloader to the local partition.  BSD needed to do that because it uses a different bootloader, while Mandriva would not need to, but it does simplify the situation.  You would then add the exact same chainloader entry as you added for BSD pointing to mandriva's partition and Voila, should work the same.

Chainloader is basically a hand-off in a relay.  GRUB loads because it is on the MBR.  Then if a chainloader section is required, it "hands off" to the next bootloader, it could be Windows, could be a BSD bootloader, or it could be another GRUB.  This bootloader then acts as if it had just booted as normal and you keep going.  This makes running multiple distros very easy, because each package manager can update its own grub automatically upon a kernel update (saves you work!).

---

### Post by angryfirelord on 2007-08-20
DBSD is very good, but I prefer to use PC-BSD because I won't have to do tons of compiling (yes, I tried using binary updates, but the package manager couldn't find a lot of packages).

---

### Post by Steve1961 on 2008-01-22
I've just installed the recently released version of DesktopBSD - out of interest more than anything else - and I have to say I'm really impressed.  Apart from a temporary problem with an nvidia usb 2 controller on my motherboard (which I've 'almost' fixed), hardware detection is great, the live DVD booted without problems (more than I can say for the latest PCLinuxOS releases, which required noapic nolapic boot options), and the package management is really slick - as long as you set the option in the package manager to binary packages when possible.  It's a real shame that the DesktopBSD forum has very few postings because this system has real potential in my opinion.

---

### Post by Antman on 2008-01-22
It's funny that you posted this; I just installed it on my desktop just to test. The installer is very well done and polished and boot up times are pretty good.
It's a very clean system. 

I wasn't too impressed by the speed however. I always heard that BSD based systems were fast, but it seemed my Sidux, Zenwalk and Vector installs are faster (launching apps and overall feel). Now I didn't spend any time tweaking the DesktopBSD system so maybe it would have performed better, but as it stands I don't really see any reason for me to jump to DesktopBSD from linux.

Maybe when FreeBSD 7.0 is released I will try again.

---

### Post by Steve1961 on 2008-01-22
> **Antman said:**
> It's funny that you posted this; I just installed it on my desktop just to test. The installer is very well done and polished and boot up times are pretty good.
It's a very clean system. 

I wasn't too impressed by the speed however. I always heard that BSD based systems were fast, but it seemed my Sidux, Zenwalk and Vector installs are faster (launching apps and overall feel). Now I didn't spend any time tweaking the DesktopBSD system so maybe it would have performed better, but as it stands I don't really see any reason for me to jump to DesktopBSD from linux.

Maybe when FreeBSD 7.0 is released I will try again.

The default boot times aren't anything special, but whilst I've been fixing this usb issue I've needed to rebuild my kernel 5 or 6 times, and in the process I've trimmed it fairly substantially of the stuff I don't need.  I was amazed how easy it is to compile a kernel in BSD.  It only takes about 15 minutes on my machine and the kernel config is just a short text file.  Anyway, the system now flies.

---

### Post by Antman on 2008-01-25
> **Steve1961 said:**
> The default boot times aren't anything special, but whilst I've been fixing this usb issue I've needed to rebuild my kernel 5 or 6 times, and in the process I've trimmed it fairly substantially of the stuff I don't need.  I was amazed how easy it is to compile a kernel in BSD.  It only takes about 15 minutes on my machine and the kernel config is just a short text file.  Anyway, the system now flies.

hmmm... Since I am finding less need for my windowsxp partition, I may install DesktopBSD on it and play for a good while. :popcorn:

---

### Post by Steve1961 on 2008-01-25
> **Antman said:**
> hmmm... Since I am finding less need for my windowsxp partition, I may install DesktopBSD on it and play for a good while. :popcorn:


Only problem I'm having is trying to get my head round building a firewall with pf - but hey, it's all part of the fun :)

---

### Post by mips on 2008-01-28
> **Steve1961 said:**
> Only problem I'm having is trying to get my head round building a firewall with pf - but hey, it's all part of the fun :)

Just use Firewall Builder, [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

It gives you an easy to use GUI which then spits out the desired config for pf.

---

### Post by Steve1961 on 2008-01-28
> **mips said:**
> Just use Firewall Builder, [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

It gives you an easy to use GUI which then spits out the desired config for pf.

Funnily enough I've just discovered that.  I have to say I still prefer the simplicity of iptables with a firestarter front end though.

---

### Post by Ripfox on 2008-02-07
Is that KDE I see? 

I'm out.

:lolflag:

---

### Post by Antman on 2008-03-02
I'm wondering if DesktopBSD can be updated to the FreeBSD 7.0 base?!?:confused:

I have a IBM T60 I would love to try it on and I heard that FreeBSD version 7 has 3945 wireless drivers included.

I hope either PC-BSD or DesktopBSD makes a version based on 7.0 soon:popcorn:

---

### Post by scottro on 2008-03-02
Funny to hear you say that about pf--I was posting today on another forum how I hate iptables and love pf.  :)  Is it alright to post links to personal pages (with no advertising?)  I have a page that's a beginner's guide to pf.  (As you see from my post count, I'm new here, and not sure of the rules.)
Peter Hansteen liked it, anyway.  (He wrote a pf book recently.)

Re upgrading it to 7.0.  Yes, DesktopBSD is more FreeBSD-ish than PCBSD, although either one can be upgraded with the standard FreeBSD commands.   DesktopBSD as Oliver Herold will constantly tell you, is just BSD with a few GUI front ends.   However, you'll probably then have to upgrade KDE and I don't know if there are packages yet, you might have to use the ports, which will take quite awhile.    

If I were doing it, I'd first do the csup to upgrade to 7.0, then do a portsnap (or use their port front ends tool) and be sure to upgrade all ports.  That's one problem with a major release upgrade, even though there are compat libraries, upgrading ports can be time consuming, and some things may be broken..

As for pf, OpenBSD prides itself on its docs, and there's a link to their faq, which is really a user manual on their man web page.  It's quite good as is Peter Hansteen's page.

---

### Post by Fatman_UK on 2008-04-28
As a tenured FreeBSD noob and Ubuntu addict, I have a foot in both camps. IMO the OP is attempting to compare rosaceous pomes with citrus hesperidia when he asks about DesktopBSD as a "contender" to Ubuntu. Presumably the OP assumes the BSD projects care about market share of desktop systems. From hanging around the FreeBSD mailing lists, I can tell you that most BSD users (and I include developers in this) do not care which operating system you use. You should have seen the flames loosed upon a poor noobie recently who had the temerity to ask "why should I use BSD, then?"

The FreeBSD developer focus seems to be more "creating a system we like" than "creating a system everyone likes". It's a meme that pervades the FreeBSD community. Some of the more vocal FreeBSD users proudly proclaim that the best of all worlds is FreeBSD for servers and Ubuntu for desktops. (That's a great combination, by the way. I use it myself.) Of course, just because FreeBSD is this way doesn't mean DesktopBSD is, but since it's a fork of FreeBSD I'd bet my lunch money on it.

Speaking of DesktopBSD, I have recently been trying to decide between DesktopBSD, PC-BSD and DragonflyBSD for my BSD desktop slice. From what I can tell, Dragonfly looks the ugliest but the best engineered, and DesktopBSD is the prettiest - yes, KDE, but no-one said you can't install Gnome. A good rule of thumb for installing BSDs is: if you're not prepared to do some work, don't install a BSD. ;)

I've been having problems with using DesktopBSD in a VMware Server. It works fairly well but the file system is a bit unstable. One day I had to run fsck manually, twice. All I was doing was a regular ports upgrade. No way that should crash the file system. Either something about DesktopBSD doesn't like VMware Server, or they've somehow managed to make their UFS code unstable.

Most likely the flaw is a PEBKAC in the system. Does everyone have stability problems with VMware Server + DesktopBSD, or is it me?

---

### Post by cardinals_fan on 2008-04-29
> **Fatman_UK said:**
> As a tenured FreeBSD noob and Ubuntu addict, I have a foot in both camps. IMO the OP is attempting to compare rosaceous pomes with citrus hesperidia when he asks about DesktopBSD as a "contender" to Ubuntu. Presumably the OP assumes the BSD projects care about market share of desktop systems. From hanging around the FreeBSD mailing lists, I can tell you that most BSD users (and I include developers in this) do not care which operating system you use. You should have seen the flames loosed upon a poor noobie recently who had the temerity to ask "why should I use BSD, then?"

This is one of my favorite things about the BSD's - they avoid hype like a disease.  Afterall, where else would you find an OS which advertises itself as "the logical continuation of the FreeBSD 4.x series" (DragonFlyBSD, awesome btw).  I firmly believe in choice of OS, and I don't care what other people use.

---

### Post by mips on 2008-04-29
> **scottro said:**
> Is it alright to post links to personal pages (with no advertising?)  I have a page that's a beginner's guide to pf.  (As you see from my post count, I'm new here, and not sure of the rules.)


Yes, it is fine to post links to your own site.

I myself would like to see your pf guide.

---

