---
title: "Newbie Software Questions"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Fuzzgun on 2007-04-15
Hi to everyone on the forum,
Main System Hardware:
ASUS A8V DELUXE
AMD OPTERON 180
ATI RADEON X1950PRO AGP
2GB OCZ PLAT REV2 PC3200
SEAGATE BARRACUDA 160GB SATA x 1
SEAGATE BARRACUDA 160GB ATA-100 x 1
AUDIGY 2 SZ SOUND CARD
NEC DVD RW ND-3250A
SPEEDTOUCH 580 WIRELESS ROUTER

I have just set up Ubuntu 6.10 Edgy on a spare hard drive, so that I can get used to it and tackle any problems before installing on my main hard drive(haven't tackled the drivers for my ATI Radeon X1950 Pro yet!). 
My questions are really about software for Ubuntu and what I really need for internet security and hard disk performance.
On my main hard drive I have WinXP home edition and I have been using NOD32 anti-virus, Sunbelt Kerio Personal Firewall, Webroot's Spysweeper & Window Washer, Evidence Eliminator and Kremlin Sentry for a few yeras now.

I know that NOD32 is available for linux users but is it necessary or are there better programs out there?
Should I install firewall software (Firestarter for example) or will the firewall with my Speedtouch router be enough?
What options/software are available for preventing/eliminating spyware?
I use Evidence Eliminator about once a month and Webroot's Window Washer once a day to help remove built up/left over crap from my hard drives,  but are there any similar alternatives for Ubuntu users?

Any help or opinions on any of the above would be greatly appreciated.

Thanks.

---

### Post by tchoklat on 2007-04-15
Ubuntu / Linux does not require anti-virus, spy ware, or Firewalls. It is secure , or at least as secure as it can be. This issues has been discussed on these forums often. Also defragmenting etc is not required either.
 
 
tchoklat

---

### Post by Fuzzgun on 2007-04-15
Many thanks.

---

### Post by TheSe7enthSin on 2007-05-02
But is there some software that is similar to Window Washer?
A program that can clean the system and delete unwanted files.

---

### Post by caramelsoul on 2007-07-25
I

---

### Post by caramelsoul on 2007-07-25
I would also like an application similar to Window Washer, does any one know of such a thing for Ubuntu?

---

### Post by az on 2007-07-25
> **caramelsoul said:**
> I would also like an application similar to Window Washer, does any one know of such a thing for Ubuntu?

I never heard of such a thing.  So I checked the website:
Quote:

"Window Washer: 
- Scrubs hundreds of areas on your PC to remove unnecessary files to ensure your privacy and free up valuable disk space. 

- Cleans all aspects of your Internet browser activity, including Internet history, address bar, cache, cookies, and more. 

- Eliminates useless files that clog your hard drive and slow down your PC 

- Washes free space on your computer that contains portions of old and previously deleted files and documents. "


Well, Ubuntu is free-libre open source so it's not compromising your privacy (unless you install proprietary software on it)  Basically, closed-source software can easily do things behind your back, because your computer becomes a black box.  Ubuntu is not like that.  It would be very difficult for someone to upload a program that does that into the repositoties.

There are no bits and pieces that slow down your hard drive.  Windoes uses a registry which is not built for performance.  As time goes on, the registry fills and your computer slows down.  There is no such thing in Ubuntu.

As for disk space and unwanted files, you may want to clear the logs eventually, but they get compressed down regularly so they won't take up a significant amount of disk space.  Temporary files are cleared every time you boot.  Your browser cache is completely under your control.  Other that that, you can tell the package manager to clear out any downloaded package files.

---

### Post by Soybean on 2007-07-25
> **tchoklat said:**
> Ubuntu / Linux does not require anti-virus, spy ware, or Firewalls. It is secure , or at least as secure as it can be. This issues has been discussed on these forums often. Also defragmenting etc is not required either.

To clarify on this a little:
-Linux systems do not need virus scanners or spyware detectors for themselves. However, if your Linux system dual-boots Windows, or is on a network with Windows systems, having a Linux-based virus scanner can sometimes be helpful for protecting the Windows installs.
-Linux systems DO need a firewall. There's a basic one installed and set up by default in Ubuntu, and it's sufficient for most people. Even people with more advanced firewall requirements typically just modify the settings on the built-in firewall (sometimes using a 3rd-party tool)

As for the "Window Washer" type programs, I think something similar that might be more useful than most Linux users are willing to admit. ;) But it's true, *as a general rule*, that it's not needed. If unwanted files are filling up your disk or slowing down your system, it probably means that something is configured incorrectly or is otherwise broken. So the Linux solution is to track down the source of the peculiar behavior and fix it at the root, rather than just letting the junk accumulate and clearing it out periodically. This is obviously a better solution, but it can be difficult for new users sometimes.

---

### Post by jd65pl on 2007-07-25
See the linux security section

[http://jamie.dumbill.googlepages.com/l_virus.html](http://jamie.dumbill.googlepages.com/l_virus.html)

---

