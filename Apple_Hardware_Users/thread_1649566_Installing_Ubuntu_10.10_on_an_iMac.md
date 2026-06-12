---
title: "Installing Ubuntu 10.10 on an iMac"
date: 2010-12-20
forum: Apple Hardware Users
---

### Post by MadHatter21 on 2010-12-20
Hello Everyone,

Ive been at this for quite some time now and I cannot figure it out. I am trying to install just the basic Ubuntu Desktop 10.10 32bit on my iMac, AND DUAL BOOT IT WITH MAC OSX, and I am having a world of trouble. I have been trying every post on this and Google search I could find and I still cannot find success.

I have a iMac running a ATI Radeon HD 4670

My basic problem is that the graphics driver for my specific iMac, the ATI Catalyst driver, is not supported with the new versions of Ubuntu. To give you a basic synapsis of what I have tried is:

1st, I downloaded the 10.10 32bit and burnt it to a cd. 2nd, I re sized my partition scheme to get a sizable amount of space for the new OS. 3rd, I installed rEFIt on the Mac side of the operations. After doing this I rebooted, held down the char 'C' key and booted into the CD. It began to run the cd, and the screen went black, then a small icon came up at the bottom of the screen which looked like a little man in a circle with a battery next to it. I didnt know what it ment, but I just kept waiting. Then the screen displayed a flashing '_' at the top of the screen and went black.

After researching around a little I have determined that it was my graphics that were having all of the trouble. So I decided to install a old version of Ubuntu, 9.04 to be exact, and install the correct proprietary graphics driver for the HD radeon and then upgrade until I hit 10.10. I got all the way to 10.04 but then my graphics went out. AGAIN. I tried a few things but not much worked. So I gave up on the upgrading until current plan.

Then I switched back over to mac, undid EVERYTHING I had done, including uninstalling rEFIt and changing the partitions back. I then downloaded the Alternative Text Based Installed for Ubuntu 10.10 and figured I might give it a go. I then re sized the partitions, but this time did not install rEFIt thinking it would not be necessary. I booted the CD again this time making it all the way into the installer, but then getting stuck with grub. The system installed, and everything was running smooth until grub came into play. I am just beginning to learn with Ubuntu so it might be a rookie mistake but I cant figure it out. It asked me where I wanted to install GRUB. I had a few options and chose the second partition on my HD, thinking it was the Ubuntu partition. It finally ended and I rebooted the system getting ready to install the graphics driver and then the gui, but it booted up and went to GRUB. Now being inexperienced with it, I tried to figure my way through the grub shell, but I couldn't figure it out. I believe it wanted me to point it towards the OS but I really dont know what to do anymore. It seems like I have tried all of my options. 

Any help is appreciated and if there is some post/tutorial/wiki that anyone knows about that I might have missed, Id be very grateful for it.

Thank you very much,
MadHatter21

---

### Post by monkeymagico on 2010-12-20
I have been running Ubuntu on my iMac for a few months now, I tried a few of the methods online here and elsewhere but the results were not satisfactory.

I now happily use Parallels Desktop 6, A straight forward, simple set-up which allows me to safely install Ubuntu any flavor(and other Linux Distros) with full compositing and no hardware or software performance issues of any kind.

---

### Post by arabis on 2010-12-20
It seems you have installed grub on your MAC OS partition. Can you still boot in MacOsx?

---

