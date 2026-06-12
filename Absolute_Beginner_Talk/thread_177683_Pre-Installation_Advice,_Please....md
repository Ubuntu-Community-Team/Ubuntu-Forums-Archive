---
title: "Pre-Installation Advice, Please..."
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by cubdukat on 2006-05-16
I am getting ready to try Ubuntu again (I attempted to install it previously, but it wouldn't boot up), and I had a few questions before I do:

1. The last time I attempted to install it, I did it as a dual-boot (I mainly use XP Home SP2). Ubuntu is going on a partition on the same SATA drive that has XP. The install appeared to have gone well, but when I went to boot it up, GRUB appeared to ignore it. 

I have also heard that Debian (and by default, Ubuntu) is not meant to be a dual-boot OS, and that it likes (or requires) itself to be the only OS on the system. I find that hard to believe, so if anyone could tell me how to set this up so that I can dual-boot successfully, I would be most appreciative.

2. The second problem is something that I seem to have noticed with all the distros I have tried to date (and I've done all except Simply MEPIS, Slackware and Gentoo). I have a GeForce 6600GT AGP installed in my computer, and the screen is legible during the install and setup, but once the system actually boots up, the screen is completely illegible. I can't even use the Ubuntu Live CD because of this. If I boot into the safe mode, what do I do from there to get my screen working correctly?

Any assistance would be greatly appreciated.

---

### Post by joshbax on 2006-05-16
I am a complete n00b and about to post my question... But I am sure you are not meant to install more that one OS in the same partition. Is that what you did? As that may have been a problem. But it's a just a guess.

---

### Post by Jagot on 2006-05-16
With regards to your first question both Debian and Ubuntu can quite happily dual boot with Windows or indeed another distro on the same drive but in separate partitions.  You can learn about dual booting with Windows at this site, which pretty much gives you a step-by-step guide:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

With regards to the second question, you probably need to install the proper Nvidia drivers though I'm not 100% sure as I've never had to deal with this.  You can do it through Synaptic:

[http://packages.ubuntu.com/breezy/x11/nvidia-glx](http://packages.ubuntu.com/breezy/x11/nvidia-glx)

---

### Post by confused57 on 2006-05-16
When you boot up, you can try  Ctrl+Alt+F1, which should get you to a text command line, then enter:

sudo dpkg-reconfigure xserver-xorg

press "enter"

Select "vesa" as the graphics driver(or "Nv", if vesa doesn't work)

Select the resolutions for your monitor, no higher than your native resolution.

Entering "startx"(without quotes) at the command prompt should start Gnome.
Press "enter"  (or you can try Ctrl+Alt+F7)

May work, no guarantees...

---

### Post by cubdukat on 2006-05-16
Thanx. 

Hopefully Ubuntu can read NTFS partitions so that I can get the nVidia drivers off of my XP partition instead of fiddling around with my USB card reader.

With any luck, this will be the distro I finally settle down with. So far, the only two I've really been impressed with are FC5 and Suse 10 OSS. Sadly, not even these two have been able to get me online with my external modem. But that's another story...

---

### Post by cubdukat on 2006-05-17
Well, I attempted the installation last night, but it didn't work. It said something about initrd being unable to install, then it aborted. I checked the CD I was using and there was nothing wrong with it, so I tried it twice more, both times without success.

I ended up reinstalling Suse 10 OSS, but I'll probably try it again.

---

### Post by Sef on 2006-05-17
> Well, I attempted the installation last night, but it didn't work. It said something about initrd being unable to install, then it aborted. I checked the CD I was using and there was nothing wrong with it, so I tried it twice more, both times without success.

Did you md5sum the download?

---

### Post by cubdukat on 2006-05-18
It wasn't a download. I got the CD from SendIt.com.

It did a complete, if unsuccessful, install the last time I used it, and it's been in the sleeve ever since then, so who knows why it didn't work. I'll probably try it again soon.

I checked the CD and I didn't see any scratches on either side. It was probably just my computer acting contrary or something.

---

