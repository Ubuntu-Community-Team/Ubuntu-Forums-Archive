---
title: "Another Computer Being Switched"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by P4rD0nM3 on 2007-10-10
Hey guys, I posted awhile ago about switching my old HP desktop to Ubuntu and it was a great success. That computer used to have XP installed. I did a clean install of Ubuntu 7.04 and man it sure made that old hp desktop faster especially without those bundled programs from HP. My old video card (GeForce FX 5500) died 2 years ago and I haven't even called BFG to replace it (Lifetime Warranty), however with Ubuntu, I somehow feel that I need it JUST BECAUSE. Hehehe. It's going to be shipped back later this month.

The Ubuntu community has been very helpful unlike other linux communities that I've been to, where they want to filter out the newbies. This community is sending the right message about Linux and I appreciate it.

So now, I'm ready to convert another desktop that I have to Ubuntu 7.04. Here's the specs for the desktop:

AMD 64 X2 4200+
4 GB DDR2
640 MB 8800 GTS

My questions are:

1. Should I go 64 bit? Why?
2. I have a NVIDIA 8 series video card, will this have any sort of problem with Ubuntu?
3. Right now, I have a 250GB HDD, I'm planning on purchasing another 250GB so I can do a Raid0. Does this have any effect on Ubuntu?
4. This will connect to the internet through a wireless router.

---

### Post by cameronw on 2007-10-10
> 
1. Should I go 64 bit? Why?I think some packages (32 bit) need a 32 bit system to install, so I personally wouldn't use 64 bit but there is the bonus of increase speed. Your call really but I'm not sure if all packages have equivalent  64 bit versions. 

>  2. I have a NVIDIA 8 series video card, will this have any sort of problem with Ubuntu?Shouldn't be a problem. All 8 series card are supported with restricted drivers.
>  4. This will connect to the internet through a wireless router.Hmm could be a prob finding drivers for pci card or inbuilt wifi if not supported  out of box (wireless is a common problem when it comes to drivers)
Well dunno if that's any help

Added: Looking at your specs there I see 4GB of RAM. Now I'm pretty sure 4GB is the max that computers can take in 32-bit. I just thought I saw somewhere that 3.5 GB is the max. You better check that out, or maybe I'm just imagining things here :confused:

---

### Post by HackCoders on 2007-10-11
32bit OS's only read 3.5GB of RAM, you will need 64bit to use all 4GB...

---

### Post by Paqman on 2007-10-11
> **P4rD0nM3 said:**
> 
1. Should I go 64 bit? Why?

Why not? It'll be faster, and the chip was always designed to run 64-bit. Besides, it's the way of the future, and Linux is leading the way with support for 64-bit computing.

Gutsy will support Flash for 64-bit Firefox, something that was a problem previously. Otherwise almost all packages are available for 64-bit.

---

### Post by crjackson on 2007-10-11
> **P4rD0nM3 said:**
> Hey guys, I posted awhile ago about switching my old HP desktop to Ubuntu and it was a great success. That computer used to have XP installed. I did a clean install of Ubuntu 7.04 and man it sure made that old hp desktop faster especially without those bundled programs from HP. My old video card (GeForce FX 5500) died 2 years ago and I haven't even called BFG to replace it (Lifetime Warranty), however with Ubuntu, I somehow feel that I need it JUST BECAUSE. Hehehe. It's going to be shipped back later this month.

The Ubuntu community has been very helpful unlike other linux communities that I've been to, where they want to filter out the newbies. This community is sending the right message about Linux and I appreciate it.

So now, I'm ready to convert another desktop that I have to Ubuntu 7.04. Here's the specs for the desktop:

AMD 64 X2 4200+
4 GB DDR2
640 MB 8800 GTS

My questions are:

1. Should I go 64 bit? Why?
2. I have a NVIDIA 8 series video card, will this have any sort of problem with Ubuntu?
3. Right now, I have a 250GB HDD, I'm planning on purchasing another 250GB so I can do a Raid0. Does this have any effect on Ubuntu?
4. This will connect to the internet through a wireless router.

Keep in mind I'm a noob and have only installed about 90 times.  My answers are my opinion and YMMV.

1. Yes.  Because you have a 64-bit system and 64-bit U runs great.
2. I see no problem once you get your preferred drives installed (64-bit no harder or easier than 32-bit)
3. It should work just fine if properly setup.  I personally don't like Raid0 and don't use it.  I see no OS related problems that would be specific to 64-bit
4. I have 4 wireless systems in the house.  It can be a bear to setup if you have a poorly supported card.

---

### Post by P4rD0nM3 on 2007-10-11
My card is a D-Link Wireless card. I'm going to search for it in google.

---

### Post by HackCoders on 2007-10-11
Search your card model here, that's how I found how to set mine up.

---

