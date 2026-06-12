---
title: "Ubuntu install on Dell CPX"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by BillB on 2008-01-31
I am intending to do a fresh install of Ubuntu 7.10 on a Dell CPX laptop....650MHz, 512GB (that ran Win XP fine).  The HD will be completely cleaned.
Is it possible to get Ubuntu running w/ a wireless PCMIA adapter?  Or can it only be installed as a backup/dual boot OS that has to have a MS OS already connected to the internet?
Sometimes I think that it's impossible for a novice to get Linux running w/o endless tinkering & downloads....requiring a MS internet connection.

Any pointers will be appreciated.

---

### Post by stalker145 on 2008-01-31
> **BillB said:**
> I am intending to do a fresh install of Ubuntu 7.10 on a Dell CPX laptop....650MHz, 512GB (that ran Win XP fine).  The HD will be completely cleaned.
Is it possible to get Ubuntu running w/ a wireless PCMIA adapter?  Or can it only be installed as a backup/dual boot OS that has to have a MS OS already connected to the internet?
Sometimes I think that it's impossible for a novice to get Linux running w/o endless tinkering & downloads....requiring a MS internet connection.

Any pointers will be appreciated.

I installed Ubuntu (and Fluxbuntu) on a Dell CPi-A, 366MHz, 128MiB RAM, and a 4MiB video card without too many problems. This thing's so old that it has no mini-PCI slot nor does it have an ethernet port. If I can do it on there, you shouldn't have any problems with yours.

As for the wireless, I would suggest checking the [Hardware Compatibility Page]("https://wiki.ubuntu.com/HardwareSupport") for your desired wireless adapter. There are quite a few that work "out of the box" for your convenience.

---

### Post by p_quarles on 2008-01-31
Thread moved to Absolute Beginner Talk, since I'm guessing that a 650MHz CPU is not a 64-bit one. If I'm wrong, let me know and I'll move it back.

---

### Post by BillB on 2008-01-31
> **p_quarles said:**
> Thread moved to Absolute Beginner Talk, since I'm guessing that a 650MHz CPU is not a 64-bit one. If I'm wrong, let me know and I'll move it back.

Right....I didn't notice the 64-bit part of that, thanks.  The Dell CPX is 32-bit.

---

### Post by BillB on 2008-01-31
> **stalker145 said:**
> I installed Ubuntu (and Fluxbuntu) on a Dell CPi-A, 366MHz, 128MiB RAM, and a 4MiB video card without too many problems. This thing's so old that it has no mini-PCI slot nor does it have an ethernet port. If I can do it on there, you shouldn't have any problems with yours.

As for the wireless, I would suggest checking the [Hardware Compatibility Page]("https://wiki.ubuntu.com/HardwareSupport") for your desired wireless adapter. There are quite a few that work "out of the box" for your convenience.

Was that 7.10 that worked OK on a Dell laptop?   Will 7.10 have the right video, audio, PCMIA etc. drivers?
I chose Ubuntu because newer Dell's can come with it.

---

### Post by BillB on 2008-01-31
> **stalker145 said:**
> I installed Ubuntu (and Fluxbuntu) on a Dell CPi-A, 366MHz, 128MiB RAM, and a 4MiB video card without too many problems. This thing's so old that it has no mini-PCI slot nor does it have an ethernet port. If I can do it on there, you shouldn't have any problems with yours.

As for the wireless, I would suggest checking the [Hardware Compatibility Page]("https://wiki.ubuntu.com/HardwareSupport") for your desired wireless adapter. There are quite a few that work "out of the box" for your convenience.

I have been to the "Hardware Compadibility Page"....it didn't show any listings for PCMIA adapters, only USB?

---

### Post by stalker145 on 2008-02-01
> **BillB said:**
> Was that 7.10 that worked OK on a Dell laptop?   Will 7.10 have the right video, audio, PCMIA etc. drivers?
I chose Ubuntu because newer Dell's can come with it.

It was actually 7.04 that I installed. I tried 7.10, but it didn't really like my Linksys USB adapter for some reason.

> **BillB said:**
> I have been to the "Hardware Compadibility Page"....it didn't show any listings for PCMIA adapters, only USB?

