---
title: "Black screen and blinking underscore on Ubuntu Installation."
date: 2011-09-01
forum: Apple Hardware Users
---

### Post by baloo101 on 2011-09-01
Hi, i have a problem. my internal Superdrive is broke, so I tried to install Ubuntu with an external DVD drive but it's not working… The versions I tried are, 10.04.3 (32 and 64) and 11.04 (32)

When I'm trying to install it, I got a black screen with a blink underscore and nothing happened.

I tried in FW400 and USB using external DVD, nothing
I tried to use de MacMini's of my friend as a target mode, same problem
I followed all steps here : [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) but nothing happened.
When I hold CMD si see what are de boot devices, I can see my CD with de name of Windows.
I also tried to boot on CD using rEFIt but nothing.

My MacBook is a 2,1 model with 2.0 ghz processor. I can mount my CD under OS X when I insert it into my external DVD drive

I saw this thread ([http://ubuntuforums.org/showthread.php?t=1832848](http://ubuntuforums.org/showthread.php?t=1832848)) but I don't have exactly the same problem as him so this is why I'm starting a new thread.

This a lot for your help and have a nice day.

---

### Post by baloo101 on 2011-09-01
Sorry, I did not present myself before asking this question... Can someone tell me where can I do this. Thanks.

---

### Post by baloo101 on 2011-09-03
Ok, I tried de CD's ont other computer that is not a MacBook and it's working perfectly... Some one has any idea about this problem ?

---

### Post by DoubleClicker on 2011-09-04
Do you get the blinking underscore before or after the the grub menu screen?  If it's after then then see:

[http://ubuntuforums.org/showthread.php?t=1754619](http://ubuntuforums.org/showthread.php?t=1754619)

---

### Post by baloo101 on 2011-09-05
> **DoubleClicker said:**
> Do you get the blinking underscore before or after the the grub menu screen?  If it's after then then see:

[http://ubuntuforums.org/showthread.php?t=1754619](http://ubuntuforums.org/showthread.php?t=1754619)

Thks to help me DoubleClicker, I have the blinking underscore before all, so i didn't see the grub menu.

---

### Post by DoubleClicker on 2011-09-05
Do you have the right version for your architecture?
A 64 bit CD won't boot on a 32 bit machine, and an an  x86 disk won't boot on a PPC.   

If you've verified that you have the right disk for your architecture, and still have the problem, then it means the problem is that your CDRom drive can't read your LiveCD.  Either you have a hardware problem with the drive, or the Disk is slightly damage, in a way  that Your CDRom can't be read in your the disk, but other machines can.

---

### Post by baloo101 on 2011-09-05
> **DoubleClicker said:**
> Do you have the right version for your architecture?
A 64 bit CD won't boot on a 32 bit machine, and an an  x86 disk won't boot on a PPC.   

If you've verified that you have the right disk for your architecture, and still have the problem, then it means the problem is that your CDRom drive can't read your LiveCD.  Either you have a hardware problem with the drive, or the Disk is slightly damage, in a way  that Your CDRom can't be read in your the disk, but other machines can.

Thks for the advice ;) It could be that but I have a C2D but with your advice, I tried somethings. 

- Boot from the original Snow Leopard DVD => It's work
- Boot from Ubuntu 10.04.3 or from old 10.04.1 i already burned in the past => Does not work
- Tried with GParted Live CD => Does not work
- Tried WinXP SP2 and Win7 boot CD's => Does not work at all...

So i thing that other OS'es, than Apple Mac OS X, does not like to boot from external DVD drive... :confused:

Other advice some one ? I don't want to spend an other 100$ for a Super Drive...

---

### Post by DoubleClicker on 2011-09-06
well I don't have any more advice to give about your DVD drive,   but if you are just trying to find a way to install ubuntu I have a suggestion:

1.  download the iso to your computer (or use the CD, if it will load in mac os x)

2.  using disk utility create a small 800 MB partition, in the free space that you set aside for ubuntu. and format it as FAT.

3. use Disk utility to "restore" the iso/CD to the 600mb partition

4.  Boot from the 800 MB Ubuntu "LiveCD" partition 

5.  install ubuntu just like you would from a LiveCD.

Sorry I didn't think about this earlier.

---

### Post by baloo101 on 2011-09-06
> **DoubleClicker said:**
> well I don't have any more advice to give about your DVD drive,   but if you are just trying to find a way to install ubuntu I have a suggestion:

1.  download the iso to your computer (or use the CD, if it will load in mac os x)

2.  using disk utility create a small 800 MB partition, in the free space that you set aside for ubuntu. and format it as FAT.

3. use Disk utility to "restore" the iso/CD to the 600mb partition

4.  Boot from the 800 MB Ubuntu "LiveCD" partition 

5.  install ubuntu just like you would from a LiveCD.

Sorry I didn't think about this earlier.

Thks, I tried somethings else because the restore didn't work so :
 
1- I made a FAT32 volume on my HD 
2- I followed this tutorial ([https://help.ubuntu.com/community/Installation/FromImgFiles#Mac_OS_X](https://help.ubuntu.com/community/Installation/FromImgFiles#Mac_OS_X)) but replaced usb key for my new volume

This doesn't work.

Other things, I'll take a external enclosure that is only USB, maybe there are somme issues with enclosure that has firewire / usb chipset.

I'll come back with the tests this week :) hope this work.

---

### Post by baloo101 on 2011-09-09
So.. I tried with a USB Only external DVD drive and nothing more.... I'm disappointed... Someone can help me ?

On the Ubuntu Forums FR, an other member has the same problem. Hope someone will guide me on a good steps to solve this 

:popcorn:

---

### Post by UltraNEO* on 2011-09-10
> **baloo101 said:**
> So.. I tried with a USB Only external DVD drive and nothing more.... I'm disappointed... Someone can help me ?

On the Ubuntu Forums FR, an other member has the same problem. Hope someone will guide me on a good steps to solve this 

:popcorn:

Hi baloo101. 

This blank screen with the flashing underscore has been plaguing me recently and I'm trying to install Ubuntu on my 2008 MacBookPro 4,1. For a while I've always, always thought it's the disk at fault but after burning a dozen disks with all the versions available I've came to one conclusion... My drives faulty. 

To prove this, I popped open my macbook and replaced the internal drive from another machine and guess what? Every single disk I've previous burnt booted, even those AMD64 only versions. 

Weirdest discovery, the original slot-loading drive worked for reading and writing, even  bootable with MacOS X Leopard, Snow Leopard and Window Ultimate... Just refuses to boot with any Linux installations :confused:

---

### Post by baloo101 on 2011-09-12
> **UltraNEO* said:**
> Hi baloo101. 

This blank screen with the flashing underscore has been plaguing me recently and I'm trying to install Ubuntu on my 2008 MacBookPro 4,1. For a while I've always, always thought it's the disk at fault but after burning a dozen disks with all the versions available I've came to one conclusion... My drives faulty. 

To prove this, I popped open my macbook and replaced the internal drive from another machine and guess what? Every single disk I've previous burnt booted, even those AMD64 only versions. 

Weirdest discovery, the original slot-loading drive worked for reading and writing, even  bootable with MacOS X Leopard, Snow Leopard and Window Ultimate... Just refuses to boot with any Linux installations :confused:

Thks a lot UltraNEO. Yesterday I tried with a brand new dvd drive and then retried with both same enclosure and the problem remains.... Here at Ubuntu-FR, an ohter person has the same problem : [http://forum.ubuntu-fr.org/viewtopic.php?id=630541](http://forum.ubuntu-fr.org/viewtopic.php?id=630541) but he has a MacBook Pro (he didn't say the version)

And for the slot loading drive, I already replace it and it broke just a few weeks after warranty end. I don't want to spend an other hundred box only to install Ubuntu.

Thks for everyone has help me. I'm hoping other will have suggestions.

---

