---
title: "Having trouble with usb install"
date: 2013-04-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by joco1500 on 2013-04-07
Hello all

i have a asus aspire one with windows xp in it. i would like to put ubuntu in it because i finally got out of high school

i have went into the BIOS and changed it to boot to the usb drive because it doesn't have a disc drive (netbook)
i know that i made the usb right because i used it to put ubuntu on my desktop (a dell if that matters) the day before
i have tried to install it twice now but it won't boot from usb. 

can someone help me plz?

---

### Post by UltimateCat on 2013-04-08
Hi:

These instructions for Installation from USB should help-;-)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You will most likely have to shrink the Win's partition in order to make room for the Ubuntu installation.
[http://www.wikihow.com/Shrink-a-Windows-XP-Partition](http://www.wikihow.com/Shrink-a-Windows-XP-Partition)

Before you install Ubuntu make sure that you write down all of your Win's XP partitions so that when the Ubuntu installer paritition manager takes you to the partition scheme you will know what partitions not to click on or highlight.

When I installed Linux on my laptop I had to first shrink the Windows partition and than proceed with the Linux install.
During the Linux install I had to manually create my Linux partitions. 

For example:
```
dev/sda ( /) boot I allocated 20GB for the journaling file system
dev/sda swap I allocated 2 GB

```

The Ubuntu installer partition manager may have other choices but one of them is to allow the new install to completely take over the entire drive. (I know that's not what you want) So see what options you have.
There may be an option for allowing the partition manager to keep Windows and still comply to due the Ubuntu install-

Reading the installation documentation is recommended-
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

