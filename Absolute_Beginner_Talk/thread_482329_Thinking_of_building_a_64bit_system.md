---
title: "Thinking of building a 64bit system"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by JParkus on 2007-06-23
I would be using Ubuntu of course . The bare bone I'm looking at has a gig of memory with it Athlon  64 3200+ 160 gig hard drive bla bla bla. Anyways the question I have is are there any issues with the visual things that I've learned to love like Beryl and Avant? Either way I just found out the computer I've been using only has a 650Mhz Pentium . So I would like something newer.

---

### Post by jpkotta on 2007-06-23
NVidia makes 64-bit drivers, and they work.  I haven't tried Beryl, but the video drivers are the only thing that might make it a no-go for 64-bit.  I don't know about ATI.

You can run just about anything that is 32-bit in a 32-bit chroot.  It can take some effort to set up a chroot ([https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)).  The main things that cannot be worked around with a chroot are device drivers, like the video driver.

---

### Post by Jimmyfj on 2007-06-23
I have a AMD Athlon 64 3000+ System build on a MSI motherboard, ATI Radeon 9600 and a 160 GB SATA HDD - I haven't managed to get Beryl working, nor Macro media flash player, I have built a server on it till better 64 bit support arrives. Hopefully that'll be very soon.

---

### Post by Phixion on 2007-06-23
Unless you're going to be encoding/decoding or using apps that make use of 64bit processors it just isn't worth installing imo.

You get more problems with certain apps/drivers not working than its worth.

Just go for the 32bit version :D

---

### Post by Bostonian on 2007-06-23
I just installed the 64 bit distro to play around with. Beryl and avant will work fine, but you'll be spending a lot more time with your computer. Realmedia doesn't work, if you use a 64 bit browser, theres no flash, and there's all sorts of little things that don't "just work" anymore.

---

### Post by BobCFC on 2007-06-23
> **Bostonian said:**
> I just installed the 64 bit distro to play around with. Beryl and avant will work fine, but you'll be spending a lot more time with your computer. Realmedia doesn't work, if you use a 64 bit browser, theres no flash, and there's all sorts of little things that don't "just work" anymore.


Yeah Beryl works fine.   There is a way to run the 32bit flash plugin in a 64bit firefox browser.  you can install it easily: [using this script]("http://ubuntuforums.org/showthread.php?t=425672")

I am watching YouTube and Google video perfectly now on Feisty Fawn 7.04 64bit using 64bit firefox.


PS There is no 64bit flash for windows either,  they just settle for 32bit browsers doh!

---

