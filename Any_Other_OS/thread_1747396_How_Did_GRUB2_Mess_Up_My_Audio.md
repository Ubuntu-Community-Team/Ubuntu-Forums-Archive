---
title: "How Did GRUB2 Mess Up My Audio?"
date: 2011-05-02
forum: Any Other OS
---

### Post by mattjw on 2011-05-02
Whenever I'm not playing any media, I get a crackling and popping sound coming from my speakers every five seconds or so. When I turn on music or video, it goes away and plays fine.

My guess is that reinstalling GRUB did this, but I can't find anything on how that would affect my audio hardware.

Let me walk you through what happened.

I have Linux Mint running on a PC with a ASUS Xonar soundcard connected with an internal sp/dif cable so that the sound comes out of the Nvidia graphics card HDMI.  That goes to my TV and through the surround sound.

Everything worked just fine.

Then I need to add a window's partition.  I booted from a LiveCD, repartitioned the drive (using G-Parted), installed Windows XP on the new partition, booted back up with the LiveCD and recopied GRUB2 to the disk (using the SIMPLEST method [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")) 

Then when I started up Mint, I get the crackling.  (Don't even get me started on the sound in WindowsXP).

I've made sure it's actually the sound coming out of the computer, and not due to the cable or surround sound or TV or anything.

Any ideas on where I can start to look?

---

### Post by Perfect Storm on 2011-05-02
Moved to Other OS/Distro Talk.
Please also read: [http://ubuntuforums.org/showthread.php?t=1721564](http://ubuntuforums.org/showthread.php?t=1721564)

---

### Post by mattjw on 2011-05-02
Solved! It wasnt a software issue. It was hardware. 

I opened up the case and just moved some internal cables around. Specifically my internal spdif line was intertwined with the hard drive cables. They must have been causing interference. Gave them some breathing room and its all better.

---

