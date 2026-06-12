---
title: "Ubuntu on a portable hard drive?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2007-10-04
Is there a way to install Ubuntu (with GRUB) all onto an external HDD, so that I can keep it completely seperate from the main Windows partition on a family laptop?

Thanks in advance for any replies.

---

### Post by overdrank on 2007-10-04
> **Mazza558 said:**
> Is there a way to install Ubuntu (with GRUB) all onto an external HDD, so that I can keep it completely seperate from the main Windows partition on a family laptop?

Thanks in advance for any replies.

Hi and there is some good info here
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
good luck!

---

### Post by Mazza558 on 2007-10-04
Hmm.. There's nothing on there that tells you how to install onto a USB drive, only info about if you can't boot into the drive.

---

### Post by Colro on 2007-10-04
If your laptop is able to boot from a USB (test this beforehand, some can't), simply make it the 1st priority boot drive in your BIOS and install Ubuntu onto it like a normal installation. When it's plugged in Ubuntu should boot, when it isn't windows will pop up. If you have never installed Ubuntu before, I'd recommend unplugging your normal harddrive when you install just as a precaution, although it isn't required.

---

### Post by benerivo on 2007-10-04
I'd do it the way Colro suggested, but if you leave the drive in, then make sure the bootloader is put on the usb drive and not on the internal one. See [here]("http://img519.imageshack.us/my.php?image=feistydual18cv5.png") for when to set this during installation. In this screenshot (hd0) is this persons hda drive. If he wanted to put it on his hdb drive (his second hard drive) he would change this to (hd1).

---

### Post by overdrank on 2007-10-04
> **Mazza558 said:**
> Hmm.. There's nothing on there that tells you how to install onto a USB drive, only info about if you can't boot into the drive.

Hi and this page
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
Is linked in the page I posted earlier under 
Installing on external or RAID hard disks

If you would like to install Ubuntu on an external hard disk or a RAID array, see the guides below for instructions.
      BootFromFirewireHardDisk - Booting Linux from a Firewire hard disk.
    *

      BootFromUSB - Booting an Ubuntu system on a USB hard disk on computers which cannot boot from USB (using a boot CD).
    *

      [Ubuntu]LiveUsbPendrivePersistent - Installing Ubuntu or Kubuntu on a USB pendrive with persistent mode.
    *
      Installation/LVMOnRaid - Installing onto a Software RAID Array, with all partitions on RAID and LVM (including root and boot).
    *
      FakeRaidHowto - Installing onto a BIOS RAID array.
    *
      How to dual-boot Ubuntu and XP after installing them separately on two HDs - If you really want to keep XP and Ubuntu on separate hard drives.

---

