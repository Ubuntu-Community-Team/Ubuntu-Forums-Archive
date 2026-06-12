---
title: "Advice before installing?"
date: 2011-09-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by MontrealDude on 2011-09-01
So I decided to go out and buy a brand new system.

I bought the parts and have now put it all together into what I hope will be a pretty good machine for the next 2 years.

I have a couple ASUS parts, and would appreciate any advice you guys might have... more specifically, has anyone encountered problems with any of the following parts:

MoBo : Asus M5A97
V-Card : Asus EAH6450 

I'll also be using an AMD X2 560 Phenom II (black edition), 500gig WesternDigital HD, Kingston RAM (2x 2gig DDR3) and an LG DVD-R.

I'll be using the 64 bit version of Ubuntu 11.04 so if anyone has come across issues with these parts... please let me know before I take the plunge please!

Thanks guys!

---

### Post by MontrealDude on 2011-09-05
Seriously? Nobody at all... ?

---

### Post by gordintoronto on 2011-09-05
I've been using 64-bit Ubuntu on a Phenom II X2 for two years now, with good results. However, I have a Gigabyte motherboard and Nvidia video card, so I can't comment on your motherboard or video card.

Sometimes the very newest motherboards have an Ethernet adapter which is not yet supported.

---

### Post by SirDrexl on 2011-09-06
The video card is based on the Radeon 6450, if that helps anyone else.

Will you be using a CD to install, or a USB flash drive?  If you go the USB flash route, bear in mind that many motherboards will treat USB flash as a hard drive.  When installing Ubuntu, GRUB by default will install to the first hard drive (sda), and a problem can arise since, at least in my experience, the USB drive gets assigned as sda while the actual hard drive is sdb.  You have to remember to tell GRUB to install to sdb instead of accepting the default.

---

### Post by MontrealDude on 2011-09-07
Yes the V-Card is a Radeon 6450 by ASUS.

I'll be installing to the hard drive from a CD, but thanks for thinking ahead of the game and mentioning the possibilities.

I'd love to hear if anyone has had any issues with the hardware itself though... I know drivers are always a problem with Linux since most companies dont include any in the software provided with the hardware.

I'll be setting up my machine probably next week, so don't be shy folks... if you have had problems, or have installed these parts with no problems, let me know!

Thanks

---

### Post by Johnny3 on 2011-09-29
> **MontrealDude said:**
> So I decided to go out and buy a brand new system.

I bought the parts and have now put it all together into what I hope will be a pretty good machine for the next 2 years.

I have a couple ASUS parts, and would appreciate any advice you guys might have... more specifically, has anyone encountered problems with any of the following parts:

MoBo : Asus M5A97
V-Card : Asus EAH6450 

I'll also be using an AMD X2 560 Phenom II (black edition), 500gig WesternDigital HD, Kingston RAM (2x 2gig DDR3) and an LG DVD-R.

I'll be using the 64 bit version of Ubuntu 11.04 so if anyone has come across issues with these parts... please let me know before I take the plunge please!

Thanks guys!

Have you put this together? How did MB and V card Work.
Thanks and God Bless Johnny3

---

### Post by MontrealDude on 2011-10-01
OK...

So, I tried installing Ubuntu 11.04 64bit... from a CD

The purple page with the white keyboard looking thing with a stick figure man at the bottom appeared... and I thought YES here we go...

Unfortunately the screen then went all haywire... green and red lines up and down the screen... yet the CD was spinning... 

Eventually the screen went black with a flashing white underscore ... like a command prompt... I tried typing but nothing was coming up on the screen. 

I thought maybe my CD of the 64 bit Ubuntu was corrupted, so I tried my 32 bit CD which I used to install on this machine which I'm writing from now... same results.

Any advice on what might be happening would be greatly appreciated!

Thanks

---

### Post by Johnny3 on 2011-10-01
With it run mem test? I known you puled all memory and video card and reseated them. Try 1 stick of memory pull battery and jumper BIOS reset. Do you have another video card? Do you have the latest BIOS? It has been a while but on one Asus MB I think I had to lower the I think PCI slot in the BIOS?
Good Luck and God Bless Johnny3
[http://vip.asus.com/forum/topic.aspx?board_id=1&SLanguage=en-us](http://vip.asus.com/forum/topic.aspx?board_id=1&SLanguage=en-us)

This looks Good [http://openbenchmarking.org/s/ASUS%20M5A97%20EVO](http://openbenchmarking.org/s/ASUS%20M5A97%20EVO)

---

### Post by Johnny3 on 2011-10-01
From looking at newegg the M5A97 EVO PCI-express  is 2.0x16. The video card EAH6450 is 2.1x16 don't think it will work. Most MB will go down but not up in PCI express. I think. I would return that video card and get this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121422](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121422)
about same price.  But I am no expert ether.(spelling too)
Good Luck and God Bless Johnny3 65++

I have the 555 amd black and want a new MB and video card. So you need to get it working in Ubuntu 11.04 pronto.

---

### Post by MontrealDude on 2011-10-02
arrrrrg...

Jonny you clever son of a gun, you totally hit the nail on the head with that one...

How could I be so dumb? I didn't even think to check the PCIE slots for compatibility... I just hope the store will let me exchange it, since it's been more than 15 days ](*,)

The only thing I'm unsure about is how come it worked fine up until the actual install...

I did a MemTest fine, the UEFI interface with the fancy OS like graphics and all worked... I guess the compatibility issues only come up when the card starts using more of its capabilities?

#-o

Thanks Jonny... I'll let you know what happens.

---

### Post by Johnny3 on 2011-10-02
I am not shore about that. NVIDIA video card seem to work better in Linux for me that AMD or ATI. The video  card might just be to new to have any Linux driver's out yet. But from the things I have read the MB should work.( I think). If store want let you exchange I would call Asus could be a bad card. Maybe try 10.04 LTS?
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/](http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/)
Good Luck and God Bless Johnny3 65+++

PS good Luck. Nice to have 2 PC someone is working. I have no one to talk to. So I long as I can get on the inter net I can usual get thinks fixed.(usual the key word)

---

### Post by MontrealDude on 2011-12-08
quick update...

I eventually gave up and installed windoze 7 ... sigh

Lately I've been yearning to go back to Linux so i did quite a bit of research.

My research has led me to this answer... nomodeset!

Using nomodeset "should" fix the video display issues i was having when trying to install previously. According to what I've read, this is a common problem with an easy fix. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded.

You can find the article [here]("http://ubuntuforums.org/showpost.php?p=10069997&postcount=1") -- enjoy!

---

