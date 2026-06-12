---
title: "asus eeepc 1015cx boot stuck"
date: 2012-11-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by svrkispm on 2012-11-28
Hello,
I have and USB key with Ubuntu 10.04.4 LTS (kernel 3.2.0) on it. Recently I have bought an Asus EEEPC 1015 CX. I am unable to boot this USB key on it.
Moreover, I have older USB key with 10.04 LTS installed (kernel 2.6.33) which also doesn't boot.

I was suspecting this to be a kernel problem, so I have tried other kernel versions, namely 3.5, 3.6, and 3.7 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), but this didn't help.

Symptoms: in recovery mode: boot process prints "Loading initial ramdisk ...", then screen refreshes and it gets stuck with cursor blinking in top left part of the screen.
in normal mode: all I get is a blank screen.

Thank you for any ideas.

---

### Post by alex quim on 2012-11-28
hi, sorry to do this. I am new in this forum and I dont know how to start a topic (thread), sorry about my english, my mother tongue is portuguese, sorry about everything.
thanks for help and atention

---

### Post by svrkispm on 2012-11-28
> **alex quim said:**
> hi, sorry to do this. I am new in this forum and I dont know how to start a topic (thread), sorry about my english, my mother tongue is portuguese, sorry about everything.
thanks for help and atention

click the big red "NewThread" button in top left side ;)

---

### Post by alex quim on 2012-11-28
> **svrkispm said:**
> click the big red "NewThread" button in top left side ;)

I cant see it, only "NEW REPLY"

---

### Post by svrkispm on 2012-11-28
> **alex quim said:**
> I cant see it, only "NEW REPLY"

go to [http://ubuntuforums.org/forumdisplay.php?f=408](http://ubuntuforums.org/forumdisplay.php?f=408) and then click new thread

---

### Post by sudodus on 2012-11-28
> **svrkispm said:**
> Hello,
I have and USB key with Ubuntu 10.04.4 LTS (kernel 3.2.0) on it. Recently I have bought an Asus EEEPC 1015 CX. I am unable to boot this USB key on it.
Moreover, I have older USB key with 10.04 LTS installed (kernel 2.6.33) which also doesn't boot.

I was suspecting this to be a kernel problem, so I have tried other kernel versions, namely 3.5, 3.6, and 3.7 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/), but this didn't help.

Symptoms: in recovery mode: boot process prints "Loading initial ramdisk ...", then screen refreshes and it gets stuck with cursor blinking in top left part of the screen.
in normal mode: all I get is a blank screen.

Thank you for any ideas.

The following reply assumes that you have some experience with linux, and that you have at least a live system running on some computer. (Otherwise let us know, and we can help you do the corresponding things from Windows.)

I have booted an eeepc from a USB pendrive with Ubuntu. I do not remember that I had to use some particular boot options. But it might be important how to prepare the USB device.

Usually it works if you

- make a partition, format it to FAT32, and add a boot flag
and an lba flag.

- use Unetbootin to transfer the live system from the iso file to the USB drive.

I suggest that you try with the newest long time support version, 12.04 LTS. And for an eeepc I suggest Lubuntu or Xubuntu instead of vanilla Ubuntu, so download those iso files :-)

See the following links for more details!

