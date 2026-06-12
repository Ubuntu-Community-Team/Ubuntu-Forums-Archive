---
title: "Can I make a live OSX USB while in  Ubuntu?"
date: 2011-07-22
forum: Apple Hardware Users
---

### Post by ilazria on 2011-07-22
I've found many sites showing how to make an OSX live USB or External HD via Mac's Disk Utility. However, because of my recent troubles, my Mac Pro doesn't have a working OSX, and I can't access disk utility with my Snow Leopard install disk. I'm using a flashed PC graphics card, which leaves me with no picture until the login screens appear.

Is there any way to create a live cd/usb or external hard drive of Snow Leopard while in Ubuntu?

---

### Post by 2F4U on 2011-07-23
You probably know that you violate Apples licence terms if you do that. You are allowed to use Mac OSX only on Apple hardware.

---

### Post by jocko on 2011-07-23
> **2F4U said:**
> You probably know that you violate Apples licence terms if you do that. You are allowed to use Mac OSX only on Apple hardware.
And a Mac Pro isn't Apple hardware?

---

### Post by ilazria on 2011-07-23
> **2F4U said:**
> You probably know that you violate Apples licence terms if you do that. You are allowed to use Mac OSX only on Apple hardware.

How is installing OSX on an external HD any different than installing on an internal HD? I'm just needing to be able to install it from an operating system other than OSX. As Mac doesn't prohibit having multiple OSs installed, I don't see how there is any conflict with using a different OS to perform the install, if the alternate OS has the capability. Plus, you are allowed to use Disk Utility to restore OSX to a formatted HD.

I don't see the same function in Ubuntu's Disk Utility, so I'm wondering if I've overlooked something, or there is some package or software I need to install.

---

### Post by scorp123 on 2011-07-25
> **ilazria said:**
>  and I can't access disk utility with my Snow Leopard install disk.  How come? It's right there on the installation DVD in the "Tools" menu.

Other than that you don't really have a lot of working options. Here on Ubuntu there are tools and scripts such as "dmg2iso" (can be found via Google) and "dmg2img" (can be found in the "apt" repositories) that can convert Apple's *.dmg disk images into formats such as *.iso so you then can use Linux programs such as "k3b" (KDE) or "brasero" (GNOME) to burn that image onto a DVD-R disk ... But those conversions won't work with every *.dmg file. 

So your best option would still be to get yourself a working version of Mac OS X 10.6 "Snow Leopard" (e.g. from your local Apple store) and then use Apple's own "Disk Utility" to do this.

The problem here is that *.dmg disk images and Mac's "HFS+" filesystem are not common outside the Mac world, so usually you will need Apple's own tools to correctly handle those disk image formats.

---

### Post by ilazria on 2011-07-25
> **scorp123 said:**
> How come? It's right there on the installation DVD in the "Tools" menu.

Other than that you don't really have a lot of working options. Here on Ubuntu there are tools and scripts such as "dmg2iso" (can be found via Google) and "dmg2img" (can be found in the "apt" repositories) that can convert Apple's *.dmg disk images into formats such as *.iso so you then can use Linux programs such as "k3b" (KDE) or "brasero" (GNOME) to burn that image onto a DVD-R disk ... But those conversions won't work with every *.dmg file. 

So your best option would still be to get yourself a working version of Mac OS X 10.6 "Snow Leopard" (e.g. from your local Apple store) and then use Apple's own "Disk Utility" to do this.

The problem here is that *.dmg disk images and Mac's "HFS+" filesystem are not common outside the Mac world, so usually you will need Apple's own tools to correctly handle those disk image formats.

SOrry, I forgot to mention that I am using a flashed PC graphics card in this Mac. As far as I know, there are no methods for getting a flashed PC graphics card to show any picture until the desktop is loaded. This also affects visibility when running the Snow Leopard install disk. There is no picture, so I can't see anything to run the install.

SO, right now I have a working Snow Leopard install disk, but no way to use it. I want to put Snow Leopard on an exrernal hard drive or USB so I can see if there are any recoverable files on the internal hard drive I originally installed OSX on. At first, I had been able to access that hard drive and copy some files from Ubuntu. The OSX hard drive seemed completely normal, I just couldn't boot to it. After I shutdown for the night and restarted the next day, Ubuntu's disk utility shows that drive as completely blank, no partitons, no format, nothing. I figure it probably means that the drive got wiped somehow, and it won't matter what I use to access it, but before I take the plunge and reformat the drive, I want to check, just to be sure. 

If I can do an install while in Ubuntu, it will save me the hassle and headache of packing up the kids and driving to my parents' house to use one of their macs.

---

### Post by scorp123 on 2011-07-25
> **ilazria said:**
>  If I can do an install while in Ubuntu ... I don't really think so. 

