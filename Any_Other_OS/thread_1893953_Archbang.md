---
title: "Archbang"
date: 2011-12-11
forum: Any Other OS
---

### Post by mauvebic on 2011-12-11
Its not easy getting used to when all you've ever known relates to the debian family of releases - but once you get used to doing sudo packer -S rather than sudo apt-get install, it's really not that bad. I mean, for me, its important to have an OS that makes the most of my hardware, rather than bug out and have people telling me to swap parts.

Still the biggest problem i have thus far is getting pacman/packer to resolve the host names of packages that AUR targets. Still im pretty optimistic that ill find out whats wrong. I'd rather deal with that than figure out why the cpu fan is 110% whenever i do anything worthwhile with my system :-)

what has your experience been?

---

### Post by BrokenKingpin on 2011-12-12
The biggest appeal of Arch to me is that it is a rolling release. That being said I currently don't have any real issues on Ubuntu or Debian to justify the effort of learning the Arch way of things.

I may give Archbang a try at some point though just to check it out.

---

### Post by Dlambert on 2011-12-12
> **mauvebic said:**
> Its not easy getting used to when all you've ever known relates to the debian family of releases - but once you get used to doing sudo packer -S rather than sudo apt-get install, it's really not that bad. I mean, for me, its important to have an OS that makes the most of my hardware, rather than bug out and have people telling me to swap parts.

Still the biggest problem i have thus far is getting pacman/packer to resolve the host names of packages that AUR targets. Still im pretty optimistic that ill find out whats wrong. I'd rather deal with that than figure out why the cpu fan is 110% whenever i do anything worthwhile with my system :-)

what has your experience been?

My wifi doesn't work (BCM4312)

---

### Post by mauvebic on 2011-12-13
> **Dlambert said:**
> My wifi doesn't work (BCM4312)

You need bcmwl-kernel-sources, i had that card in a laptop. though the only distribution i knew that had it in the install was crunchbang. all the other just had it in the livecd.

---

### Post by Dlambert on 2011-12-13
> **mauvebic said:**
> You need bcmwl-kernel-sources, i had that card in a laptop. though the only distribution i knew that had it in the install was crunchbang. all the other just had it in the livecd.

How would I do this? For clarification. In archbang or even arch itself, I followed a bunch of guides to no joy... :confused:

---

### Post by snowpine on 2011-12-14
> **Dlambert said:**
> How would I do this? For clarification. In archbang or even arch itself, I followed a bunch of guides to no joy... :confused:

Can you be specific (terminal output, error messages etc.) what you mean by "no joy"? The one and only guide you should need is the Arch Wiki:

[https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless)

Carefully follow the guide step-by-step and ask if you have any questions (preferably on the Arch forum but I'll keep an eye on this thread here too).

---

### Post by ratcheer on 2011-12-14
I have been using ArchBang / Arch for a little over two months. I am still just using it as a "get my feet wet" distro. I still use Ubuntu about 95% of the time. I feel like Arch's "keep it simple" philosophy interferes with my "get it done" approach. Sure, it is much less bloated, but when I want to do something, I don't want to take hours figuring out how to find, install, and configure it.

I finally got the ATI Catalyst driver installed, though. That was a big step. And, two days later, I got it upgraded from 11.11 to 11.12.

Tim

---

### Post by Dlambert on 2011-12-14
> **snowpine said:**
> Can you be specific (terminal output, error messages etc.) what you mean by "no joy"? The one and only guide you should need is the Arch Wiki:

[https://wiki.archlinux.org/index.php/Broadcom_wireless](https://wiki.archlinux.org/index.php/Broadcom_wireless)

Carefully follow the guide step-by-step and ask if you have any questions (preferably on the Arch forum but I'll keep an eye on this thread here too).

No joy = Not working

I'd have to reinstall, I'll try over the weekend, and I followed that guide and it didn't work for me.

---

### Post by snowpine on 2011-12-14
If you decide to try again over the weekend or whenever, then start with step 1:

> Determine which driver you need/can use

First, determine your card's PCI-ID. Type the following (case-sensitive) command into a console:

$ lspci -vnn | grep 14e4


---

### Post by Dlambert on 2011-12-14
> **snowpine said:**
> If you decide to try again over the weekend or whenever, then start with step 1:

Its the Broadcom 4312

---

### Post by snowpine on 2011-12-14
> **Dlambert said:**
> Its the Broadcom 4312

[https://wiki.archlinux.org/index.php/Broadcom_wireless#b43.2Fb43legacy](https://wiki.archlinux.org/index.php/Broadcom_wireless#b43.2Fb43legacy)

> b43/b43legacy

The drivers are included in the kernel since 2.6.24.
Loading the b43/b43legacy kernel module

Verify which module you need by looking up your device here. You can also check by computer model here. Blacklist the other module (either b43 or b43legacy) to prevent possible problems/confusion. For instructions, see Kernel_modules#Blacklisting.

Install the appropriate b43-firmware or b43-firmware-legacy package from the AUR.

You can now configure your device. 

---

### Post by Dlambert on 2011-12-15
> **snowpine said:**
> [https://wiki.archlinux.org/index.php/Broadcom_wireless#b43.2Fb43legacy](https://wiki.archlinux.org/index.php/Broadcom_wireless#b43.2Fb43legacy)

I will try this weekend.

---

