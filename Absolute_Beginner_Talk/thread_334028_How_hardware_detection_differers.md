---
title: "How hardware detection differers?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by TusharG on 2007-01-08
How each Linux distro is different when it comes to hardware detection? Isn't all are using the same kernel and same source for packaging? 
 For example: Lot of editors say PCLinuxOS has amazing hardware detection. I'm wondering how PCLinuxOS and Ubuntu hardware detection will differ? Both are debian based distros and both are using the same sources for packing. 
   I do understand the distro difference based on packging ex: rpm based, deb based. 

Can anyone tell how hardware detection differers from distro to distro?

---

### Post by az on 2007-01-08
It depends.

Traditionally, a lot of the configuration that you would need to run a desktop is done during the install.  There is not one single linux installer, but each distro pretty much has made their own.  More and more, a lot of these things are being off-loaded to the individual software projects - for example, Edgy started using unit-IDs for fstab - that way, when you change the order of your hard disks, they will still be mounted in the right spot.

The Xorg packages configure themselves when you install them.  A few years ago, the installer would probe your hardware and configure X.

Also, a lot of different distros handle things differently; for example, where to put things in the filesystem, how to name them, etc....

I suspect, though, that in a few years, the components will be sufficiently well seperated (like Udev and HAL, where you don't have to worry about your hardware, it's abstracted for you) that the upstream applications will just rely on the compenents being there and the stuff being handled properly.

Said differently, a lot of software does both low-level and high-level configuration.  When that is properly seperated, it will be easier for everything to be uniform.

---

### Post by TusharG on 2007-01-09
Thanks a lot for your reply. What I still wonder when lot of companies claim a better hardware detection and when magazine editors, bloggers support that!
 For example video drivers for ATI & Nvidia will remain same and detection should remain same for same numbered kernel? How Fedora will differ in hardware detection from SUSE or from PCLinuxOS or Ubuntu?
 PCLinux and Ubuntu are derived from debian so in that case wouldn't then will have same hardware detection capability for same kernel level?

---

### Post by az on 2007-01-09
> **TusharG said:**
>  PCLinux and Ubuntu are derived from debian so in that case wouldn't then will have same hardware detection capability for same kernel level?

Well, for example, Xandros, Linspire and Mepis are all Debian-based and they all have different installers.

It's not just about the kernel.  And often different distros use different versions of the kernel or use different patches.  When you are basing something off Debian Unstable, the kernel changes quite often - the kernel the distro is released with depends on when they decided to take the packages and work with them.

---

### Post by TusharG on 2007-01-09
Thanks a lot for clearing my doubt. 
 So these guys put extra effort to make the distro work better and even through debian, Ubuntu, PCLinuxOS have same origin they differ from kernel number and efforts of developers. 


Thanks again.

---

### Post by Bachstelze on 2007-01-09
Exactly, and the kernel is not 100% the same, either. Most distros - actually, all of them but Slackware - do not une a "vanilla" kernel - i.e. a Linux kernel exactly as it was released by Torvalds and Co. on [http://www.kernel.org](http://www.kernel.org) - but do some work on the code, for example to add and/or remove modules, thus modifying the list of hardware it can detect.

For example, my ipw3945 WiFi card was detected out of the box in Ubuntu because the Ubuntu developpers added the driver for it in their kernel, while others didn't and on my Debian, I had to manually compile and install it.

---

