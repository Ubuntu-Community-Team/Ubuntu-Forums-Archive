---
title: "MBP SR 3.1 foray nightmare"
date: 2008-09-17
forum: Apple Hardware Users
---

### Post by freakalad on 2008-09-17
Hi guys,

So I've finally done it! I've finally sacrificed my beloved MBP, so that I can run my home server, work machine, eeePC (701) & MBP all Ubuntu 8.04.1+

The rest have gone off swimmingly, but I'm having no joy at all with my Mac.

Decided I want a single-boot Ubuntu (Gnome). I'll look into booting up OS/X off an external drive one day, should I need to do any hardware firmware upgrades. 
I was hoping to do a "Linux from Scratch" (LFS) or "roll-your-own" system, once I have everything running OK. I'd like to avoid custom kernel compilation, as this may get overly complicated it I need to upgrade at a later stage.

So, my setup so far:
* MacBook Pro Santa Rosa v3.1, MacTel Duo-core 2.4 GHz, 2 Gig of RAM (will beef this up to 4 Gig later, when I've got the $$$)
* Did a complete HDD wipe (no rEFIt; didn't see the point at the time)
* Set up LVM; following partitions:
  - Pri 250 MB /boot, outside of the LVM
  - In LVM I have the following partitions: /, /home, /var, /tmp, swap
* Used Ubuntu 8.04.1 AMD64 DVD to do installation

All-in-all, the installation went OK (just OK), and for all ends & purposes, I have a working system. Now there's a lot of hacking & tweaking & modding required to get the system up to speck and respectable, if I was to compare it to what I had before.
Don't get me wrong! I LOOOOOVE my Ubuntu (my work & eee are absolutely phenomenal), but I'm tired of mucking about to get some of the most basic thing working (wifi, bluetooth, 3D, power, fans, SMS, kb-backlight, touchpad, iR-RC, etc, etc). Some of it I've got work; most not

Has somebody got a customized ISO I can use, or some post-install script I can use to get it all going as it should? Even an older (8.04) 64-bit config that I can update/upgrade will suffice
Am I RTFM'ing the wrong resources? (there's a helluva lot out there)

---

### Post by cyberdork33 on 2008-09-17
> **freakalad said:**
> I was hoping to do a "Linux from Scratch" (LFS) or "roll-your-own" system, once I have everything running OK. I'd like to avoid custom kernel compilation, as this may get overly complicated it I need to upgrade at a later stage.Those statements seem counter-intuitive, but OK... Although, if you want something that is more "from scratch" you could checkout Gentoo.

> **freakalad said:**
> Has somebody got a customized ISO I can use, or some post-install script I can use to get it all going as it should? Even an older (8.04) 64-bit config that I can update/upgrade will suffice
Am I RTFM'ing the wrong resources? (there's a helluva lot out there)
No.
Again, for wanting a "from scratch" type of system, it seems very strange that you don't like "mucking about" in the system... That is what "from scratch" is all about really.

For your Mac, the proper guide to help with the hardware configuration is here:
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
and actually there are a lot of bugfixes in the newer Intrepid releases if you wanted to go ahead and try them out.

Much of the configuration has to be done because of the proprietary nature of the Mac. There is just not a lot of information available to get the hardware really well-supported. There are various discussions in this forum on that topic if you'd like to check them out.

Good Luck.

PS Please do not use that term for reading documentation, even for yourself. It is not considered proper in these forums.

---

### Post by freakalad on 2008-10-01
I've been mucking about with an Intrepid dist-upgrade on my MBP for a while now, with mixed results. 
Some stuff works & others don't; system is leaning towards instability

I might go the way of releasing a post-install script to get a "standard" installation up to scratch, but this won't be any time soon. 
Maybe someone else has already gone down this route & may be able to assist me.

As for my "roll ur own" statement I made earlier, I'm referring to something like RemasterSys ([http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)) image of a stable system, once it's up to speed

Will check & post back here again later

Thanks again 4 the info

---

### Post by freakalad on 2008-10-16
Thing's still far from perfect (getting better with every updage/upgrade), but I came across a solution to video driver issues:
EnvyNG

Works really well & got my video going better than I could've done myself

---

### Post by freakalad on 2008-11-03
Upgraded my MBP SR 3.1 to the latest Intrepid Ibex (aptitude dist-upgrade method). 
Still single-boot; will look into OS/X off ext HDD later; not a priority.

Solved issues associated with Atheros Ath9 proprietary driver, and power management seems a lot more stable.

Touchpad seems OK for now; can't recall what guide I followed at the moment

Still getting stability & general issues with "pommed" (the apple extra's like back-light, fans, motion sensor & such)

---

### Post by hanzomon4 on 2008-11-03
pommed not need... anymore

---

### Post by cyberdork33 on 2008-11-04
> **hanzomon4 said:**
> pommed not need... anymore
Correct. There are many items in the mactel-support PPA that replace it.
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

---

### Post by freakalad on 2008-11-04
That's fantastic, CD!

Thanks for the info; some of those resources where not available the last time I checked.

Will implement some of those changes, soon-ish.
I just hope I'd be able to extricate pommed & associated modules safely without breaking my baby

---

