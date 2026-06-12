---
title: "Advice before installing Ubuntu on mid-2012 MBP"
date: 2016-12-04
forum: Apple Hardware Users
---

### Post by AlexStargazer on 2016-12-04
Hello everyone,

I’m planning on installing Ubuntu LTS, alongside OSX, on my mid-2012 _non_ retina mac. Before I start, I would like to ask for some advice; the information I’ve seen elsewhere on the Internet has been somewhat contradicting/confusing.

**Firstly**: I read that I need to use a program called rEFIt in order to dual boot the two OSs. Is this still necessary? I’m under the impression that this is needed for older macs, which use their own strange form of EFI, but is my 2012 mac in that category?

**Secondly*, ***file sharing. Ubuntu can’t write to journaled HFS+, and OSX can’t even read ext4. FAT has some annoying limitations. So, the only solution I know of is to use exFAT. I believe this requires that I install a kernel module in Ubuntu; also, should I format the exFAT partition using OSX’s Disk Utility?

**Thirdly**, drivers. I’ve already tested Ubuntu as a live USB: the webcam, sound, and keyboard backlight works. However, the wifi requires a proprietary broadcom driver. Does anyone if this works properly? Also, the laptop has an nVidia GT650M graphics card—and I don’t know much about the whole bumblebee/optirun thing.

Okay, I guess that’s most of my questions. For reference, the laptop specs are:

Processor: Ivy Bridge I7, quad-core 2.3GHz
RAM: 8GB DDR3, 1600MHz
GPU: Intel integrated + GT650M
Drive: 250GB Samsung EVO 850
Non-retina

---

### Post by AlexStargazer on 2016-12-05
Really, can no one advise me with this? I&#8217;m weary of any possibility that I might break the OSX install since I need this laptop for university.

---

### Post by howefield on 2016-12-05
Thread moved to the "*Apple Hardware Users*" - you might have better luck here.

---

### Post by AlexStargazer on 2016-12-05
*Thread moved to the "Apple Hardware Users" - you might have better luck here.*

Thanks.

---

### Post by &amp;KyT$0P# on 2016-12-05
1) Yes.  But it's called [rEFInd]("http://www.rodsbooks.com/refind/getting.html") now.

3) Wi-Fi works fine for me.  As for graphics, if you want to use the Intel graphics see [this]("https://ubuntuforums.org/showthread.php?t=2335586&p=13539492&viewfull=1#post13539492").

---

### Post by justaguyonline on 2016-12-12
Hey, it was pretty cool to see your thread since I also happen to be trying to install Ubuntu LTS on my mid-2012 Macbook Pro. I'm planning on triple booting (OS X, Windows 10, and Ubuntu Gnome 16.04), but I would love to swap notes so we can figure out what works best in Ubuntu (especially with wifi). This thread has already been a big help so far and I would love to hear how you've made it work.

In regards to an original question of yours, the solution I've seen for data sharing is to use a third, shared NTFS partition. Linux can read NTFS out of the box and just needs to be configured and OS X can too with a free install of ntfs-3g. [Here]("https://www.innoq.com/en/blog/triple-booting-a-mac/#installationofntfs-3g") are the instructions I'm planning on using myself.

---

