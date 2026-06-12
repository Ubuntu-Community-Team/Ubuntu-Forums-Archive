---
title: "Running Ubuntu 10.04 thru Virtualization (3D)"
date: 2010-07-23
forum: Apple Hardware Users
---

### Post by maciej234 on 2010-07-23
Hi, I haven't found a solution so I wanted to ask here.  I've tried virtualbox, vmware fusion and parallels 5, but I cannot run Visual Effects on my Mac running Ubuntu 10.04.  Is it only a matter of time before some software will support visual effects in Virtualziation mode on my Mac?  For example, I'm haven't been able to install parallel tools 5 on my mac to support the visual effects.

On the side, does windows virtualbox software support visual effects running the Ubuntu 10.04 guest?

---

### Post by conundrumx on 2010-07-23
To my knowledge no virtualization software currently supports OpenGL on Linux.

---

### Post by Macskeeball on 2010-07-24
What Mac do you have? 

Visual Effects work for me in VirtualBox on my Late 2009 MacBook Pro when I install the Guest Additions.
[list=1]
[*]Verify that your version of VirtualBox supports your version of Ubuntu by checking the [VirtualBox ChangeLog](http://www.virtualbox.org/wiki/Changelog). 10.04 is supported in the latest version, but this is something you have to keep in mind with future Ubuntu updates.
[*]With the Ubuntu VM off, go into the VirtualBox settings for that VM. Under System, give it at least 512MB. Personally I give it 1GB of my 4GB. Under Display > Video, give it at least 64MB of VRAM and check the box for 3D Acceleration.
[*]To see what kernel version you have in Ubuntu, type the following in its Terminal: uname -r
[*]In the Ubuntu Software Center under Applications, install the build-essential package and the version of linux-headers that matches your kernel version.
[*]In the VirtualBox menubar for your Ubuntu VM, choose Devices > Install Guest Additions. This will make a virtual disk (the Guest Additions ISO) available to Ubuntu.
[*]In Ubuntu, choose Guest Additions from the Places menu. This will mount it on the desktop.
[*]Open the disk and click "Open Autorun prompt." A Terminal window will open and automatically compile and install the VirtualBox Guest Additions.
[*]If you get errors, try Googling the error messages or posting them here. If you don't get errors, restart the Ubuntu VM and turn on Visual Effects.
[/list]

I was mostly going from memory, so it might also help to read what the VirtualBox manual has to say about Guest Additions. To access the manual, choose "Contents" from the VirtualBox Help menu.

---

### Post by maciej234 on 2010-07-24
I will try this soon, hopefully it will work

---

### Post by Macskeeball on 2010-07-24
If it doesn't, don't forget to tell us what Mac you're using.

[list=1]
[*]From the Apple menu, choose "About this Mac" and then click "More info"  to launch System Profiler.
[*]In the sidebar on the left, click on "Hardware" so that on the right it shows your "Hardware overview."
[*]Tell us what it says for "model identifier." For example, mine says "MacBookPro5,4."
[*]In the sidebar on the left, choose "Graphics/Displays" under hardware.
[*]Tell us what it says for chipset model. This will tell us what graphics card you have. For example, mine says "NVIDIA GeForce 9400M."[/list]

Of course, you only need to do the above if you have problems. If it works, let us know that too. I hope all this helps.

---

### Post by maciej234 on 2010-07-24
thanks this worked. Is there a way to fix the scrolling in Ubuntu in Virtualbox? The scrolling seems very stiff and jagged when compared to VMware fusion.  Is this graphics related, can I tweak the graphics to perform smoother?

---

### Post by Macskeeball on 2010-07-24
I have no idea. As a guess, perhaps you should try temporarily increasing the amount of RAM and/or VRAM that you're allocating to the Ubuntu VM to see if it makes a difference. Or if enabling Visual Effects made scrolling worse, try more moderate visual effects.

If no one else ends up being able to help you in this thread, I can at least point you to a couple of other places that may be able to help. First is the [Virtualization forum](http://ubuntuforums.org/forumdisplay.php?f=308) here on the Ubuntu forums, and the other is the official [VirtualBox forums](http://forums.virtualbox.org/).

---

### Post by macewan on 2010-07-27
Do you have a similar tutorial for VMWare Fusion?

> **Macskeeball said:**
> What Mac do you have? 

Visual Effects work for me in VirtualBox on my Late 2009 MacBook Pro when I install the Guest Additions.
[LIST=1]
[*]Verify that your version of VirtualBox supports your version of Ubuntu by checking the [VirtualBox ChangeLog]("http://www.virtualbox.org/wiki/Changelog"). 10.04 is supported in the latest version, but this is something you have to keep in mind with future Ubuntu updates.
[*]With the Ubuntu VM off, go into the VirtualBox settings for that VM. Under System, give it at least 512MB. Personally I give it 1GB of my 4GB. Under Display > Video, give it at least 64MB of VRAM and check the box for 3D Acceleration.
[*]To see what kernel version you have in Ubuntu, type the following in its Terminal: uname -r
[*]In the Ubuntu Software Center under Applications, install the build-essential package and the version of linux-headers that matches your kernel version.
[*]In the VirtualBox menubar for your Ubuntu VM, choose Devices > Install Guest Additions. This will make a virtual disk (the Guest Additions ISO) available to Ubuntu.
[*]In Ubuntu, choose Guest Additions from the Places menu. This will mount it on the desktop.
[*]Open the disk and click "Open Autorun prompt." A Terminal window will open and automatically compile and install the VirtualBox Guest Additions.
[*]If you get errors, try Googling the error messages or posting them here. If you don't get errors, restart the Ubuntu VM and turn on Visual Effects.
[/LIST]

I was mostly going from memory, so it might also help to read what the VirtualBox manual has to say about Guest Additions. To access the manual, choose "Contents" from the VirtualBox Help menu.

---

### Post by maciej234 on 2010-07-27
As far as I know, I could not enable 3D in VMware fusion because open GL is not supported

---

### Post by Macskeeball on 2010-07-27
> **macewan said:**
> Do you have a similar tutorial for VMWare Fusion?

No, VirtualBox is the only virtual machine software I've used up to this point.

---

### Post by macewan on 2010-07-29
I'll try to duplicate under VMWare & Parallels (latest) & post the results.

may take a few days. Need to spend time making money first ;-) 


> **Macskeeball said:**
> No, VirtualBox is the only virtual machine software I've used up to this point.

---

### Post by tchoklat on 2010-09-16
> **macewan said:**
> I'll try to duplicate under VMWare & Parallels (latest) & post the results.

may take a few days. Need to spend time making money first ;-)

I am running Parallels 6 with Ubuntu 10.4 on my iMac with the latest updates. I have build-essentials and headers installed and also Parallels tools installed. I am unable to turn on 3D or any visual effects thru System>Preferences>Appearance>Visual Effects.

Any thoughts? Do I need Compiz to do this?

tchoklat

---

### Post by macewan on 2010-10-11
> **tchoklat said:**
> I am running Parallels 6 with Ubuntu 10.4 on my iMac with the latest updates. I have build-essentials and headers installed and also Parallels tools installed. I am unable to turn on 3D or any visual effects thru System>Preferences>Appearance>Visual Effects.

Any thoughts? Do I need Compiz to do this?

tchoklat

Compiz has not helped me.

---