Sure, they're there. The below are just the 'A's that have PCMCIA cards listed.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards3com](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards3com)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAdaptec](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAdaptec)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAriaextreme](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAriaextreme)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus)

You have to go to "Wireless Network Cards" and then check each manufacturer. It's a pain, but it's worth it in the long run.

---

### Post by BillB on 2008-02-01
> **stalker145 said:**
> It was actually 7.04 that I installed. I tried 7.10, but it didn't really like my Linksys USB adapter for some reason.



Sure, they're there. The below are just the 'A's that have PCMCIA cards listed.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards3com](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCards3com)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAdaptec](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAdaptec)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAriaextreme](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAriaextreme)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus)

You have to go to "Wireless Network Cards" and then check each manufacturer. It's a pain, but it's worth it in the long run.

Oh' my mistake....I guess the PCMIA cards are under PCI!

My 2WIRE is not on the list....but 2WIRE IS on other lists.  Who knows....


As a novice, I'm just so discouraged with how SO many things can go wrong w/ Ubuntu (Linux).   It seems every step you take there's another PROBLEM.
Just getting Ubuntu installed w/ a way to get on the internet (it's USELESS until you do) is mind boggling!

Why doesnt SOMEONE make a Linux that is easy to install/understand, and comes with a simple way of connecting to the internet (w/ most wifi card/chips)?   Forget all the fluff........just make those 2 things EASY.   Then you can download all the fluff AFTERWARDS!

Something software people just don't understand.

2 simple things!

---

### Post by stalker145 on 2008-02-02
> **BillB said:**
> Oh' my mistake....I guess the PCMIA cards are under PCI!

My 2WIRE is not on the list....but 2WIRE IS on other lists.  Who knows....


As a novice, I'm just so discouraged with how SO many things can go wrong w/ Ubuntu (Linux).   It seems every step you take there's another PROBLEM.
Just getting Ubuntu installed w/ a way to get on the internet (it's USELESS until you do) is mind boggling!

Why doesnt SOMEONE make a Linux that is easy to install/understand, and comes with a simple way of connecting to the internet (w/ most wifi card/chips)?   Forget all the fluff........just make those 2 things EASY.   Then you can download all the fluff AFTERWARDS!

Something software people just don't understand.

2 simple things!

I understand your frustration and can sympathize. I've had my share of problems also. The first time I installed Ubuntu was on my tower that now works perfectly. However, 2 years ago when I ran through the installation (mind you, everything worked in the LiveCD) I rebooted and was met with a message stating that my OS couldn't be found. It turned out that my IDE expansion card was throwing everything off. Since that time, the programmers have found a way to make things work out for the better.

As for your problem: I really hate pointing fingers, but in this case it must be done. What is happening is that the company that makes the drivers for your device have not come out with a driver for Linux nor have they opened up their current Windows drivers for our programmers to tinker with. It is no simple process, I'm sure, to create a driver for all the different devices that may happen to be in someone's computer so that they can be assured that Linux will work on their box.

Until the day comes that we can be assured that anything we pick up off the shelf will work with our OS, we must be vigilant. We must research every device we consider purchasing to see if it has even the most remote possibility of working with Linux.

As a closing example, and a sort of prayer, I'll say this: yesterday I was in CircuitCity and BestBuy looking for a TV tuner card. After a lot of research and talking to their "techs", I decided of the Hauppauge WinTV-HVR 1600. I decided on this one simply because on the Hauppauge web site, they came out and said that they were working on Linux drivers and currently had beta drivers available.

Research is key. I will now be shutting down to see if my limited research paid off.

Good luck in your venture as well.

---

### Post by BillB on 2008-02-02
Come to think of it there are 3 things that I want.
#1 Find a linux that will work on my Dell CPX (a VERY popular 'older' laptop).
#2 Be able to connect to the internet w/ it (wifi card).
#3 Be able to use my Canon digital camera w/ it (a very popular camera maker).

I haven't started installing Ubuntu yet, but the guy who's giving me the 7.10 CD said that I should look into problems w/ my Dell before I start.
Now that I have looked into it, I'm thinking that in the long run, going back to MS may be better....if not easier?  (a friend gave me a XP CD).

It seems Linux is still (only) for software engineer types?

---

