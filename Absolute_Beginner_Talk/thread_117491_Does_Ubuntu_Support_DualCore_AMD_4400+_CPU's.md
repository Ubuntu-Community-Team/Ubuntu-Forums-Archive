---
title: "Does Ubuntu Support DualCore AMD 4400+ CPU's"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by boardwatchr on 2006-01-15
Hi;

I have a dual boot (Window 64bit, and Windows XP) system I use for checking out OS's.  I downloaded Ubuntu's 64bit Live and 64Bit Installer ISO's and created CD's with them.  When booting with either the 64Bit Live or the 64Bit Installer CD, I receive an error from the installer that says it can't find the install files(??).  The CD images were verified and the results on the CD's were verified after burning so I know the NERO burn was good.  

Since the Live version does not write to a HD and won't work with my ASUS SLI configuration running an AMD 4400+ CPU can I assume that Ubuntu does not support dual core CPU's yet?  Has anybody gotten Ubunto to run on a Dual Core CPU chipset yet?  Please advise.

Thanks,
Chuck

---

### Post by Sutekh on 2006-01-17
No you can't assume that.  Ubuntu does support dual-core, there are many users (myself included) that use Ubuntu with dual-core CPUs.

How did you burn the Ubuntu image files?  They must be burnt as an image in Nero, not as a data disc.  This is very important.

[HowTo: Burn an ISO disc image with Nero in Windows]("http://www.ubuntuforums.org/showthread.php?t=111589&highlight=burn+nero+image") is a simple howto if you use Nero Express, similar if you use full Nero.  Close the wizard at start-up and choose 'Recorder' and then 'Burn Image', then select the ISO you downloaded.

Keep at it!

---

### Post by CompShrink on 2006-01-21
I am no expert in this area, but hope this helps:

Make sure you have the release version first off, the preview releases they make are somewhat unreliable, as would be expected of a pre-release candidate version.

My understanding is you need the 64 bit version with the SMP kernel. I know Ubuntu supports this, but I don't know if the live CDs have the SMP kernel on them, somehow I doubt it.

Try the install CD, if you can get it to work, and then use Synaptic (Under the System or Computer menu on the taskbar, depending on the version) to download the SMP kernel, and boot up with that.

If for some reason breezy doesn't work for you, even the release version, maybe try Hoary?

I hope someone more skilled can help you, the IRC channel is a great source for getting real time, useful help.

---

### Post by ozgothic777 on 2007-07-15
I don't know if this will help you guys. I had tried different programs to burn the ISO image. the best application is Nero.  I tried the recommended free software and got bad burns. So I resorted to burning the ISO onto a CD-RW .

As for system. Im running XP pro on dell e521 AMD +5000 dual core. I have all core operating systems running on a 160 gig hard drive and maintain a mirror raid of 2 X500 gig for archival and music.

Amd support is great - both processors are listed in the system >preference >hardware information.

what I choose to have is maintain my XP pro 32 bit version along with UBUNTU 64. setup went smoothly - though I had to set occupied partitions so when I installed UBUNTU 7.04 it would go after the free partition only.

(I also unplugged my raid before install!) make things easy here. I have no problems with the system as IM still learning about everything. Im impressed with the OS all together.

---

### Post by Wim Sturkenboom on 2007-07-16
I also don't know if this will be of help after one-and-a-half year

---

