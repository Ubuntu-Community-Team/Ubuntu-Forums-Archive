---
title: "EFI boot vs BIOS on Macbook Pro?"
date: 2011-05-10
forum: Apple Hardware Users
---

### Post by deludrien on 2011-05-10
Hi,

I am getting a new Macbook Pro 2011 soon and I am trying to decide how I want to set up my dualboot OS X and Linux. I've been reading about it, but a lot of resources are fairly old and I'm looking for clarification on some things. I'm rather new to this, so please excuse my ignorance.

As I understand it, I have two options:

1. Create a hybrid MBR/GPT with Boot Camp or diskutil and boot with Apple's BIOS emulation layer thing.
2. Use grub-efi to boot from pure EFI.

Firstly, a lot of (older) guides recommend using rEFIt with the first option, but I've heard that rEFIt no longer works? Can I set up the hybrid MBR/GPT without rEFIt, and, if so, what problems will I encounter? Is it as simple as partitioning and just installing Ubuntu?

Secondly, does booting Ubuntu from EFI currently work well? Is grub-efi working properly? I read somewhere that there may be issues with graphics and a lack of 3d acceleration - is this still the case? Also, if I were to take this route, how would I start setting up a pure GPT EFI boot on my laptop? Are there basic, noob-friendly instructions somewhere? Do I still use Bootcamp/diskutil to partition? How do I prevent it from making a hybrid MBR/GPT partition scheme? How would I even install Ubuntu with grub-efi? Is a pure EFI boot currently better or worse than the former option?

---

