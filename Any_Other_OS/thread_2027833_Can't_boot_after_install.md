---
title: "Can't boot after install"
date: 2012-07-17
forum: Any Other OS
---

### Post by PsySc0rpi0n on 2012-07-17
Hi fellow linuxers...

I've installed a custom version of Ubuntu 10.04 (BT5) and everything went smoothly until the time to reboot...

When my system reboots, it hangs right after POST and my screen goes black and the mouse's cursor stays blinking for ever in the upper left corner of my screen...

what could be the problem? I've tryied over 3 times the install of this OS and this problem doesn't get solved...

Someone told me that could be the MBR (Master Boot Record).

What can i do to try to get this problem solved???

---

### Post by dino99 on 2012-07-17
maybe you should report/ask the maintainer of this "custom" release.

---

### Post by PsySc0rpi0n on 2012-07-17
> **dino99 said:**
> maybe you should report/ask the maintainer of this "custom" release.

It's an Ubuntu based release. It's BackTrack 5 R2.

So, probably if i try to install a "reference" version of Ubuntu probably i'm goig to get the same problem, right? 

> **bizworldusa said:**
> u must whether the drivers supported for ubuntu

thank u
[http://www.bizworldusa.com/](http://www.bizworldusa.com/)

Sorry nut i didn't quite understand your post...

My RIG is:
CPU: Intel E8400
MB: Asus P5K Pro
Video card: Sapphire HD 6870 Vapor-X and Sapphire X1950XT
HD 1: WD VelociRaptor 150Gb
HD 2: WD RaptorX 150Gb
HD 3: WD 1 TB

I think i don't have any hardware incompatible with Ubuntu/Linux

---

### Post by PsySc0rpi0n on 2012-07-18
I've tried to nreinstall Grub and when i write down this on the console

```
fdisk -l
```

the info on my 2 hard drives show up but in the drive that has no OS, has an asterisc under the "Boot" column...

What does this means?

And the hard drive where i've installed my OS has no asterisc in the "Boot" column.

---

### Post by Shadius on 2012-07-19
> **PsySc0rpi0n said:**
> I've tried to nreinstall Grub and when i write down this on the console

```
fdisk -l
```

the info on my 2 hard drives show up but in the drive that has no OS, has an asterisc under the "Boot" column...

What does this means?

And the hard drive where i've installed my OS has no asterisc in the "Boot" column.

I think that means it has a boot flag. I'm not sure though. Maybe someone else knows more.

---

### Post by oldfred on 2012-07-19
Moved to Other OS. as it is BT5.

From liveCD download and run this. Post link to BootInfo. 

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

An asterisk is the boot flag in a partition list. Grub does not use boot flag, but Windows has to have it on a primary partition to boot or repair the boot partition. Some BIOS will not let you boot at all without one on a primary partition, so you should have one just in case although it means nothing to grub. (Some other boot loaders also use it.)

---

