---
title: "Lubuntu on a eMac G4"
date: 2013-11-26
forum: Apple Hardware Users
---

### Post by LeoTheLion89 on 2013-11-26
I have a eMac 1.25GHz (underclocked to 1GHz since it was from a school) it has 1.5GB of RAM and a SuperDrive but i have a few questions.

I know you can install i386 software on amd64 Ubuntu but how do i force install i386 software on PowerPC Ubuntu?

How do i make the Lubuntu respond the same as OS X (i.e Command+C or Command+V to copy and paste rather than the windows version Control+C or Control+V)?

My AirPort Exterme card IS NOT even detected in OS X System Profiler says there is no AirPort card installed but Lubuntu 12.04 detects it and says Firmware missing. Why would Lubuntu detect it when Mac OS X wont?

how do i get DVD Playback to work on PowerPC Ubuntu? there is no PPC version of libdvdcs2

How do i get the Rockbox Utility to work on PowerPC Linux? it is a universal file that just extracts and opens on either 32 or 64 bit systems but simply does not open on PowerPC people over at Rockbox say it should work just fine.

---

### Post by Lars Noodén on 2013-11-27
i386 software will not install on PPC any more than it would on MIPS.  PPC is a different architecture, with different machine code instructions and in most ways superior.  Pretty much all software that is available to Ubuntu is available on the PPC.  There might be some blobs that are incompatible but those are very undesireable anyway from a maintenance and security perspective.  For what it's worth, IBM is investing $1 billion into Linux on PPC, but mostly on the server.

About the keyboard shortcuts, there's no easy way in LXDE.  You'll have to manually edit an XML file. 

[https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)

But if it helps to know, command (left and right, respectively) is Super_L and Super_R.

---

### Post by LeoTheLion89 on 2013-11-27
> **Lars Noodén said:**
> i386 software will not install on PPC any more than it would on MIPS.  PPC is a different architecture, with different machine code instructions and in most ways superior.  Pretty much all software that is available to Ubuntu is available on the PPC.  There might be some blobs that are incompatible but those are very undesireable anyway from a maintenance and security perspective.  For what it's worth, IBM is investing $1 billion into Linux on PPC, but mostly on the server.

About the keyboard shortcuts, there's no easy way in LXDE.  You'll have to manually edit an XML file. 

[https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)

But if it helps to know, command (left and right, respectively) is Super_L and Super_R.
I dont know what you mean by PowerPC linux being superior for the fact most sofware used dont work on it examples:
Chromium
Skype
Wine
CrossOver
PlayOnLinux
VirtualBox

I dont get how Firefox 25 can be installed on PPC Linux when the last version to work on the PPC Platform is 3.6. If Firefox 25 can be made to work on PPC Linux why is no one making it work on PPC OS X? Chromium is Open-Sorce of Google Chrome so why is Chromium not written for PowerPC Linux? Why is it that q4wine can be installed AND ran on PPC Linux but is unusable due to lack of Wine code?

---

### Post by dr.david.maloney on 2013-11-30
Firefox 25 can be installed on Linux PPC because talented and dedicated people, like the ones in this forum, ensure that it is updated on PowerPC Linux. PPC Linux is not OS X PPC, you need to grasp that concept before you go any further in tuxland.

 Tenfourfox, However is Firefox, ported to PPC OS X, which is currently at version 24 and still at source parity with Firefox, although the main developer, a MD (medical doctor, ie, he saves lives during the day, codes for PPC OS X at night-for free I might add) named Cameron Kaiser is running into some potential port busting issues with Australis. He plans on maintaining security and feature parity if he cannot maintain source parity with Firefox. It is very extremely likely that in the not too distant future there will be NO current browsers that are fully supported for OS X PPC. The toolkit is just getting too old. That is not the case with Linux, which has a constantly updated and improved toolkit, thanks to, again, talented and dedicated folks who work with Debian. Your other issues:

Chrome/Chromium-no PPC port of the V8 Javascript engine. Talk to Google, please.
Skype-again, no PPC port, talk to Microsoft, please.
Wine-x86, only, never has nor will there ever be PowerPC "support"
Crossover-x86, only, talk to Codeweavers, please
PlayonLInux, x86 only.
VirtualBox, virtualizes x86 only. There was a project, a long time ago and in a galaxy far far away (2005, no Intel macs except for the supersecret ones at Apple, Steve still alive) called Mac on Linux that did something similar. Its long long long dead. Perhaps you'd like to revive it. I know about a million PowerPC Linux users who'd love you forever for that.

Perhaps you should sell the imac G4 and pick up a used PC from the same era for ten or fifteen bucks, as it sounds like you want to Skype with your friends, use Chrome/Chromium and play Windows games on your imac G4, which is a total and complete impossibility. But not with Lubuntu x86.

I for one like to focus on what a PowerPC mac from that era CAN do, not what it can't do. Which is quite a bit, actually. Like, browse the web, crunch some numbers, watch funny cat videos on youtube. For what it can't do, I use a Dell and Debian. 

Peroid.

---

### Post by dand1972 on 2013-12-01
> **dr.david.maloney said:**
> Chrome/Chromium-no PPC port of the V8 Javascript engine. Talk to Google, please.

It looks like there's work being done on this:

[https://groups.google.com/forum/?_escaped_fragment_=topic/v8-dev/06ReYVfFgGA#!topic/v8-dev/06ReYVfFgGA](https://groups.google.com/forum/?_escaped_fragment_=topic/v8-dev/06ReYVfFgGA#!topic/v8-dev/06ReYVfFgGA) 

[https://github.com/andrewlow/v8ppc](https://github.com/andrewlow/v8ppc)

---

