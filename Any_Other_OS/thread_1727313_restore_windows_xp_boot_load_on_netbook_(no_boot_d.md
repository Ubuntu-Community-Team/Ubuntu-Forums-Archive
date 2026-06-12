---
title: "restore windows xp boot load on netbook (no boot disk)"
date: 2011-04-12
forum: Any Other OS
---

### Post by senor_cardgage on 2011-04-12
I've found a lot of similar problems solved by using a win xp boot disk, but unfortunately since I'm using an Asus EeePC 1005HA that came loaded with xp and no cd drive, that's not an option for me (nor do I possess a disk). There should still be an xp recovery partition on my hdd, but I'm not sure I can boot into it.

Here's the run-down. I'm a beginner when it comes to linux/ubuntu, but a few times a year I'll get excited about trying a new distro or tweaking what I've got and I'll do a bunch of reading and messing around with booting different os's on my netbook. I've always kept XP safe as my primary os and used that for school and work, and dual booted different flavors of linux.

Yesterday, I thought I'd try out Joli OS, and wanted to wipe my old ubuntu install that I didn't really use any more. Without thinking too much of it, I went ahead with gparted and deleted my ubuntu partitions and merged them with my xp partition, after which I was going to go ahead with starting from scratch again. I realized pretty quickly that I should have thought that through a bit more clearly, as I rebooted and got this:

error: no such partition.
grub rescue>

I know that this is the logical outcome of me completely removing the partitions that GRUB is supposed to be looking for, but I don't know if there is a way around it. I'm going to try setting up a usb stick with ubuntu and booting from that to see if I can get a little control back and maybe eliminate GRUB completely and restore the boot loader for XP. However, I'm not really sure how I should be going about this and am looking for a little direction.

Apologies if I missed the thread that answers this elsewhere, but I did try to do my homework beforehand. Thanks for any and all help!

---

### Post by wilee-nilee on 2011-04-12
To much personal information, just the facts please.;)

So you have a unbootable XP because you removed the Grub bootloader by removing Ubuntu. The MBR=the first 512mb of the hard drive has part of the grub bootloader there but the rest is gone it was in Ubuntu. 

You can load a XP install disc onto a thumb easily in windows. 

You can go buy a external cd/dvd/ reader to boot a XP disc and run fixmbr in the MS terminal and have XP. 

You can boot a Ubuntu thumb and install lilo and have XP back as well. 

You can reload and install another OS with a bootloader that will pick up XP and be fixed what do you really want?

---

### Post by senor_cardgage on 2011-04-12
Apologies, I tend to be too wordy (with most things in my life). I will stick to the facts from here on out.

My optimum solution would be to get back to just XP and eliminate GRUB (without deleting or reformatting my current XP partition, which I don't think is necessarily at risk here but thought I should mention).

I am hoping to use a thumb drive, with either an XP install disc or bootable ubuntu, to get it back.

I may get the linux bug again and want to dual boot later down the road, but right now I'd love to get back to just a clean XP boot.

---

### Post by wilee-nilee on 2011-04-12
> **senor_cardgage said:**
> Apologies, I tend to be too wordy (with most things in my life). I will stick to the facts from here on out.

My optimum solution would be to get back to just XP and eliminate GRUB (without deleting or reformatting my current XP partition, which I don't think is necessarily at risk here but thought I should mention).

I am hoping to use a thumb drive, with either an XP install disc or bootable ubuntu, to get it back.

I may get the linux bug again and want to dual boot later down the road, but right now I'd love to get back to just a clean XP boot.

You can use the lilo bootloader from a Ubuntu live cd follow these directions to install. Boot the live cd edit the menu to show software resources in admin open the software sources and in the 1st tab 2nd or 3rd line tick the universe repo on, then run update grub in the terminal, then run these two commands, assuming that you have one HD=sda. Run in the terminal this command to see how your hd is showing from the booted ubuntu.
```
sudo fdisk -l
```
we are trying to confirm the first 3 letters of the hd here no numbers.

Restore basic windows boot loader - universe enabled
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```

---

### Post by senor_cardgage on 2011-04-12
Thanks for the help. I had a little trouble that slowed me down from running ubuntu smoothly off the usb drive (hardware drivers mostly, couldn't use my trackpad and wi-fi), so I ended up reinstalling ubuntu and I'm just back to where I was yesterday, no problem, and I can go ahead from here.

Thanks again.

---

