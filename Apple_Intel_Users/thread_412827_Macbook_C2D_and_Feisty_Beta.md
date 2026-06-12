---
title: "Macbook C2D and Feisty Beta"
date: 2007-04-18
forum: Apple Intel Users
---

### Post by [-Ghost-] on 2007-04-18
Hello,

I've recently been successful in setting up a triple boot on my new Macbook C2D. Kubuntu Feisty 7.04 Beta installed without a single hiccup and i was pleasantly surprised that the whole process for getting all 3 OSes working together ended up being so effortless. My OSX and WinXP boots appear fully functional, however there are still a couple nagging issues with the functionality of my Feisty boot. I've searched the forums here and elsewhere but most posts either deal with a CD instead of C2D Macbook, with a different version of Kubuntu, or with conflicting answers on workarounds/solutions. I tried replying to an existing post but it appears dead. So i apologize if this post was made erroneously.

One of the two issues that is apparant off the bat when i boot into Feisty is that the trackpad is extremely slow, navigating the mouse pointer takes an exceedingly long time. I've seen people reporting an overly responsive trackpad under Feisty, but not under-responsive. I am hoping that if there is no command-line workaround then Kubuntu updates will resolve the issue.

Which brings me to the most crippling issue. my wireless connectivity. I am only able to use wireless with my current setup using an Apple Aireport Express, but my Feisty boot remains the only OS unable to connect. I understand the chipset in the C2D differs from the CD and that people have been exploring a pair of work-arounds for this (ndiswrapper and madwifi). I've downloaded ndiswrapper 1.32 and a winxp/2k driver for what i've read is a compatible Lenovo chipset, moving the files from my OSX HD over to my FAT32 XP drive which i should be able to access under Feisty.  I'm wondering what the syntax would be for getting the chipset working using those files? Also, would waiting until thursday and downloading the official release of Feisty to over-write my existing Feisty install be the best solution?

Any input would be appreciated,

Thanks

---

### Post by ronocdh on 2007-04-18
Hello and welcome! [This]("http://ubuntuforums.org/showthread.php?t=397327") is a recent and very informative link that should get your trackpad in order. As for your wireless, I too triple boot and I was able to use ndiswrapper fine on my C2D MBP 15". I believe the guide I use was [this one]("https://help.ubuntu.com/community/MacBook"), which, yes, is for a MacBook, but nonetheless it works fine. The method is to mount the XP drive and grab the wireless drivers there (assuming you used Apple's driver CD from Boot Camp to set up XP).

Any more questions, post back! =)

---

