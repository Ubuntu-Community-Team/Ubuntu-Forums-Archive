---
title: "Macbook pro 8.2: Unable to install any ubuntu version (except 10.04.2)"
date: 2011-04-15
forum: Apple Hardware Users
---

### Post by tsug on 2011-04-15
Hello guys,

  I'm getting nut. It's been 3 days I try to install Ubuntu on my brand new macbook pro 8.2 without any concluding results.

  The rpoblme is that the DVD drive doesn't get recognized by the ubuntu live CD installer. I think i've tried pretty much all the combination I could without success, including:
 - 10.10 x86 and 10.10 amd64 both live and alternate,
 - 11.04 Beta 1 x86, 11.04 Beta 1 amd64 both live and alternate,
 - Plus a couple of daily live CDs, even one labelled amd64+mac.

All of these gave me the same result: After booting the CD, the installer shows the blinking cursor, then the ubuntu logo with dots, and then always get the same message:
(initramfs) Unable to find a medium containing a live file system.

I've harvested all the forums everywhere and it seems i'm the only one facing this issue...

The only version which worked for me was the 10.04. But as soon as I upgrade it to 10.10, again, I lose the DVD drive ...

I really don't understand how you guys make it work. It seems that the 8.2 and 11.04 works fine, at least for the installation part.

Any help would be greatly appreciated !

Thanks

Edit: I added lshw before(10.04)  and after upgrade to 11.04, if any help

---

### Post by ChrisDeath on 2011-04-16
Hi tsug

have the same issue here with MacBook Pro 8.2 (early 2011). It seems to be an issue of an unsupported SATA chipset (ICH?). 
With the last year MacBooks there was the same issue: [http://ubuntuforums.org/showthread.php?t=1458341](http://ubuntuforums.org/showthread.php?t=1458341)

So hopfully somebody can patch the kernel, at least for Natty...

---

### Post by Anon7-2521 on 2011-04-16
I have a MBP 8,1 and I have the same issue. I have 10.04 installed but can't get any drivers for it. Can't even get ethernet internet to work, so it's basically worthless.

---

### Post by tsug on 2011-04-17
Yeah, when installing 10.04 there is no network available.
You can workaround this by burning the 10.10-alternate to a CD (the drive works under 10.04) and upgrade to 10.10.
Then you lose the drive but you have the network :) So you can finish the 10.10 upgrade.
Then you can install 11.04 if you wish.

---

### Post by tsug on 2011-04-17
ChrisDeath: Thanks for your feedback.
What is weird is that it's working flawless on 10.04. I don't really understand losing some drive by upgrading to a newer version.
Even weirder, nobody mentions it anywhere, so I thought it was a defect on my side. At least, it confirms I'm not the only one :)
Now, everything works fine on 11.04 except the CD drive so let's wait for a kernel patch then.

---

### Post by ChrisDeath on 2011-04-17
Tryed 10.04.2 yesterday evening too, with the same result :(
@tsug: I will try the updating thing now too ;)

---

### Post by Anon7-2521 on 2011-04-17
> **tsug said:**
> Yeah, when installing 10.04 there is no network available.
You can workaround this by burning the 10.10-alternate to a CD (the drive works under 10.04) and upgrade to 10.10.
Then you lose the drive but you have the network :) So you can finish the 10.10 upgrade.
Then you can install 11.04 if you wish.

How do you get the network to work in 10.10?

---

### Post by tsug on 2011-04-18
> **Anon7-2521 said:**
> How do you get the network to work in 10.10?

It worked for me when booting under 10.10. And by network, I mean the ethernet adapter, the wireless adapter is not working (even in 11.04).

---

### Post by Anon7-2521 on 2011-04-18
Ahhh okay. I got 11.04 installed by using both a CD and thumb drive at startup. USB internet is working though.

---

