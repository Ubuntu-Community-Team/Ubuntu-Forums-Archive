---
title: "no keyboard &amp; trackpad in livecd on macbook air 2012"
date: 2012-08-01
forum: Apple Hardware Users
---

### Post by appleair on 2012-08-01
when i first boot into the livecd, before loading the OS, the keyboard works fine, as the only way i'm able to boot into the OS without getting a kernel panic is to set acpi to off which i do through the keyboard, however once it actually gets boots into the OS, neither the keyboard or trackpad are functioning anymore, hitting the capslock key doesn't even turn the capslock LCD on 

i have a brand new macbook air, latest generation

any workarounds for this?

---

### Post by uymj on 2012-08-06
Same problem here. Also: no wireless and no ethernet.

---

### Post by naresh pathipati on 2012-08-06
I guess,may be u shud try booting with other OS versions of linux. or else may be u were booting unstable version of UBUNTU

---

### Post by sgarman on 2012-08-06
If you are only interested in running the livecd, I'm not sure I can help you. However I have the 13" 2012 MBA (5,2) and was able to install 12.04 easily via a USB thumb drive. 

Check out this posting:

[http://grigio.org/macbook_air_4_1_2011_ubuntu_linux_12_04_liveusb](http://grigio.org/macbook_air_4_1_2011_ubuntu_linux_12_04_liveusb)

I personally used the +mac alternate version of the daily 12.04 ISO from a few days ago. You can get that from here:

[http://cdimage.ubuntu.com/precise/daily/current/](http://cdimage.ubuntu.com/precise/daily/current/)

Simply dd that iso file to a USB thumb drive (using the full disk filename, not a partition, e.g, /dev/sdb, not /dev/sdb1).

You can then insert this USB thumbdrive into your MBA and turn it on with the Alt key held down. Select the "Windows" disk to boot from and the alternate installer should come up. After selecting my language, I hit F6 and enabled the "noapic" boot option, which I've heard is necessary for stability. From there the install went smoothly.

Note in my case I am using the entire drive for Ubuntu. You may need to use rEFIt and set up your disk partitions beforehand if your goal is to dual-boot Ubuntu and OS X.

Hope this helps,

Scott

---

### Post by uymj on 2012-08-08
> **naresh pathipati said:**
> I guess,may be u shud try booting with other OS versions of linux. or else may be u were booting unstable version of UBUNTU

I tried Mint and also Fedora. Same effect. Interestingly, running Ubuntu in a virtual machine is perfectly fine...

---

### Post by 2blue on 2012-08-08
There must be a workaround for this as long as it works during booting, there should be a way to get these tettings in fully booted system? 

For those who  like to run an os from live CD Puppy Linux has versions for Mac, it is made to run from CD and RAM, most often with a small savefile. Should be no trouble keeping with an osx/ubuntu dualboot setup. You will hardly now it is there.

---

### Post by uymj on 2012-08-31
> **sgarman said:**
> If you are only interested in running the livecd, I'm not sure I can help you. However I have the 13" 2012 MBA (5,2) and was able to install 12.04 easily via a USB thumb drive. 

Check out this posting:

[http://grigio.org/macbook_air_4_1_2011_ubuntu_linux_12_04_liveusb](http://grigio.org/macbook_air_4_1_2011_ubuntu_linux_12_04_liveusb)



Well, this doesn't work for the MacBook Air 5,2

> **sgarman said:**
> 
I personally used the +mac alternate version of the daily 12.04 ISO from a few days ago. You can get that from here:

[http://cdimage.ubuntu.com/precise/daily/current/](http://cdimage.ubuntu.com/precise/daily/current/)

Tried this, too. When I do create the disk from MacOS, it doesn't even recognize the USB stick during rebooting; when I create the startup disk from Ubuntu, it recognizes it but immediately crashes with a boot error

---

### Post by uymj on 2012-09-26
OK, I think I found a pretty good description:

[http://maketecheasier.com/install-dual-boot-ubuntu-in-macbook-air/2012/08/27](http://maketecheasier.com/install-dual-boot-ubuntu-in-macbook-air/2012/08/27)

I had problems with 12.04, but I used 12.10. It seems that 12.10 supports more or less all the hardware things. Download the current version from here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and choose the +mac option.

---