### Post by srs5694 on 2011-05-10
You might want to check [this page](http://www.rodsbooks.com/ubuntu-efi/index.html) I wrote on EFI-booting Ubuntu 10.10, as well as my page on [hybrid MBRs.](http://www.rodsbooks.com/gdisk/hybrid.html) The two pages combined will answer a lot of your questions. You should also read [this forum post,](http://ubuntuforums.org/showthread.php?t=1743664) which describe an attempt to EFI-boot 11.04 that seems to have damaged the computer's firmware.

In an ideal world, I'd say that booting with EFI and without a hybrid MBR would be the best solution to a Linux/OS X dual boot. Linux handles a pure-GPT disk just fine, and as my page on the topic should make plain, my opinion of hybrid MBR's is extremely low; they're flaky and dangerous. Unfortunately, the state of support for EFI in Linux is rather low. Partly this is because of the very new state of GRUB's EFI support, but partly it's because distributions haven't really gotten their acts together on this score. Ubuntu 11.04 seems to be a vast improvement over 10.10 on this score, with the notable exception of the possibility of damaging at least some Macs' EFIs, if that report is accurate and reliable, rather than simply a weird fluke. If it were possible to boot Linux in BIOS mode on a Mac while using a conventional GPT, that would probably be the best compromise; however, AFAIK Apple's firmware uses a hybrid MBR (or a pure-MBR disk) as a trigger to activate the BIOS support, so AFAIK it's not possible to do this without having a hybrid MBR or regular MBR disk attached to the computer.

Oh, and as to rEFIt, it can be used with either pure-GPT or hybrid configurations, and with pure-EFI or EFI/BIOS boot modes. That is, rEFIt is not limited to hybrid MBR configurations, as you seem to believe. It's still a viable boot selector; it still works just fine. You could also use GRUB as your boot selector, if you prefer. (Either way, you'll need to use GRUB, since rEFIt can't boot a Linux kernel directly; it chain loads GRUB to get Linux booted.)

---

### Post by deludrien on 2011-05-10
Thanks for your help so far, that clears things up considerably.

Are Ubuntu's problems with EFI a problem with the Linux kernel itself, or unique to itself? Would other distributions of Linux, such as Debian, work better in EFI boot - and would your instructions on EFI-booting Ubuntu mostly apply to other distros?

Also, if I end up damaging my computer's firmware, would I be able to fix the problem myself by "reflashing" the firmware, as was mentioned in that topic?

---

### Post by srs5694 on 2011-05-11
The EFI-boot issues relate both to GRUB 2 (which is common across several distributions, although some distributions use other boot loaders) and to the installation scripts and specific configurations of Ubuntu (which obviously vary across distributions).

I've never tried an EFI installation of Debian, so I can't comment on it specifically. I have done an EFI installation of Fedora 14, but that was in VirtualBox, not on a Mac. I had more problems with Fedora 14 than I did with Ubuntu 11.04 in VirtualBox, but there may be Mac-specific issues that might reverse this on a Mac.

AFAIK, the Linux kernel works OK with EFI, although there are probably some lingering issues on at least some systems. It's conceivable that the damaged firmware issue was kernel-related; or that might have been a GRUB issue or a configuration issue. I just don't know enough about the precise cause of that firmware issue. I don't know if reflashing the firmware would permanently fix the problem or if it would recur on every boot, effectively forcing use of BIOS mode (or perhaps use of ELILO or some other boot loader).

Sorry I can't answer your questions more definitively. I'm afraid that Linux is (or at least Linux distributions are) just lagging behind in EFI support, leaving those who use it on the "bleeding edge." I'm experimenting with it myself, but there's clearly a lot of system-to-system variability.

---

### Post by deludrien on 2011-05-11
Assuming that the firmware does end up damaged, is it likely that I'll be able to reflash it and get rid of the EFI boot setup so that I can move to a hybrid MBR setup, or would I need to get a motherboard replacement?

---

### Post by srs5694 on 2011-05-11
[quote=deludrien]Assuming that the firmware does end up damaged, is it likely that I'll  be able to reflash it and get rid of the EFI boot setup so that I can  move to a hybrid MBR setup, or would I need to get a motherboard  replacement?[/quote]

I've presented the information I have, but it's scant. I cannot give you a simple answer to that question, since I don't know the answer.

---

### Post by dfacto on 2011-09-22
@srs5694 After reading your excellent EFI-Booting Ubuntu, I am wondering if you could talk a bit more about the the reasons behind having /boot partition?  You mention it isn't required but I am wondering what's the advantage of having it.  Typically I do not make a boot parition--any time I do have a problem, I merely boot a usb drive and chroot.  Another reason to NOT have it is to not have wasted space (128gb doesn't go far when OSX hogs 30-40gb!)  Are there any issues related to the fact that refit doesn't read ext4 (and this is currently my fs of choice--especially on SSDs).

Thanks!

---

### Post by srs5694 on 2011-09-22
> **dfacto said:**
> @srs5694 After reading your excellent EFI-Booting Ubuntu, I am wondering if you could talk a bit more about the the reasons behind having /boot partition?  You mention it isn't required but I am wondering what's the advantage of having it.

Most systems don't need a separate /boot partition; however, it's useful in some situations, such as:


[list]
[*]Older BIOSes had limits on how big a drive they could handle. These limits varied over time, and included (from memory) 504 MiB, ~128 GiB, and ~8GiB. Today there seeems to be a 2 TiB limit, but few people have exceeded it, and it may be more of a boot loader limit than a BIOS limit. In any event, if you've got a disk that's bigger than your BIOS or boot loader can handle, creating a separate /boot partition that's located below that limit can enable you to boot -- the BIOS and boot loader need only load the kernel and initial RAM disk from the /boot partition, whereupon the kernel takes over, and as it usually has less severe limits, the limits are sidestepped. All of this is less important with EFI-based boots, since EFI's limits are much higher than those of any BIOS.
[*]Some boot loaders, such as GRUB Legacy, can't read Linux LVM or RAID partitions. Thus, if you want to put your main installation in an LVM or RAID setup, you've got to have a separate /boot partition to store the kernel and initial RAM disk. GRUB 2 is supposed to be able to read Linux LVM and RAID volumes, so this shouldn't be an issue if you use GRUB 2. I've never tested this claim myself, though.
[*]In some situations, the device you want to use for your root (/) filesystem can't be read by the firmware. In this case, putting /boot on another disk that *can* be read by the firmware works around this problem. There was a recent thread here from somebody who was having problems like this, probably because the desired Linux root (/) partition was on an external disk with 4096-byte sectors that the computer's BIOS refused to boot.
[*]If /boot is on a separate partition, you can leave it unmounted most  of the time, thus protecting the kernel from accidental damage. OTOH,  this can cause kernel upgrades to go wrong if you forget to mount /boot  before doing the upgrade.
[/list]


There are probably other reasons, too, but these are the ones that spring to mind. As you can see, they mostly deal with working around firmware and/or boot loader limitations. In the case of my [EFI-Booting Ubuntu on a Mac](http://www.rodsbooks.com/ubuntu-efi/index.html) Web page, I was venturing into poorly-charted territory, and I thought that some methods of getting the system to work might work better if the /boot directory was readable by the firmware. Since most Linux filesystems are not readable by a Mac's EFI implementation, putting /boot on a separate partition seemed like it might be useful -- then I could use HFS+ on it. It turned out that these last-resort boot methods were *not* necessary, so I didn't end up needing a separate /boot partition, but I had one anyhow, so I wrote up the Web page with it in place.

> Typically I do not make a boot parition--any time I do have a problem, I merely boot a usb drive and chroot.  Another reason to NOT have it is to not have wasted space (128gb doesn't go far when OSX hogs 30-40gb!)  Are there any issues related to the fact that refit doesn't read ext4 (and this is currently my fs of choice--especially on SSDs).

A /boot partition can be quite small -- I normally create them at about 200 MiB -- so the space issue isn't a big deal, even on a smallish hard disk.

GRUB 2 can read most or all Linux filesystems, so if you use GRUB 2, there's no problem with putting the /boot directory on the Linux root (/) partition as ext4fs. If you want to try ELILO, though, it needs to be able to read your kernel file through the EFI, so your kernel would have to be on a FAT or HFS+ partition. The usual approach with ELILO is to copy the kernel (and the initial RAM disk) to the EFI System Partition (ESP), which is normally 200 MiB on a Mac. That's plenty big enough to house several kernels and initial RAM disks, so it's not really a problem. An alternative might be to convert /boot to HFS+ and have ELILO read the kernel from there; however, I've not gotten ELILO to work correctly on my 32-bit Mac Mini. I don't know if that's because of its 32-bit nature or because of the Mac's EFI 1.x implementation, though.

---

### Post by dfacto on 2011-09-22
Great! Thorough as always--thanks again!

---

