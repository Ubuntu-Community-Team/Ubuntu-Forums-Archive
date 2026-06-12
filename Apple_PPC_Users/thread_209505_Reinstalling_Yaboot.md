---
title: "Reinstalling Yaboot"
date: 2006-07-05
forum: Apple PPC Users
---

### Post by applemacmad on 2006-07-05
HI,

I am fairly new to Linux, so this is over my head! Since I installed Ubuntu, I have installed Mac on a separate partition, and it appears to have overwritten the Ubuntu boot loader, so the only way to boot linux is to hold down option and put in password etc...
How can I reinstall the bootload to gain easy access to Mac _and_ Linux?

---

### Post by xurios on 2006-07-05
if you can still boot into linux by holding down option, then your yaboot-boot loader is probaly still intact. You can do a couple of things to find out what's going on: From os x, in Terminal

```
diskutil list /
```will give you a list of all the paritions on your root device (your mac hd). If you still have more than one Apple_Bootstrap partition, than one is likely to be the yaboot partition and you're good to go. You just need to write to the boot-device variable in nvram to boot from the yaboot-boot loader instead of your os x boot loader.

You can look in your /etc/yaboot.conf file from the linux side to see which partition yaboot is on. Post again if you get stuck.

---

### Post by applemacmad on 2006-07-05
The Yaboot partition appears to be /dev/hda2, but there are only two options in yaboot, for linux and CD.
So firstly, how do I make my laptop always boot into yaboot, and secondly how do I make yaboot include mac?

---

### Post by xurios on 2006-07-05
Could you post your yaboot.conf? Also, have you read the yaboot.conf manual? Did yaboot previously give you the os x option, before you installed os x on a separate partition?

---

### Post by linear on 2006-07-05
This may have some useful information: [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot")

---

### Post by applemacmad on 2006-07-05
When I installed Ubuntu, my Mac partition was empty, so the original Yaboot came up with Linux and Cd options. Since I have installed Mac, I need to press option etc to get to Yaboot, where I am given the same options. Here is my yaboot.conf

> 
boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=4
root=/dev/hda4
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux


---

### Post by linear on 2006-07-05
I think you need to add:

**macosx=/dev/hdaX**, where X is the number of your OS X partition. (In mine, it's the line after "enablecdboot".)

After saving yaboot.conf, you then need to run **sudo ybin -v**.

---

### Post by applemacmad on 2006-07-06
Thanks, that worked perfectly

---

