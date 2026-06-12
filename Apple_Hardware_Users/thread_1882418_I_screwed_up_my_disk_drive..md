---
title: "I screwed up my disk drive."
date: 2011-11-17
forum: Apple Hardware Users
---

### Post by orfeas0 on 2011-11-17
Hello everyone.
I'm using a macbook air 11" 2gb ram 64gb ssd core i5 1,6 model (2011).
I tried to install ubuntu using a flash usb key, unsuccessfully. But the worst part is, it kinda ruined my hard drive. I can only use 50gb (out of 60gb) for mac OSX Lion, and disk utility won't see the rest. And it can't move it. So I've lost 10gb of space and can't use boot camp to install Windows (It claims there are some files that can't be moved).

I posted a thread in the macrumors forum, but I thought the ubuntu community must have something more to offer. Here is the link to the other thread, if you need some extra details. [http://forums.macrumors.com/showthread.php?p=13868834&posted=1#post13868834](http://forums.macrumors.com/showthread.php?p=13868834&posted=1#post13868834)

Thank you for your time.

---

### Post by WasMeHere on 2011-11-17
Welcome to the Ubuntu Forums orfeas0,

1. As said in the mac thread: be sure to have your important stuff backed up!

2. Run a ***live*** session from your Ubuntu CD/USB drive.
a. Do ***not*** mount anything on the SSD
b. Use ***gparted*** to view and then try to edit your partition table. I hope it will be possible to delete what you created (maybe an extended partition with some logical partition(s) inside). And then it should be possible to expand your HFS(?) partition to use that space. (Linux should be able to delete what it created, but if Windows did it, I'm not sure.)

Or if you dare/wish, make a new attempt to install Ubuntu into those 10 GB of space. If so, let us discuss what would be the most suitable version and flavour of Ubuntu!

Have fun finding out :-)
Olle

---

### Post by orfeas0 on 2011-11-17
> **Olle Wiklund said:**
> Welcome to the Ubuntu Forums orfeas0,

1. As said in the mac thread: be sure to have your important stuff backed up!

2. Run a ***live*** session from your Ubuntu CD/USB drive.
a. Do ***not*** mount anything on the SSD
b. Use ***gparted*** to view and then try to edit your partition table. I hope it will be possible to delete what you created (maybe an extended partition with some logical partition(s) inside). And then it should be possible to expand your HFS(?) partition to use that space. (Linux should be able to delete what it created, but if Windows did it, I'm not sure.)

Or if you dare/wish, make a new attempt to install Ubuntu into those 10 GB of space. If so, let us discuss what would be the most suitable version and flavour of Ubuntu!

Have fun finding out :-)
Olle

the closer I get to solving my problems, the more problems appear!
I downloaded the latest ubuntu distro and disk util/diskmounter can't open it!
[http://imageshack.us/photo/my-images/695/screenshot20111117at326.png/](http://imageshack.us/photo/my-images/695/screenshot20111117at326.png/)
It says there are no mountable file systems when trying to open the iso(or burn it on a USB).
I also converted it to a .img file following ubuntu's instructions but it can't open that either. I'll download another version from torrents hoping that will work.

Oh and also, must I make a bootable ubuntu usb drive or just copy the iso's files in the usb?

---

### Post by WasMeHere on 2011-11-17
You must make you USB drive bootable, and it is not as simple as copying the iso file. See the following link
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by orfeas0 on 2011-11-17
I downloaded it again from torrents and still the same problem...
It says no mountable file systems... Any clue about that? Should I try an older ubuntu version or??

---

### Post by WasMeHere on 2011-11-17
You must not expect the iso file to be mountable. To be sure that the download was good, check the md5sum with the one posted on the Ubuntu site! But I am almost sure that is not what is holding you back now. If you follow the instructions in the link from my previous post, you have a better chance to succeed.

---

### Post by orfeas0 on 2011-11-17
> **Olle Wiklund said:**
> You must not expect the iso file to be mountable. To be sure that the download was good, check the md5sum with the one posted on the Ubuntu site! But I am almost sure that is not what is holding you back now. If you follow the instructions in the link from my previous post, you have a better chance to succeed.

As I said, more problems keep coming up :/

I created the bootable USB, but when I boot to ubuntu and click "try to install" I get stuck in a black/purple screen. I can shut down the computer by pressing (not holding) the power button, but I can't get into ubuntu.
There's a little section in the "how to install ubuntu on macbook" article:
> MacBook Air 3,2
Please notice: While all of the info and above commands are executed properly on a MacBook Air 3,2 (that is the 2010 version 13" version of the Air) the end result will not produce a bootable USB device, at least not with the image for Ubuntu 10.10 64-bit. When booting of the USB device the following message or something similar will appear: "Missing operating system" and the process is auto-magically halted.

To get the USB device (e.g. a USB stick) to show up at all in the boot menu you also may have to reboot/turn on/off the computer a couple of times and also resync the partition tables using rEFIt. After doing this the USB should then appear as a bootable device while holding in the alt or c key when you are rebooting the computer. Notice that both the computers built in bootloader and rEFIt will identify the USB device as a Windows device, but that's not a problem and expected.

A workaround to the-usb-device-is-not-booting-problem is to:

Install rEFIt.
Create a bootable start disk using Ubuntu and a USB stick.
Create a separate partition on the Airs HD.
dd the whole USB stick to that partition.
Resync with rEFIt. Turn power off and on.
Select Pingo/Windows logo: Install should start. (Here you might want to press F6 to change parameters, e.g. use nomodeset)
But that's related to the 2010 version of the macbook air, while I have the 2011, so I guess that's not the problem.
Plus I actually CAN boot from the usb, it's just that I can't get in ubuntu. I do see the "install ubuntu or try ubuntu" screen. But nothing after that.

---

### Post by WasMeHere on 2011-11-17
> **orfeas0 said:**
> ...
But that's related to the 2010 version of the macbook air, while I have the 2011, so I guess that's not the problem.
Plus I actually CAN boot from the usb, it's just that I can't get in ubuntu. I do see the "install ubuntu or try ubuntu" screen. But nothing after that.

Well I think you have your USB system running at its first level. Press the F6 key (if there is one) to get a sub-menu to select different boot options before continuing! I suggest that you test the system live for quite a while before trying to install to your hard drive.

If you are not happy with Ubuntu 11.10, try **11.04** or **10.04 LTS** (long time support) or the corresponding Linux Mint versions 11 or 9 (based on Ubuntu)! Sometimes it takes some trial and error to find software that co-operates well with your hardware.

---

### Post by orfeas0 on 2011-11-17
> **Olle Wiklund said:**
> Well I think you have your USB system running at its first level. Press the F6 key (if there is one) to get a sub-menu to select different boot options before continuing! I suggest that you test the system live for quite a while before trying to install to your hard drive.

If you are not happy with Ubuntu 11.10, try **11.04** or **10.04 LTS** (long time support) or the corresponding Linux Mint versions 11 or 9 (based on Ubuntu)! Sometimes it takes some trial and error to find software that co-operates well with your hardware.

I will try the other versions too, thanks.
About testing the system live: Doesn't work. But I got it to install, although when it asked to reboot, it wouldn't shut down. It asked me to remove installation media and press enter, I did it, nothing happened. I have to force shut down. Then I booted up again while pressing alt, but no ubuntu installation was shown, just the mac one.

This is too vague , though. Can I ask 1 specific question? Is there a way to completely wipe my drive so I can reinstall OSX Lion properly again? Or will this ruin my drive, making it unbootable?

---

### Post by WasMeHere on 2011-11-17
> **orfeas0 said:**
> I will try the other versions too, thanks.
About testing the system live: Doesn't work. But I got it to install, although when it asked to reboot, it wouldn't shut down. It asked me to remove installation media and press enter, I did it, nothing happened. I have to force shut down. Then I booted up again while pressing alt, but no ubuntu installation was shown, just the mac one.

This is too vague , though. Can I ask 1 specific question? Is there a way to completely wipe my drive so I can reinstall OSX Lion properly again? Or will this ruin my drive, making it unbootable?
I suggest that you keep trying to run Ubuntu live. Do you have an F6 key to get into that sub-menu for options? And yes, continue with the other versions!

If none of those work, download an iso file for Knoppix. It is known to be good at identifying hardware and booting on most computers. You can also use the knoppix live system to edit your partition table to make all of your hard drive available for OSX.

If you have a full backup (for example an image of the drive) then you can certainly restore your system to that point. I don't know how easy it is to reinstall OSX from scratch or if you have the tools and license for it. That information is easier to get from a Mac user forum.

---

### Post by orfeas0 on 2011-11-17
> **Olle Wiklund said:**
> I suggest that you keep trying to run Ubuntu live. Do you have an F6 key to get into that sub-menu for options? And yes, continue with the other versions!

If none of those work, download an iso file for Knoppix. It is known to be good at identifying hardware and booting on most computers. You can also use the knoppix live system to edit your partition table to make all of your hard drive available for OSX.

If you have a full backup (for example an image of the drive) then you can certainly restore your system to that point. I don't know how easy it is to reinstall OSX from scratch or if you have the tools and license for it. That information is easier to get from a Mac user forum.
I don't know how exactly but I finally fixed my partitioning!!!
I installed ubuntu in the free (10gb) space, which after installing it wasn't working. But thanks to that, I could resize my mac partition to the original 60gb!
Now the problem remains: how the hell do I boot camp into windows? But that's not for the ubuntu forums so I'll be leaving you.
Thanks for the help Olle Wiklund!

---

