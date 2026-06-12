---
title: "Macbook 8,1 - Natty / grub 2 does not install"
date: 2011-06-20
forum: Apple Hardware Users
---

### Post by joost1123 on 2011-06-20
Hi everyone,

I am able to install 11.04 (64bit) on my MBP, but after installation I cannot boot into it.

On [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) I can find:

> This information will not work for iMac (11,1) users installing recent versions of Ubuntu (e.g., Maverick). The presence of the bios-grub partition that the Ubuntu installer creates by default (e.g., sda3) causes a conflict that prevents syncing the GPT and MBR partition tables. Deleting sda3 does not help since grub2 requires that bios-grub partition, nor will it use either sda or sda4 aborting with the error: "This GPT partition table has no BIOS boot partition; embedding won't be possible!". So installing Ubuntu with the bios-grub partition fails and installing without it fails. See "Single-Boot".

And this seems to be the problem, as trying to re-install grub from the live-cd results in that error message. Looking at this forum there are a lot of people running ubuntu on the same laptop, so my question is: **How??**

I've tried installing ubuntu 10.10 and 10.04 LTS but they have the same problem. :(

Thanks.

---

### Post by srs5694 on 2011-06-20
First, the gptsync utility (or other methods of "syncing" disks on Macs) creates a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) I recommend you read up on this topic. Hybrid MBRs are dangerous hacks, and if you don't understand them, you're opening yourself up for a world of pain by using them. If you don't care to take the time to understand them, then don't use them. Either don't install Windows or Linux on a Mac, or learn how to do it without using a hybrid MBR. (That's difficult or impossible for Windows, but it can be done for Linux by using EFI booting rather than BIOS booting.)

Second, it sounds like the issue is that gptsync is putting the wrong partitions in the hybrid MBR. This is easily corrected by using a more flexible tool. There are versions of gptsync that will do the job, although the most common binaries aren't so flexible. Alternatively, you can use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to do it.

Finally, if you care to do it with a standard GPT rather than the dangerous hacked hybrid MBR, see [this page](http://www.rodsbooks.com/ubuntu-efi/index.html) I wrote on the topic. It's a bit dated, since it covers Ubuntu 10.10. Things are a bit better with 11.04, at least in theory. Unfortunately, as noted on that page, some Macs have firmware that can be damaged by an Ubuntu installation in EFI mode. (I saw a reference that it was the efibootmgr tool that does the damage, but I haven't looked into it in detail.)

---

### Post by YesWeCan on 2011-06-20
@srs5694 Out of interest, is it not possible to install Grub to the Ubuntu partition and boot it by normal means? Excepting the potential core.img sector addressing problem that Grub might have at some point.

And this sector address issue is caused by the location of core.img being changed. Is there a standard filesystem type that is not prone to this, or is less prone, that one could create a boot partition with, with grub MBR in its PBR?

---

### Post by srs5694 on 2011-06-20
YesWeCan,

It is at least theoretically possible to install GRUB 2 to the PBR of a partition; however, sometimes it won't do to this because of the block list issue. That's not the issue here, though; the issue is the convoluted installation and booting methods that are common on Macs because of Apple's "wisdom" in using limited and dangerous hybrid MBRs rather than finding some other way to get Windows to boot on their machines, and on the Ubuntu developers relying on this same technique to get Ubuntu to install on Macs. Linux *can* be installed and booted using EFI tools on Macs, although there are advantages and disadvantages to this approach.

---

### Post by joost1123 on 2011-06-20
You are my hero!

> **srs5694 said:**
> Second, it sounds like the issue is that gptsync is putting the wrong partitions in the hybrid MBR. This is easily corrected by using a more flexible tool. There are versions of gptsync that will do the job, although the most common binaries aren't so flexible. Alternatively, you can use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to do it.[..]

There was a problem with my Hybrid MBR. I first tried creating a new Hybdrid MBR with gdisk (in the recovery menu), but for some reason Refit thought that new MBR was invalid and refused to use it. I then completely reset the MBR with gdisk (thus, making the whole disk protected, as is the default case on Macs). Now I could use Refits gptsync tool to sync the disk again, and voila! I can now boot into Ubuntu. 

So, for some reason previous Linux'es messed with my MBR, which caused Refit to be unable to sync correctly.

---

### Post by YesWeCan on 2011-06-20
> **srs5694 said:**
> YesWeCan,

It is at least theoretically possible to install GRUB 2 to the PBR of a partition; however, sometimes it won't do to this because of the block list issue. That's not the issue here, though; the issue is the convoluted installation and booting methods that are common on Macs because of Apple's "wisdom" in using limited and dangerous hybrid MBRs rather than finding some other way to get Windows to boot on their machines, and on the Ubuntu developers relying on this same technique to get Ubuntu to install on Macs. Linux *can* be installed and booted using EFI tools on Macs, although there are advantages and disadvantages to this approach.
Thanks. Your web page about hybrid MBRs is most interesting.

---