[[COLOR="Red"]http://ubuntuforums.org/showpost.php?p=11546560&postcount=5[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")
[[COLOR="red"]http://ubuntuforums.org/showthread.php?t=1958073[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by sudodus on 2012-11-28
Have you tried any boot option?

The first one to try is **nomodeset**.

See for example
[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

This is straight-forward when you boot from a CD or from a USB drive, that you have cloned directly from the USB drive, while it means editing the boot menu in a Unetbootin system.

This link shows how to clone the iso file (dd image of the iso file)
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1958073[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by svrkispm on 2012-11-28
> **sudodus said:**
> Have you tried any boot option?

The first one to try is **nomodeset**.

See for example
[[COLOR="Red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

This is straight-forward when you boot from a CD or from a USB drive, that you have cloned directly from the USB drive, while it means editing the boot menu in a Unetbootin system.

This link shows how to clone the iso file (dd image of the iso file)
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1958073[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")


Hello,
thank You very much for Your swift reply,
"recovery" grub record is using nomodeset by default (so it didn't help). Currently the only nonstandard boot option I am using is "elevator=noop". I have tried boot options "noacpi, noapic, novga", it didnt't help either.

I am using 10.04 and I would very much prefer to continue using it, I want to avoid the upgrade to 12.04 at all costs. 10.04 is LTS and this notebook has some sticker saying "ubuntu certified" on it, so I expected, that with some effort this should work too.

I have few years experience with linux, and I would love to prefer some "nice" solution (imo building my own kernel is NOT a nice solution, but as a last resort I am willing to try this too).

For the start, is there any way to determine WHY it gets stuck after loading ramdisk? I would like to see some very verbose output on what it is doing and where it fails, how can I enable it?

---

### Post by svrkispm on 2012-11-28
> **sudodus said:**
> The following reply assumes that you have some experience with linux, and that you have at least a live system running on some computer. (Otherwise let us know, and we can help you do the corresponding things from Windows.)

I have booted an eeepc from a USB pendrive with Ubuntu. I do not remember that I had to use some particular boot options. But it might be important how to prepare the USB device.

Usually it works if you

- make a partition, format it to FAT32, and add a boot flag
and an lba flag.

- use Unetbootin to transfer the live system from the iso file to the USB drive.

I suggest that you try with the newest long time support version, 12.04 LTS. And for an eeepc I suggest Lubuntu or Xubuntu instead of vanilla Ubuntu, so download those iso files :-)

See the following links for more details!

[[COLOR="Red"]http://ubuntuforums.org/showpost.php?p=11546560&postcount=5[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")
[[COLOR="red"]http://ubuntuforums.org/showthread.php?t=1958073[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

Sorry, maybe I wasn't clear in my previous post: the mission objective is not to make any ubuntu work on this machine, the mission is to make my usb key with my standard ubuntu 10.04 boot on this machine.

The usb key is perfectly fine, it boots fine on maybe 4-5 other machines (namely my older asus and my thinkpad), and it looks like this:
```

sudo fdisk /dev/sdc
Password or swipe finger: 

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sdc: 3980 MB, 3980394496 bytes
255 heads, 63 sectors/track, 483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e73ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          15      120456   83  Linux
/dev/sdc2              16         461     3582495   83  Linux

```

---

### Post by svrkispm on 2012-11-28
One new discovery - 32 bit ubuntu 12.04 with kernel 3.2.0-x DOES boot.

I have tried very simillar kernel, but my system is 10.04 and 64 bit, and it DOESN'T boot - may this be the key?

---

### Post by sudodus on 2012-11-28
> **svrkispm said:**
> Sorry, maybe I wasn't clear in my previous post: the mission objective is not to make any ubuntu work on this machine, the mission is to make my usb key with my standard ubuntu 10.04 boot on this machine.

The usb key is perfectly fine, it boots fine on maybe 4-5 other machines (namely my older asus and my thinkpad), and it looks like this:
```

sudo fdisk /dev/sdc
Password or swipe finger: 

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sdc: 3980 MB, 3980394496 bytes
255 heads, 63 sectors/track, 483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e73ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          15      120456   83  Linux
/dev/sdc2              16         461     3582495   83  Linux

```
What is on your small first partition? And it is marked boot, while I guess your Ubuntu system is on your second partition.  Maybe this will confuse the boot process of the eeepc (?)

---

### Post by sudodus on 2012-11-28
> **svrkispm said:**
> One new discovery - 32 bit ubuntu 12.04 with kernel 3.2.0-x DOES boot.

I have tried very simillar kernel, but my system is 10.04 and 64 bit, and it DOESN'T boot - may this be the key?
This is a big step forward :-)

Maybe something in the eeepc is not truly 64 bits (I have only tried a 32 bit system on an eeepc that belongs to a friend). But it might also be some problem that is solved in the 12.04 version. After all, 12.04 is also an LTS version, and I am a happy user of it (mainly using lubuntu-desktop).

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2088658[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2088658")

---

### Post by svrkispm on 2012-11-28
Final solution:
Asus EEEPC 1015 CX has Intel Atom N2600. According to Intel, this CPU has 64 bit instruction set ([http://ark.intel.com/products/58916/Intel-Atom-Processor-N2600-1M-Cache-1_6-GHz?q=n2600#infosectionpackagespecifications](http://ark.intel.com/products/58916/Intel-Atom-Processor-N2600-1M-Cache-1_6-GHz?q=n2600#infosectionpackagespecifications)), but the N2600 CPU in eee pc does not have 64 bit instruction set, which is probably a bios issue.

I am returning this netbook and I suggest anyone to NOT BUY THIS.

---

### Post by svrkispm on 2012-11-28
> **sudodus said:**
> This is a big step forward :-)

Maybe something in the eeepc is not truly 64 bits (I have only tried a 32 bit system on an eeepc that belongs to a friend). But it might also be some problem that is solved in the 12.04 version. After all, 12.04 is also an LTS version, and I am a happy user of it (mainly using lubuntu-desktop).

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2088658[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2088658")

Yes, this was the case.Which is interesting, because I have maybe 15 pieces of older eeepcs in various configurations and this has never been an issue ...
Thanks a lot for Your help :)

---

### Post by sudodus on 2012-11-28
> **svrkispm said:**
> Yes, this was the case.Which is interesting, because I have maybe 15 pieces of older eeepcs in various configurations and this has never been an issue ...
Thanks a lot for Your help :)
You are welcome, and please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

