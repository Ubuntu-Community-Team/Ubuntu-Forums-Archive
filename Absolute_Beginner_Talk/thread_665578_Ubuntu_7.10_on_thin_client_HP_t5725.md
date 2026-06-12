---
title: "Ubuntu 7.10 on thin client HP t5725"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Bakken on 2008-01-12
Hello everybody, it's my first post here, I've got a little problem with Ubuntu I can't google the answer to, so I humbly ask you for help...

I have just installed Ubuntu 7.10 on an HP thin client t5725.

It's a marvelous piece of hardware -- very small and completely silent. It comes with 512M ram, 512M internal flash disk, six USB-slots, a PCI slot (optional), and external DVD-rom (optional) and some real old Debian pre-installed.

I've plugged in some old PCI wireless card from my old computer. Since Ubuntu would not fit in the little built-in drive I have found some four old USB sticks with total capacity of 7G and plugged them in also.

Booted Ubuntu from the CD, ran install and put / on the internal drive, and distributed /usr, /home, /tmp, /var, and swap on the four USB sticks.

It installed all right but wouldn't reboot. So I boot in rescue mode and see that my four USB-drives are not automatically mounted. The drive letters assigned to USB-drives on startup are random, so to keep track of the many partitions (/usr, /home, /tmp, /var) I label them with e2label, like

e2label /dev/sde1 HOME
e2label /dev/sdc1 USR
...

and then edit my /etc/fstab file as:

proc            /proc           proc    defaults        0       0
/dev/sda1       /       ext3 defaults,errors=remount-ro         0 1
LABEL=HOME      /home   ext3 defaults                           0 0
LABEL=TMP       /tmp    ext3 defaults                           0 0
LABEL=USR       /usr    ext3 defaults                           0 0
LABEL=VAR       /var    ext3 defaults                           0 0

however, it still wouldn't boot. I have to boot into rescue mode and then

mount -a
exit

and after that the whole thing works like a charm. I am typing this post from this little box right now.

Why does it not automatically mount my USB-sticks?

Thanks in advance!

---

### Post by blueridgedog on 2008-01-12
Have you tried a basic fstab setup w/o labels and simple names of the devices such as /dev/sde1 etc?

---

### Post by dcstar on 2008-01-12
> **Bakken said:**
> 
..........
proc            /proc           proc    defaults        0       0
/dev/sda1       /       ext3 defaults,errors=remount-ro         0 1
LABEL=HOME      /home   ext3 defaults                           0 0
LABEL=TMP       /tmp    ext3 defaults                           0 0
LABEL=USR       /usr    ext3 defaults                           0 0
LABEL=VAR       /var    ext3 defaults                           0 0

however, it still wouldn't boot. I have to boot into rescue mode and then

mount -a
exit

and after that the whole thing works like a charm. I am typing this post from this little box right now.

Why does it not automatically mount my USB-sticks?

Thanks in advance!

I'm not sure that the part of the startup that mounts USB devices is run before the system requires critical system directories like /tmp, /var & /usr.

I'd speculate that the normal boot-up sequence requires these to be on a "normal" drive, not an external (USB) one.

I would recommend that you actually boot off a USB drive:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by blueridgedog on 2008-01-12
Looking to know more theoretically:

What about systems then that boot off of USB drives entirely?  Don't the base initrd includes support for USB storage device?  I would almost consider it a bug if initrd include the code to mount the but the device wasn't mounted in time to be used in the file system.

And ... are you up late or up early over in Australia?

---

### Post by Bakken on 2008-01-13
> **blueridgedog said:**
> Have you tried a basic fstab setup w/o labels and simple names of the devices such as /dev/sde1 etc?

Yes, and the problem is that although the built-in disk is always /dev/sda the four external disks get after each reboot different random letters for some reason...

Thus the /usr disk is sometimes /dev/sdc and after next reboot it becomes /dev/sdf. Labels are persistent and I can manually mount disks with 'mount -a' but it is not getting done automatically on startup :(

---

### Post by Bakken on 2008-01-13
> **dcstar said:**
> I'm not sure that the part of the startup that mounts USB devices is run before the system requires critical system directories like /tmp, /var & /usr.

I'd speculate that the normal boot-up sequence requires these to be on a "normal" drive, not an external (USB) one.

I would recommend that you actually boot off a USB drive:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Yeah, you are probably right, the system can boot off an external USB-disk but apparently the whole system must be on the boot disk, not on several small external USB-disks. The problem is, ubuntu needs about 4G disk to install in normal mode and I just haven't got such big USB-disk.

well, seems like I'll have to mount my disks manually from recovery mode each reboot. Not really a big deal, I can live with that until I get myself a real big external disk.

Thanks for your attention!

---

### Post by Bakken on 2008-01-13
> **blueridgedog said:**
> Looking to know more theoretically:

What about systems then that boot off of USB drives entirely?  Don't the base initrd includes support for USB storage device?  I would almost consider it a bug if initrd include the code to mount the but the device wasn't mounted in time to be used in the file system.

And ... are you up late or up early over in Australia?

This t5725 can boot off a USB-disk all right but it seems that at the boot time only this one bootable USB-disk is mounted. The systems boots and then at some point looks for the other USB-disks, but aparently only after /etc/fstab is processed.

So I boot into recovery, the system mounts only / and /boot (which are on the bootable disk) and complaints that the other disks in /etc/fstab are unknown. By the time it stops complaining the USB-drives are already getting recognized but it's too late. At this point manual 'mount -a' mounts all the partitions. Then you exit from the recovery mode and the system happily does its stuff, and then loads gdm, and everything is fine since then (except that USB-disks are noticably slower than hard-disks, although quite acceptable and completely silent, and they also blink nicely :lol:).

I guess, I have to content myself with this funny booting procedure until something comes up...

And yes, I was a bit late yesterday (I live in Denmark), changing my /etc/fstab and rebooting and looking at the screen...

---

### Post by blueridgedog on 2008-01-13
Not a solution, but can you invest in a larger USB drive that can handle the entire system?

---

### Post by Bakken on 2008-01-13
> **blueridgedog said:**
> Not a solution, but can you invest in a larger USB drive that can handle the entire system?

Yes, I guess this would work (and it actually does with the little ancient debian which was preinstalled on the 512M built-in flash). I just thought it's cool to distribute the system over several flash-disks so that the overall performance would be a bit better, as the flash-disks are not exceptionally fast. And then I couldn't wait until Monday... :)

---

