---
title: "Wake from suspend issues with 2016 MacBookPro"
date: 2023-11-10
forum: Apple Hardware Users
---

### Post by jjkraw on 2023-11-10
I've been trying to install / debug making a 2016 MBP dual-boot with Ubuntu 22.04.03.  Before I go into any details, I just want to check if there are some basic steps for this laptop that I missed upon installation.  Here's the info.

Basic guidelines I followed for install here: [https://www.makeuseof.com/tag/install-linux-macbook-pro/](https://www.makeuseof.com/tag/install-linux-macbook-pro/)

The machine itself:


[LIST]
[*]MacBook Pro 13" (late 2016, MacBookPro13,1) 
[*]2.4 GHz Dual-Core Intel Core i7 
[*]16 GB 1867 MHz LPDDR3 
[*]Intel Iris Graphics 540 1536 MB 
[*]13.3-inch Built-in Retina Display 
[*]1TB Flash Storage 
[*]WiFi Broadcom BCM4350 1.0 
[/LIST]

The issue: Upon waking from sleep, the root filesystem becomes read-only. Looking at dmesg output, there are a number of error messages concerning changing the states of various bits of hardware. Eventually there are disk system errors ending with an error writing the superblock, which causes the filesystem to be remounted read-only.

I have the dmesg output but will hold off on that until it's clear that it's helpful (it's big). I think I have to be missing something from the start (perhaps drivers) given that other users have been successful with MacBooks.  FWIW, everything works OK if I don't suspend. The only add I had to do was to get the sound working (solution that worked: [https://askubuntu.com/questions/1254124/ubuntu-20-04-lts-no-sound-on-macbookpro](https://askubuntu.com/questions/1254124/ubuntu-20-04-lts-no-sound-on-macbookpro))

Thanks in advance.

Edit: I was able to install on a MacBook Air 13" (Mid 2012, MacBookAir5,2) with no other problems than wifi (Broadcom), so it is definitely something to do with this particular Pro's hardware and/or drivers.

---

### Post by jjkraw on 2023-11-16
Update...

I was able to get rid of the read-only file system problem by based on info I found here:
  [https://github.com/Dunedan/mbp-2016-linux](https://github.com/Dunedan/mbp-2016-linux)

Scroll down to "Suspend & Hibernation".

I found that I also needed to disable "d3cold" for a PCI bridge to get it to work consistently. I created an /etc/rc.local file with the following contents:

```
#!/bin/bash
echo 0 > /sys/bus/pci/devices/0000\:01\:00.0/d3cold_allowed
echo 0 > /sys/bus/pci/devices/0000\:04\:00.0/d3cold_allowed
```

So now I can suspend, for some definition of suspend, because I'm still seeing via dmesg what is described in this bug report here:

  [https://bugzilla.kernel.org/show_bug.cgi?id=212767](https://bugzilla.kernel.org/show_bug.cgi?id=212767)

This is a bug that was fixed and the patch has been included for 2+ years, but apparently the fix doesn't work/apply to a MacBookPro13,1.

I'll keep poking away at this, but if anyone has ideas let me know!

---

