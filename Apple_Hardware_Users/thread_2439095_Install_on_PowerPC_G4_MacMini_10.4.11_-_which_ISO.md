---
title: "Install on PowerPC G4 MacMini 10.4.11 - which ISO?"
date: 2020-03-22
forum: Apple Hardware Users
---

### Post by jdoughe3 on 2020-03-22
Greetings!  

In this work from home era - I'm trying to revive a 2006 MacMini PowerPC G4 that's been in use as a dvd player for my tv.   I'd like to get any version of linux up and running - solely to run citrix desktop for work.

I've found amazing resources - but old resources.   I know enough to be dangerous - but would appreciate a guiding hand to find the right ISO.

I've read the PowerPC wiki - [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads). and the pinned forum post - where to install ubuntu on power pc.  [https://ubuntuforums.org/showthread.php?t=427714&highlight=mac+mini+PowerPC+G4](https://ubuntuforums.org/showthread.php?t=427714&highlight=mac+mini+PowerPC+G4)

Lots of good info.  I'll spare you all the things I've tried - most recent attempt below (I feel like I'm getting closer?)

For the 
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
the first desktop link is dead - [http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/](http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/)
so I went to the 12.04 link - [http://cdimage.ubuntu.com/releases/precise/release/](http://cdimage.ubuntu.com/releases/precise/release/)
And downloaded both of these and burned to two different DVDs[URL="http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04.5-dvd-amd64.iso"]
ubuntu-12.04.5-dvd-amd64.iso[/URL]
[ubuntu-12.04.5-dvd-i386.iso]("http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04.5-dvd-i386.iso")
Neither pops up in Startup manager (hold c while booting up)

Am I picking the wrong ISO?   Any advice appreciated.   Thanks already to this community for the vast resources!

---

### Post by gsahli on 2020-03-23
I have been using Ubuntu MATE 16.04 for a few years - stable but dog slow.
[http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/](http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/)

PS - I don't know about Citrix on Powerpc. You will have to use Mac OS 10.4 or 10.5 to get that.
Remember that most of what you read about ubuntu software is about Intel/AMD processors (and ARM is increasing lately).
I just checked, and although there isn't Citrix, there is an "rdesktop" client, which may give you access.

---

### Post by este.el.paz on 2020-03-23
To OP, those two options for 12.04 aren't showing "powerpc" in the name . . . U-MATE 16.04 was supporting PPC, but overall now the backports are not.  Look through some of the recent posts here, possibly in the "Arctic Fox" thread, or the other one that got moved here with my name in it, where the guy mentioned "wicknix" as doing re-spins of old distros that are supported.  I just managed to get the last distro of U-MATE 17.04 that was PPC installed on my G4 PowerMac, but, there is no browser that shows up in the install . . . so stuff is busted down.  Anything that says "i386" or "amd64" is going to be intel based and not PPC friendly.

---

### Post by jdoughe3 on 2020-03-23
Thanks, folks.  Love the PPC iso link- thank you!   NOW I understand that the x86 and arm iso links were never gonna work.  I tried so many!

So looks like I’m sunk.  Without a Citrix install - this plan don’t work.  Thanks for the rdesktop suggestion - but I’m trying to access company resources - they definitely wouldn’t like that.

The machine still has life.   without a browser though- it’d be so limited.  

I can’t stop thinking that there might be a way- but I think I should give up. If you think differently - Throw me a lifeline.

---

### Post by este.el.paz on 2020-03-23
Usually there are "alternative" choices to whatever you are trying to bring over to linux . . . but, yes, one of the cruel ironies of machines is that the hardware can exceed the software support for the hardware . . . .  Prolly better to just keep using the machine for what you were, and get into something newer to do "work" stuff?  But, look around, try to find support for PPC that is current . . . .

---

### Post by gsahli on 2020-03-23
I hope you noticed I said that Mac OS 10.5 or 10.4 Does have a Citrix client?
[https://discussions.citrix.com/topic/344912-citrix-receiver-for-mac-power-pc-g4-running-version-osx-1058/](https://discussions.citrix.com/topic/344912-citrix-receiver-for-mac-power-pc-g4-running-version-osx-1058/)

---

### Post by este.el.paz on 2020-03-24
> **gsahli said:**
> I hope you noticed I said that Mac OS 10.5 or 10.4 Does have a Citrix client?
[https://discussions.citrix.com/topic/344912-citrix-receiver-for-mac-power-pc-g4-running-version-osx-1058/](https://discussions.citrix.com/topic/344912-citrix-receiver-for-mac-power-pc-g4-running-version-osx-1058/)

@gsahli:

Hopefully that was noticed, if that is the key point for the OP, because these days going back to OSX 10.4 or 5 may be the better road to keeping the "ancient PPC" hardware running . . . native system, etc . . . .

---

### Post by ernsteiswuerfel on 2020-06-21
[INDENT]If you want a much more painfree experience with Linux on G3/G4/G5 hardware just skip this outdated distro and use another one. Also G3/G4/G5 PPC is no longer supported by Ubuntu.

These are (better) alternatives with bootable isos, current software (working browser, etc.) and current kernels:
[https://voidlinux-ppc.org/](https://voidlinux-ppc.org/)
[https://www.adelielinux.org/](https://www.adelielinux.org/)
[https://fienixppc.blogspot.com/p/download.html](https://fienixppc.blogspot.com/p/download.html) (64bit only, USB boot image)

Also no need to fiddle around with yaboot any longer. Void and Adelie use grub just like you know it from Linux on regular x64_64 hardware.[/INDENT]

---

