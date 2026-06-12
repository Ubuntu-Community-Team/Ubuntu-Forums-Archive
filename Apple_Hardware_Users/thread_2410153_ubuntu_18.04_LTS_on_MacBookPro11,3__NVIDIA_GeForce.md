---
title: "ubuntu 18.04 LTS on MacBookPro11,3  NVIDIA GeForce GT 750M"
date: 2019-01-11
forum: Apple Hardware Users
---

### Post by i-ben on 2019-01-11
Hi, I have installed ubuntu desktop 18.04 LTS on an external USB 500gb flash drive.

I have osx 10.11.6 and windows 10 installed on macbook SSD ( working )

I can boot osx windows and ubuntu with option key.

Ubuntu freezes on startup on animation screen. If i go arrow left or right I see various networking packages fail.
Then the system just freezes. I can't get into command prompt.

I can't boot into system recover either.
I am guessing the hardware is causing a crash but can't get to the logs to know. I don't have a way to mount ext4 in osx or windows.
 
I have tried various options in Grub like [COLOR=#111111]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
[/COLOR]
and acpi_vendor etc but still freezes

I was warned on install about the partition not being aligned. there is 30mb of nothing before the 1st partition. I can't remove this if I create the large ext4 main partition.

should I now try to mount the volume from windows and get kernel crash logs?

I tried searching for MacBookPro11,3  NVIDIA GeForce GT 750M

I tried a 2nd downloading of the ISO /  checksum OK.

I was thinking of avoiding refind in case osx updates break it.

any ideas? before I give up and go out to buy an old thinkpad ! should never have bought a mac in the 1st place :)

UPDATE: I added Refind and switched on spoof mac osx option which allows windows see the intel graphics card, Ubuntu kernel still hangs on startup..
will try mount disk now and post kernel / X11 crash log..

UPDATE2: cannot mount the ext4 partition from windows with Ext2Fsd. going to try ext3.








[COLOR=#111111]
[/COLOR][COLOR=#111111]
[/COLOR][COLOR=#111111]
[/COLOR]

---

