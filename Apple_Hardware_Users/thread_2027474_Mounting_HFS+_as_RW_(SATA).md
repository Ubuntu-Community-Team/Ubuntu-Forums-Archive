---
title: "Mounting HFS+ as RW (SATA)"
date: 2012-07-16
forum: Apple Hardware Users
---

### Post by adidas77 on 2012-07-16
I am trying to mount my HFS+ formated external hard drive in Ubuntu 12.04 Desktop 64 Bit with read-write permissions. I can get it to mount ro easily but not rw. To give you a little more info the drive was formatted on my macbook pro running OS X v10.6, is 2 TB in size, and is connected to my computer via a SATA to eSATA cable.

I have tried a lot of things that people have listed online, and corrupted the drive several times. I would like to get it working well without fear of it crashing one day.

I have tried:
- disabling/enabling journaling (either way it doesn't work, when its not journaled I have a higher corrpution rate)

-installing "hfsprogs", "hfsutils", and "hfsplus"
(these things have a really high rate of corrupting my drive)

-I have made my ubuntu UID match my Mac UID
(as listed in the fourth comment here: [http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write))

Generally the command I use is:
```
sudo mount -t hfsplus -o force,rw /dev/sdx# /media/mylocation
```
In the past this worked, but now it is not.

I have gotten the drive to mount properly in the past, which is why I know for a fact that it is possible. I have had to reinstall Ubuntu on my computer several times (I tinker with something else, break it, then need to reinstall) and each time it is a huge pain to get it to work. I have gotten it to work 3 times before, each time I spend a ton of time working on it, modifying the mount command, fstab entry, etc and it eventually just works. Whats weird is that it never is anything consistent, I just reboot one time and then it works. I would like to figure out exactly what the trick is so I can be confident in doing it in the future. In the past once I got it working I was able to add an entry in /etc/fstab and it mounted automatically with the correct permissions,  etc:

```
UUID=yourUUID /media/yourlocation hfsplus force,rw,nobootwait 0 0
```
I am now on the 4th time and I can't get it to work. I have done all the tricks I have done in the past and none work. I have even formatted a USB pen drive as HFS+ and have messed with mounting it (that way I can corrupt it and not my hard drive with all my data). The point I have gotten to now I can actually mount the USB drive as rw but not the external hard drive which seems crazy to me because the only difference is the way they interface with the system (USB vs SATA).

I require that the hard drive be mounted via eSATA and not USB because I need the extra transfer speed. Also I require that it be HFS+ because I need it to work with my mac as well as others and my experience with FUSE support of other formats on the mac hasn't been very good.

Please let me know anything that might help!

P.S. I thought of this after I posted but the last time I got it working I shutdown the computer and when I rebooted it wouldn't boot up. I figured out that it was trying to boot off my external hard drive (eSATA) rather than my internal (SATA). I ended up solving the problem by swapping the SATA ports on my motherboard that the drives were connected to. It didn't make very much sense to me but the only thing I could think of was that somehow the SATA ports have varying priority for boot. What was weird was that with the original configuration (the one resulting in a boot from the external) it wouldn't mount properly but after I reconfigured it (to boot off the appropriate drive) then it would. I have experimented with configurations this time to no avail.

---

### Post by rduke15 on 2012-11-12
On a fresh Ubuntu install, your HFS+ drive should mount read-only automatically, without having to tinker with anything.

Unless if it's a drive over 2TB in size, in which case dmesg should show you "hfs: volumes larger than 2TB are not supported yet"

Your problem may come from the eSATA connection which is not recognized as E-sata but as plain SATA, preventing automount. Your SATA port may be configurable in the BIOS to be marked as eSATA. That depends on your SATA chipset and on the BIOS.

If you have trouble hot-plugging esata drives (any partition type), the boot options "pciehp_force=1" and "pciehp_poll_mode=1" may help. They would be added in /etc/default/grub:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp_force=1 pciehp_poll_mode=1"
```

But it is not clear if your problem is (also?) related to hotplugging. So before changing options, make sure (with a NTFS or ext3 esata disk) that it is indeed (part of) your problem.

Once Ubuntu mounts your drive normally, but read-only, you can remount it read-write as [shown here]("http://superuser.com/a/348870/53547"):

```
sudo mount -o remount,rw,force /dev/sdx
```

---

