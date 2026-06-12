---
title: "Ubuntu 14.04 USB Booting"
date: 2016-01-15
forum: Apple Hardware Users
---

### Post by rafiqcombrinck on 2016-01-15
Hi All

I went through quite a few pages already and managed to eventually create a usb stick that I can boot my MacBook Pro 13 (early 2011, OS X 10.11) with. Problem is I actually created it to use on my sons ancient iMac 5.1 (OS X 10.4) and it does not want to boot from it. It sees the drive but gives me a page full of EFI errors. I even tried rEFIt but still won't work. I then created a separate partition on the internal harddrive and dd the USB stick onto that partition. Again rEFIt sees the partition but when I try and boot it it says no OS detected or some such thing.

Any clues on the way forward?

Thanks.

---

### Post by Dreamer Fithp Apprentice on 2016-01-15
Caveat: I know nothing about Macs or EFI, so this may be worthless, but:
> **rafiqcombrinck said:**
> I went through quite a few pages already and managed to eventually create a usb stick that I can boot my MacBook Pro 13 (early 2011, OS X 10.11) with.I'm surprised that was difficult. What was the problem? I haven't done this in a while but as best I remember it was just a matter of plugging in the stick, aiming the right program at the iso, and following directions from the gui.

> **rafiqcombrinck said:**
> Problem is I actually created it to use on my sons ancient iMac 5.1 (OS X 10.4) and it does not want to boot from it.If we are talking about a standard live disk (well, live stick) it should, unless maybe it's a 64 bit live stick and your son's machine is a 32 bit machine. So if it isn't something face-palming simple like that, it might just not work with that machine. But I think if there is any possibility of getting it to work, you are much more likely to get useful suggestions from people here, if you post EXACTLY what error messages you are getting. EXACTLY. This can't be stressed enough. > **rafiqcombrinck said:**
> I then created a separate partition on the internal harddrive and dd the USB stick onto that partition.I wouldn't expect that to work, and even if it did I think you'd   wind up with with a live system on a HD, which would waste RAM horribly with a virtual file system and fail to save any tweaking, settings or bookmarks past rebooting. I think you're going to have to figure out why it won't boot on your son's machine first. If you can fix that part, then you can install it. And if you can't fix that part, figuring out an alternate approach to installing without first booting the live stick, may be, if not impossible, at least a lot more trouble than it will be worth. If that is the case, I'd just try some other distros. Try Lubuntu. Or if the command line isn't to intimidating try the mini iso. Once you get a tty (like a "terminal" but without a window) working you can install the rest. Or try some non-buntus. The LXDE version of PClinuxOS is pretty good. Try a bunch of different distros.

---

### Post by rafiqcombrinck on 2016-01-16
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

These are the instructions I'm currently following and as mentioned, they work perfectly on my MacBook Pro. The iMac wants nothing to do with it though, even tried different versions (32-bit, 64-bit and some versions marked Mac). I always get this error... 

[https://www.dropbox.com/s/to3djj3hj5u39rm/2016-01-16%2006.29.15.jpg?dl=0](https://www.dropbox.com/s/to3djj3hj5u39rm/2016-01-16%2006.29.15.jpg?dl=0)

Any idea why this is?

---

### Post by este.el.paz on 2016-01-16
> **rafiqcombrinck said:**
> Hi All

I went through quite a few pages already and managed to eventually create a usb stick that I can boot my MacBook Pro 13 (early 2011, OS X 10.11) with. Problem is I actually created it to use on my sons ancient iMac 5.1 (OS X 10.4) and it does not want to boot from it. It sees the drive but gives me a page full of EFI errors. I even tried rEFIt but still won't work. I then created a separate partition on the internal harddrive and dd the USB stick onto that partition. Again rEFIt sees the partition but when I try and boot it it says no OS detected or some such thing.

Any clues on the way forward?

Thanks.

@rafiq:

rEFIt only supports up to 10.7 or so . . . try switching to rEFInd and see how that goes.  The use of the word "legacy" in the error message is a sign of "old age" . . . : - ))))  Hard to know if it's the "old" iMac, which is 32 bit . . . or rEFIt referring to itself????  Linux does prefer to have the drive formatted as FAT32 BTW . . . .  Also there is a way to "live boot an iso" . . . from within the HD partition as you say you have done, but other than the PowerPCFAQ I don't know where or how to do it, etc.  Generally the most stable way to boot the live iso is via DVD disk . . . but, perseverance furthers . . . .

e.e.p.

---

