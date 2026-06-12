---
title: "MTP MP3 player recognised as digital camera"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by bedfojo on 2007-01-12
I am running Ubuntu 6.06, fully updated.

My girlfriend has a Philips PSA615/05 MP3 player. It uses the MTP protocol. I have installed (compiled) the latest versions of libnjb, libmtp and gnomad2. However when I plug in the player, the system thinks it is a PTP digital camera. However it then fails to load the drivers and I cannot access the player from ubuntu in any way. It has always done this with the player, even beofre I installed gnomad2/libmtp etc.

Is there any way of getting the system to stop trying to identify the player as a camera and let it use libnjb/libmtp instead, as these should work with the player.

NB: the packages work OK with my Creative Zen Touch mp3 player, so there is no problem ith the install.

I'm loving ubuntu and I want to find a way to avoid booting into Windows just to upload music to my girlfriend's MP3 player! Thanks to the wonderful ubuntu community out there in advance.

---

### Post by bedfojo on 2007-01-12
Bump. Any ideas, please?

---

### Post by Indras on 2007-01-12
I recently got a friend's Creative Zen Portable Media Center (the video iPod clone) to work in Gnomad2.  Every time you plug it in, it is recognized as a digital camera, you simply have to click the "ignore" button, then open Gnomad2, and go to "Jukebox Library"->"Rescan Contents" and it will connect with the Zen.

The only advice I can give you is to check out any forums specifically on gnomad... it may not be a supported device yet.  I remember reading that you can use the ID number from the output of "lsusb" and manually add it to one of the gnomad2 config files, and occasionally,  it will work.  Sorry, I wish I had more details (or that I'd bookmarked that site!)

---

### Post by bedfojo on 2007-01-12
Thanks, but when I click on ignore and then go to Gnomad2, it says that there is no player attached to the USB bus.

I have hacked the conf files for libnjb and libmtp to add the device codes to them (which I had to do for my Zen as well) but it still thinks the Philips player is a digital camera!

Is there a conf file for libgphoto? Maybe if I can comment out something there, the system would stop trying to identify the player as a camera.

---

### Post by orb9220 on 2007-01-12
MTP devices are a pain. But I have  latest Amarok running in gnome Edgy see's my sansa e-250 when it is MTP or MSC which is also know as standard usb device.

Sorry couldn't be more Helpful.

---

### Post by NESFreak on 2007-01-20
> **bedfojo said:**
> Thanks, but when I click on ignore and then go to Gnomad2, it says that there is no player attached to the USB bus.

I have hacked the conf files for libnjb and libmtp to add the device codes to them (which I had to do for my Zen as well) but it still thinks the Philips player is a digital camera!

Is there a conf file for libgphoto? Maybe if I can comment out something there, the system would stop trying to identify the player as a camera.

That's because libmtp isn't compiled in into gnomad.
see [http://www.ubuntuforums.org/showthread.php?t=199250](http://www.ubuntuforums.org/showthread.php?t=199250) for help with gnomad. Or install libnjb and libmtp through synaptic and install [this]("http://ubuntu.moonman.se/i386/gnomad2_2.8.8-1_i386.deb") version of gnomad.
 Or see [http://www.ubuntuforums.org/showthread.php?t=273137](http://www.ubuntuforums.org/showthread.php?t=273137) for help with amarok.

NESFreak

---