### Post by borist on 2011-04-21
Hi tsug,
I am in the same situation, 11.04 b2 finally works but no CD/DVD and no build in wireless. From reading this [http://ubuntuforums.org/showpost.php?p=10537481&postcount=55](http://ubuntuforums.org/showpost.php?p=10537481&postcount=55) post it seems that if we want to get it fixed we need to send _mario_ more info. 

I am wondering if we need to open a bug for this or is there already one open?

---

### Post by tsug on 2011-04-22
I didn't file a bug as I don't know exactly what I need to provide. So if you feel like it, do it or give me the info _mario_ needs and I'll open it :)
Thanks

---

### Post by borist on 2011-04-23
> **tsug said:**
> I didn't file a bug as I don't know exactly what I need to provide. So if you feel like it, do it or give me the info _mario_ needs and I'll open it :)
Thanks

See [http://ubuntuforums.org/showpost.php?p=10705256&postcount=298](http://ubuntuforums.org/showpost.php?p=10705256&postcount=298)

---

### Post by tsug on 2011-05-13
Ok I've finally file a bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782389)

Cheers

---

### Post by jedibrand on 2011-07-08
Just wanted to report that, like anon, I got the install working by dd'ing the install iso onto a usb flashdrive, then using a cd burned with the iso to boot the flashdrive.

dd if=/path/to/ubuntu-install.iso of=/dev/diskN bs=1m

to burn the flash drive (diskN). You can follow the instructions and heed the caveats provided by Ubuntu for burning a usb flashdrive with the install iso on a Mac ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)). Finally, insert the cd and usb flash drive into the Mac, hold alt to get the boot menu, and choose the "Windows" menu item. Then just be sure to chose "Try Ubuntu without installing" (I'm paraphrasing here...).

You can also create a separate partition on your only disk, but you'll first need to create a PT in msdos on the disk, and for that you'll need a live cd that actually boots on the new 8,1 macs...

---

### Post by tsug on 2011-07-08
Ok, good to know. Thanks for your reply.

---

### Post by amo3 on 2011-07-08
> **jedibrand said:**
> Just wanted to report that, like anon, I got the install working by dd'ing the install iso onto a usb flashdrive, then using a cd burned with the iso to boot the flashdrive.

dd if=/path/to/ubuntu-install.iso of=/dev/diskN bs=1m

to burn the flash drive (diskN). You can follow the instructions and heed the caveats provided by Ubuntu for burning a usb flashdrive with the install iso on a Mac ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)). Finally, insert the cd and usb flash drive into the Mac, hold alt to get the boot menu, and choose the "Windows" menu item. Then just be sure to chose "Try Ubuntu without installing" (I'm paraphrasing here...).

You can also create a separate partition on your only disk, but you'll first need to create a PT in msdos on the disk, and for that you'll need a live cd that actually boots on the new 8,1 macs...

I'm having the same issue as everyone else, except it seems I am unable to get 10.04 to work either.  I have tried using the USB stick alone, but could not get it to appear as a bootable device using the Ubuntu guide.  Using a guide from the forums, I was able to get it to appear as a bootable device, but every menu option resulted in "Missing kernel".  

I am going to try this method of using both the CD and the flashdrive to see if I can replicate your results.  Exactly which version did you use? Thank you.

---

### Post by jedibrand on 2011-07-08
> **amo3 said:**
> I'm having the same issue as everyone else, except it seems I am unable to get 10.04 to work either.  I have tried using the USB stick alone, but could not get it to appear as a bootable device using the Ubuntu guide.  Using a guide from the forums, I was able to get it to appear as a bootable device, but every menu option resulted in "Missing kernel".  

I am going to try this method of using both the CD and the flashdrive to see if I can replicate your results.  Exactly which version did you use? Thank you.

11.04 (standard install, not the alternate)

---

### Post by nyargh on 2011-07-08
> **jedibrand said:**
> Just wanted to report that, like anon, I got the install working by dd'ing the install iso onto a usb flashdrive, then using a cd burned with the iso to boot the flashdrive.

dd if=/path/to/ubuntu-install.iso of=/dev/diskN bs=1m

to burn the flash drive (diskN). You can follow the instructions and heed the caveats provided by Ubuntu for burning a usb flashdrive with the install iso on a Mac ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)). Finally, insert the cd and usb flash drive into the Mac, hold alt to get the boot menu, and choose the "Windows" menu item. Then just be sure to chose "Try Ubuntu without installing" (I'm paraphrasing here...).

You can also create a separate partition on your only disk, but you'll first need to create a PT in msdos on the disk, and for that you'll need a live cd that actually boots on the new 8,1 macs...


I am dual booting 11.04 and OSX via refit on an 8,2 MBP.  I had to boot off a CD and USB drive to do the install (boot off CD, then install off thumb drive, but it is all seamless).

Basically, install process is:

1. Shrink OSX partition and create new "Windows" using Bootcamp in OSX
2. Install Refit
3. Insert CD and USB key with Ubuntu 11.04 live cd and reboot
4. Select "LIVECD" in Refit
5. Delete "Windows" partition during Ubuntu install and create root ext4 partition and swap
6. Install Ubuntu 11.04

---

### Post by jedibrand on 2011-07-08
> **nyargh said:**
> I am dual booting 11.04 and OSX via refit on an 8,2 MBP.  I had to boot off a CD and USB drive to do the install (boot off CD, then install off thumb drive, but it is all seamless).

Basically, install process is:

1. Shrink OSX partition and create new "Windows" using Bootcamp in OSX
2. Install Refit
3. Insert CD and USB key with Ubuntu 11.04 live cd and reboot
4. Select "LIVECD" in Refit
5. Delete "Windows" partition during Ubuntu install and create root ext4 partition and swap
6. Install Ubuntu 11.04

Got it. To clarify, when I mentioned the option to "create a separate partition on your only disk" I meant it for housing the install iso. In other words, if you don't have access to a usb flashdrive, this option might be handy. 

Yet another option would be to use an external media drive with drivers known-to-work on Linux.

Of course, if you're dual-booting, then no need to heed my advice about creating an msdos partition table...

---

### Post by watgrad on 2011-07-12
> **jedibrand said:**
> Just wanted to report that, like anon, I got the install working by dd'ing the install iso onto a usb flashdrive, then using a cd burned with the iso to boot the flashdrive.

dd if=/path/to/ubuntu-install.iso of=/dev/diskN bs=1m


How do you do this step?  I'm don't know how to make a cd that boots to the flashdrive...

---

### Post by jedibrand on 2011-07-12
> **watgrad said:**
> How do you do this step?  I'm don't know how to make a cd that boots to the flashdrive...

My poor wording is to blame here! What I meant was, burn a CD with the regular old Ubuntu installer iso, and then also dd that iso onto a thumbdrive. Then, pop in the CD, and connect the thumbdrive. Turn on your machine, press alt for the boot menu, and choose "Windows." Proceed as you normally would to install Ubuntu (via the "try without/before installing" option).

This allows you to get around two issues. The first is that I could not boot off the thumbdrive alone (it just does not show up in the boot menu). The second, is that the driver support for the new Macbook media drive on Linux is shabby. That is, the boot sector is loaded properly (that's why the "Windows" option shows up on the boot menu), but the OS itself (Ubuntu) wont load properly off the CD. Therefore, the second-stage boot loader on the CD automagically searches for Ubuntu in alternate storage devices, in this case the thumbdrive. It finds Ubuntu there and loads it. Tada!

---

### Post by Neds Moar Salt on 2011-07-12
If you have a buddy with a working ubuntu/debian installation, recreate the initrd with the required module.  You will probably be able to find it in the initrd that works.  (Maybe the kernel will let you use the old initrd with the new kernel)

Another option is install the old one and then grab the module you need and add it to /etc/initramfs-tools/modules (and rebuild of course).

---

### Post by watgrad on 2011-07-13
> **jedibrand said:**
> My poor wording is to blame here! What I meant was, burn a CD with the regular old Ubuntu installer iso, and then also dd that iso onto a thumbdrive. Then, pop in the CD, and connect the thumbdrive. Turn on your machine, press alt for the boot menu, and choose "Windows." Proceed as you normally would to install Ubuntu (via the "try without/before installing" option).

This allows you to get around two issues. The first is that I could not boot off the thumbdrive alone (it just does not show up in the boot menu). The second, is that the driver support for the new Macbook media drive on Linux is shabby. That is, the boot sector is loaded properly (that's why the "Windows" option shows up on the boot menu), but the OS itself (Ubuntu) wont load properly off the CD. Therefore, the second-stage boot loader on the CD automagically searches for Ubuntu in alternate storage devices, in this case the thumbdrive. It finds Ubuntu there and loads it. Tada!

Thanks for your reply.  I did this, so there was an improvement but not full success.  The installation seems to get into some sort of endless loop now.  I lo longer get the error about not finding an active file system.  However, the computer simply displays the ubuntu logo with the flashing orange dots endlessly.  It never moves beyond this... not sure what the next step would be - perhaps there will be an updated installation live cd? or is there another work around?

---

### Post by jedibrand on 2011-07-14
> **watgrad said:**
> Thanks for your reply.  I did this, so there was an improvement but not full success.  The installation seems to get into some sort of endless loop now.  I lo longer get the error about not finding an active file system.  However, the computer simply displays the ubuntu logo with the flashing orange dots endlessly.  It never moves beyond this... not sure what the next step would be - perhaps there will be an updated installation live cd? or is there another work around?
Did you remember to hit any key on the keyboard at the screen with (if i recall correctly) the following logos at the bottom:

(Something that looks like Da Vinci's Vitruvian Man) + (equal-sign) + (keyboard)

For some reason, Ubuntu does not mention that step in their installation guide...

---

### Post by watgrad on 2011-07-14
> **jedibrand said:**
> Did you remember to hit any key on the keyboard at the screen with (if i recall correctly) the following logos at the bottom:

(Something that looks like Da Vinci's Vitruvian Man) + (equal-sign) + (keyboard)

For some reason, Ubuntu does not mention that step in their installation guide...

Thanks again for your help - yes - did that.  Still couldn't get it to boot from the USB flash drive.  I eventually got it to work from an old backup drive that I made into a startup disk. 
It is running now.  I followed the directions in the online wiki ([https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless)) to get most things working.  (I just have to wait for the wireless driver problem to get solved and all will be good.) I appreciate the powertops suggestions for improving battery life and I also noticed another post about power consumption issues in linux ([http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html))  
Does anyone know if this applies to macbookpro?  
Does apple use Active-State Power Management?

Thanks for your advice...

---

### Post by jedibrand on 2011-07-14
> **watgrad said:**
> Thanks again for your help - yes - did that.  Still couldn't get it to boot from the USB flash drive.  I eventually got it to work from an old backup drive that I made into a startup disk. 
It is running now.  I followed the directions in the online wiki ([https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Wireless)) to get most things working.  (I just have to wait for the wireless driver problem to get solved and all will be good.) I appreciate the powertops suggestions for improving battery life and I also noticed another post about power consumption issues in linux ([http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html))  
Does anyone know if this applies to macbookpro?  
Does apple use Active-State Power Management?

Thanks for your advice...
good to hear you got things working. See my post here about my success with a micro wireless dongle from trednet:

[http://ubuntuforums.org/showpost.php?p=11047969&postcount=510](http://ubuntuforums.org/showpost.php?p=11047969&postcount=510)

I;m currently only using it via 4G, tethered to my phone (using the foss wifi "hotspot" app for android, forget the name presently...)

---

### Post by amo3 on 2011-07-15
I just wanted to note that USB and CD worked!  With the live CD it was  automatic.. With the alternate install I needed to manually mount the  USB to /cdrom with "mount -t iso9660 /dev/sdb /cdrom"

Thanks again.. Now running into the wireless issue. :/ Trackpad seems a bit crazy too.

---

### Post by schut on 2011-08-06
I'm having the same issues and I'm thinking about waiting until 11.10 is released.

Do you think we can expect any improvement of the situation with the new version?

---

### Post by zimmea on 2011-08-13
Hey guys,

Thanks for this thread, however, I am still having issues installing 11.04 on my macbook pro 8.2.

I downloaded the 11.04 64bit+mac live CD, used the universal installer to create a bootable USB drive for it, also burned the iso to a DVD, and installed refit on the mac.

popped in dvd and usb drive. powered on the mac. chose to boot linux. pressed F6 and told the installer to user nomodereset (other threads recommended this) and have tried noacpi as well.

chose to install linux

The install screen pops up. Chose english, and the "preparing to install" screen pops. I'm connected to power, have HD space and am connected to the net over Ethernet.

I click forward and it just hangs. responsive cursor but nothing else happens. I've also tried clicking the install 3rd party software option and it makes no difference.

Any advice? I'm relatively green with Linux. I want to use it to run ROS for a robot i'm building.

Thanks in advance!

---

### Post by crook17 on 2011-08-13
i seem to be having the same problem, i also tried fedora with no luck, to install i simply mad a bootable usb drive with uni boot and burned the iso to cd put both into the mac and it fell back onto the usb when i didnt detect the cd drive.

You can see my post here
[http://ubuntuforums.org/showthread.php?t=1823356](http://ubuntuforums.org/showthread.php?t=1823356)

---

### Post by Gyuyoung Kim on 2011-09-13
> **tsug said:**
> Yeah, when installing 10.04 there is no network available.
You can workaround this by burning the 10.10-alternate to a CD (the drive works under 10.04) and upgrade to 10.10.
Then you lose the drive but you have the network :) So you can finish the 10.10 upgrade.
Then you can install 11.04 if you wish.

I have same situation. I succeed to install 10.04 on macbook pro 8.2. However, I failed to upgrade to 10.10 with a CD. Could you please let me know which 10.10 version you used during the upgrade ?

---

### Post by KillerKellerjr on 2012-04-05
I recently installed several version of Ubuntu on my MacBook Pro 8.2. I cheated but it still works. I installed bootcamp and Windows 7. Then installed successfully Ubuntu 11.04, 11.10, 12.04 Final Beta & Linux Mint 12 using wubi within Windows 7. I know its not native or running on its own partition but it works great for me and is really fast, I have 8GB of memory. For the most part everything work including Wi-Fi after installing the correct drivers with a wired connection. Wi-fi is a little flakey but workable. To install wifi perform the following:

```
sudo apt-add-repository ppa:mpodroid/mactel
sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

---

