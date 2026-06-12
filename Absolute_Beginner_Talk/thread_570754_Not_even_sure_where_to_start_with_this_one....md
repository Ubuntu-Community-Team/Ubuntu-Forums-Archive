---
title: "Not even sure where to start with this one..."
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2007-10-08
As the title implies, this problem has quite a bit of history so to anyone who attempts to read this in it's entirety and assist; thanks ahead of time!  I'm trying to provide all the details to aid those who may choose to assist.

Here is the set up:

I have a computer with an AMD64 3400+ in it, I also have 2 hard drives, one is a 200 gig(NTFS) and the other is a 40 gig(NTFS/EXT3) and an ATI 1600 series graphics card.  For the sake of keeping the word count down, let's call the 200 gig HD1 and the 40 gig HD2.

After getting HD1 close to full (well closer than I prefer) I decided to export a chunk of my data to HD2.  Before I could do this, HD2 was an entire Linux Drive which housed various distros and my boot loader (GRUB).

Without thinking "hey that's my boot loader," I formatted HD2 and blew up my boot loader.  Clearly this would be a problem so I had to fix it.  Using an Ubuntu LiveCD, I reinstalled Ubuntu on 7 gigs of HD2 for boot loading and also for my own experimentation with Linux.  The remainder of the drive was formatted for NTFS to house a lot of the data from HD1 such as MP3s, videos, pictures, etc.

Awhile ago I decided to return from my Linux vacation and get back into learning the OS.  The first problem I had to tackle was getting the ATI drivers installed and set up correctly so I could utilize the 1440x900 resolution of my monitor.  Installing from the repo didn't do the trick so I attempted to edit xorg.conf for the Hsync and Vsync values.  I wish I could provide a more detailed explanation of what happened but the short version is that Ubuntu was not happy with whatever it was I did.  After re-starting, X would not load.  The screen would flash from the prompt to blackness on roughly 4 second intervals.  After this went on for maybe 20 seconds, I would get a blue screen saying that X could not be loaded.  After issuing start X, the system apparently wasn't lying.

Being that it's not terribly hard to start over with a distro I decided that I had simply made a foolish mistake and would start from scratch with the same LiveCD.  Upon putting the LiveCD in, it wouldn't load.  I could select the option to install it but the loading bar simply remained animated, never actually loading.

What's even more confusing is that this is not unique to Ubuntu but rather almost any Linux distro I try.  To elaborate...

Sabayon will not load X (off of the LiveCD, as I recall, i get an "out of range" error)
Knoppix will start the LiveCD, install but only boot once.  Apparently, even if I don't make any changes, Knoppix will not boot after the initial install.  Knoppix is still on my system though I cannot use it, it simply servers as my boot loader.
Ubuntu will not load X (Off the LiveCD, stuck at loading stage and this only began after I screwed up X the first time)
Gentoo will not load X (off of the LiveCD)

I would very much like to get back to Ubuntu but as you can see, there are some odd obstacles for me to overcome first.  While I am not 100% new my Linux experience is limited.  For a problem like this, I have no idea where to start looking.  

Thanks in advance for your help and assistance.

P.S.  I will be restarting my OS and trying to boot my Linux distro so that I may provide a more detailed error message shortly.

---

### Post by tisepti on 2007-10-08
You might try using the alternate install disks. A guide may be found at [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/). 

As for ATI drivers you may want to try envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) I have no clue how the ATI drivers are; it worked for my nVidia 8400M GS and it claims to be able to support ATI as well. Use at your own risk.

---

### Post by The Tronyx on 2007-10-08
> **tisepti said:**
> You might try using the alternate install disks. A guide may be found at [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/). 

As for ATI drivers you may want to try envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) I have no clue how the ATI drivers are; it worked for my nVidia 8400M GS and it claims to be able to support ATI as well. Use at your own risk.

Thanks for the links.  I've been looking over the blogspot link quite a bit but I cannot figure out why this suddenly became an issue.  This is the first time I have had any problem with a LiveCD.  I'll keep searching, thanks for a nudge in the right direction.:)

EDIT:  With booting knoppix there is no X error message.  The boot goes as planned except towards the end

ide: failed opcode was: unknown
hdb: dma_timer_expiry: dma status ==0x60
hdb: DMA timeout retry
hdb: timeout waiting for DMA

And then it's completely unresponsive.  This happens after one successful boot post-installation. :?

EDIT:  I think I found the source of the problem with Ubuntu 7.04 and it relating to my video card.

---