What comes to my mind: If you keep pressing the 'T' key while a Mac is powering on it should be set into "Target mode", e.g. you get a big Firewire icon on your screen ...

The procedure is explained in detail here:
[http://www.applelife.co.uk/2008/01/how-to-safely-use-macs-firewire-target-mode/](http://www.applelife.co.uk/2008/01/how-to-safely-use-macs-firewire-target-mode/)

Basically your Mac should act as if it where a Firewire harddrive. Now if you connect your troublesome Mac to a healthy Mac via a Firewire-800 cable (every Mac store should have that on sale ...), the healthy Mac will be able to manipulate the other Mac's harddrive as if it were his own disk. It should also be possible to check the filesystem for errors and then mount the broken Mac's drive.

This works pretty well. I'd recommend you try this because this has a pretty high chance of working (I fear that Linux will not be able to correctly handle your Mac disks and might therefore do more harm than good in this situation) ... ? The downside here is that you will need that Firewire-800 cable so you can link the two Macs ... Such a cable will cost you around 20$. But it's worth it.

---

### Post by 1clue on 2011-07-25
This might be a roundabout way to do this, but...

Install OS X on a VM, boot from it and then use disk utility.

IMO that's a much more workable system anyway.  Then you get simultaneous access to Linux, which is evidently your OS of choice, and Mac OS X, which evidently you need to get at every now and then.

I haven't tried VMware with an OS X guest, but evidently they have one.  I checked their site though, and the Mac OS X that you use can't be the OEM disk for your hardware.  It has to be a separately purchased product.  A VM appears to be different hardware, which is why your video driver would work this way.

---

### Post by westie457 on 2011-07-25
Hi some suggestions for you to try.

1 Boot your MAC with a LiveCD/USB and select try. Then open a terminal and run this command ```
dd if=/dev/sda of-/dev/sdc
```
I have made the assumption that sda is your internal MAC hd and sdc is the external hd. You can confirm this by firing up Gparted and checking the top-right corner for the correct disk identification.
This will give you a back-up of sorts for you to work with leaving your original drive alone.
We will be working with the external drive only for now.

2 Now you have your back-up made and still have the terminal open run ```
sudo apt-get install testdisk
```
Once it has installed, type ```
testdisk
``` and follow the prompts to check for partitions and files.
Remember at the moment you are just checking so do not write anything to this hard drive. Any partitions found on the external drive is encouraging and we can go to suggestion 3. Nothing found on the external drive means a major disaster.

3 Assuming that the test run was successful at finding partitions on the copy, now is the time to disconnect the external drive and run testdisk on the internal drive. When the partitions have been found now is the time to allow testdisk to write a MAC-compatible boot record to the internal drive and hopefully you can now reboot into your MAC properly.


Somethings to add as explanations. The external hard drive has to be the same capacity or larger than the internal drive for the 'dd' command to work. The 'dd' command will do a byte-for-byte copy of one drive to the other. All information about testdisk can be found here. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Good luck. I hope this works for you.

---

### Post by indigosunrise on 2012-10-10
I know this thread is a bit old but after days of struggling to clean install OSX on a Mac after a disk erase I have a solution!!!

If you do it this way you can directly install from a partition on the same drive or even just boot the installer from that partition to use disk utils and create a USB installer\DVD installer or external HD installer.

Firstly install ubuntu on the mac (or an external HD) and find a dmg install OS X DVD image that matches the original OS installed on that hardware when purchased. 

Make sure when you install ubuntu that you leave free unparitioned space to create a couple of partitions later.

The big issue with these images is that they actually contain multiple partitions of different filesystems so if you just convert to img and then try to mount it or convert to iso and mount it will only mount the bootcamp installer partition but I found a link which I'll post that has the work around.

You'll need to install packages dmg2img, gparted, hfsplus, hfsprogs & hfsutils.

Create an 8GB HFS+ and another bigger HFS+ partition that you plan to install OS X on (so 30gb+), as mentioned in the link below and follow those instructions carefully.

[Use Linux to install OSX from a DMG extracted to a partition - without a Mac DVD]("http://linuxforums.org.uk/index.php?topic=1072.0")

After so much struggling, this was the only way that worked, and it's pretty straight forward. Was able to do it and install OS X within half an hour or so and the install was very fast because it was on the same HD.

Best of luck guys.

---

### Post by ojdon on 2012-10-10
Heh, thanks for sharing that piece of info, always wondered how I would accomplish that in Ubuntu, you can use Transmac under Windows and just the built-in Disk Utility in OSX.

---

### Post by indigosunrise on 2012-10-10
Also just thought I'd add that I used a Leopard image and I'm running Ubuntu 12.04 now.

---

### Post by wildmanne39 on 2012-10-11
Thanks for sharing but this is an old thread so it has been closed.

---

