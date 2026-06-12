---
title: "Full reinstallation in iMac partition"
date: 2010-11-09
forum: Apple Hardware Users
---

### Post by rmcellig on 2010-11-09
I have Ubuntu 10.10 installed in a partition on my iMac. OS X is in the other partition. Let's say I want to reinstall a clean copy of Ubuntu, do I just restart from the Ubuntu live CD and install it into the Ubuntu partition?

---

### Post by linuxopjemac on 2010-11-09
yes, that's the way to go. I would not install GRUB again though. It should be working fine as it is.

---

### Post by rmcellig on 2010-11-09
So I just boot from the Ubuntu live CD and go through the usual installer procedure, and just select the Ubuntu partition I created to install on?

That's pretty straight forward! Thanks!!!

---

### Post by lael on 2010-11-09
> **rmcellig said:**
> I have Ubuntu 10.10 installed in a partition on my iMac. OS X is in the other partition. Let's say I want to reinstall a clean copy of Ubuntu, do I just restart from the Ubuntu live CD and install it into the Ubuntu partition?

This is what I did when I upgraded from 10.04 to 10.10.  I had a very similar partition scheme.  I first backed up the first few partitions and stashed them on an external drive (with dd).  I also got the MBR and a list of parition sizes, UUIDs, etc.

I left my efi /dev/sda1 and OSX /dev/sda2 alone and recreated my /boot / and swap partitions. 

It went well and did what I expected. YMMV

Actually, I found that after doing it this way I found that my grub/boot partition didn't have the EFI flag on it and it made rEFIt go *way* faster

---

### Post by rmcellig on 2010-11-09
Thanks Lael!

So, step by step, how should I proceed with all of this? Details please. I have a screen shot in my first post of my partition scheme. I want to make this as straight forward as possible. Thanks again!!!! It would be great to have EFI faster because not I have to wait a while for it to load.

---

### Post by srs5694 on 2010-11-09
> **lael said:**
> Actually, I found that after doing it this way I found that my grub/boot partition didn't have the EFI flag on it and it made rEFIt go *way* faster

What GParted identifies as an "EFI flag" is actually a partition type code of C12A7328-F81F-11D2-BA4B-00A0C93EC93B, which identifies an EFI System Partition. It's flat-out wrong for a Linux /boot partition to have such a partition type code, if that's what you mean by "grub/boot partition." The EFI System Partition should have a FAT32 filesystem on it and it should contain certain drivers and boot loader files as defined by the EFI specification. If it has a Linux filesystem, it's entirely possible that the EFI was getting confused and running around in loops, thus causing a delay in booting the system.

For more information on this, you can download the EFI specification from [Intel's EFI page;](http://www.intel.com/technology/efi/) or for a shorter introduction, read Apple's [Technical Note TN2166.](http://developer.apple.com/library/mac/#technotes/tn2006/tn2166.html)

On a broader note, I'm experimenting with pure-GPT configurations that involve booting Linux via EFI-only tools rather than the BIOS-based tools that are commonly recommended. This requires jumping through some hoops to set up, but it gives the advantage of doing away with the ugly and dangerous [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) that's usually required. (OTOH, a hybrid MBR and BIOS-based booting is still required to boot Windows, so this approach is most useful if you *don't* want to boot Windows.) In brief, this can be done by downloading [Super GRUB 2 Disk](http://www.supergrubdisk.org/) for temporary booting, installing Linux, reverting the hybrid MBR to a conventional pure-GPT setup by using GPT fdisk (gdisk) to rewrite a "clean" protective MBR, booting with Super GRUB 2 Disk, removing grub-pc, installing grub-efi, and tweaking the GRUB configuration (it referenced the wrong partitions when I tried it).

I plan to work out the kinks in my installation procedure and write it up, but I'm busy with various other things at the moment, so it may be a while before I can get to it. IMHO, doing away with BIOS booting and hybrid MBRs is the way to go if you don't need to boot Windows on a Mac.

---

### Post by lael on 2010-11-09
> **srs5694 said:**
> What GParted identifies as an "EFI flag" is actually a partition type code of C12A7328-F81F-11D2-BA4B-00A0C93EC93B, which identifies an EFI System Partition. It's flat-out wrong for a Linux /boot partition to have such a partition type code, if that's what you mean by "grub/boot partition." The EFI System Partition should have a FAT32 filesystem on it and it should contain certain drivers and boot loader files as defined by the EFI specification. If it has a Linux filesystem, it's entirely possible that the EFI was getting confused and running around in loops, thus causing a delay in booting the system.

Basically, when I did the Ubuntu Install with 10.04 rEFIt would take forever and basically just using the 10.04 installer it left disk looking like: 
```
$ sudo gdisk -l /dev/sda
...
Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       115752999   55.0 GiB    AF00  Customer
   3       115755008       115757055   1024.0 KiB  **EF02**  
   4       115757056       942163967   394.1 GiB   0700  
   5       959626710       977089364   8.3 GiB     8200  
```

but now it looks more like:
```
$ sudo gdisk -l /dev/sda
...
Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI system partition
   2          409640       115752999   55.0 GiB    AF00  Customer
   3       115755008       115947519   94.0 MiB    0700  
   4       961476608       977104895   7.5 GiB     8200  
   5       115947520       961476607   403.2 GiB   0700
```

> **srs5694 said:**
> 
I plan to work out the kinks in my installation procedure and write it up, but I'm busy with various other things at the moment, so it may be a while before I can get to it. IMHO, doing away with BIOS booting and hybrid MBRs is the way to go if you don't need to boot Windows on a Mac.

Awesome, I've been sick of the Double EFI bootloaders!  Please do a writeup!

---

### Post by rmcellig on 2010-11-09
I have my installation window open and am not sure how to proceed. Please advise. Attached is an error I receive when trying to install. I had to take two screenshots of the install window because the window does not expand.

When installing, should I choose 

1. Install along side other operating system

2. Erase and use Entire disk

3. Specify partitions manually

You will see that my current Ubuntu partition is /dev/sda3. Do I have to reformat it in order to install a clean copy of Ubuntu?

My Mac partition is /dev/sda2

The swap files are /dev/sda5. 

If possible, I would like a quick replay because I am stuck on this screen and need to get some work done. Thanks!!!!

---

### Post by srs5694 on 2010-11-09
Lael,

It looks like the BIOS Boot Partition (which gdisk identifies as having a type code of EF02) may have been confusing something in the boot process; or perhaps a change to the filesystem on one of the partitions has done that. (The gdisk program doesn't read inside partitions to identify filesystems, unlike libparted-based tools.)

Rmcellig,

If I understand correctly, you want to completely wipe out any Linux installation you've got and re-install from scratch. If so, I recommend you select the manual partitioning option, and then select the ext4 Linux partition (/dev/sda3 in your screen shot), click the Change button, and assign it a mount point of "/". (I don't recall the precise details of the dialog box you get when you do this, so I can't give you click-by-click instructions on this.) You should then be able to proceed with the installation. If you need to preserve some data from your old Linux installation, you should back it up first, or perhaps select some other option; post back with details of what you want to keep for further advice.

This will, however, set up Linux with a hybrid MBR and a BIOS-style boot loader. My previous post to this thread outlines one possible way to go from there to a pure EFI/GPT boot process; however, I don't have a more precise writeup just yet. (Even when I work it out, it may need tweaking for different Mac models. I've got a Mac Mini 1,1, FWIW.)

---

### Post by linuxopjemac on 2010-11-10
> On a broader note, I'm experimenting with pure-GPT configurations that involve booting Linux via EFI-only tools rather than the BIOS-based tools that are commonly recommended. This requires jumping through some hoops to set up, but it gives the advantage of doing away with the ugly and dangerous hybrid MBR that's usually required. (OTOH, a hybrid MBR and BIOS-based booting is still required to boot Windows, so this approach is most useful if you don't want to boot Windows.) In brief, this can be done by downloading Super GRUB 2 Disk for temporary booting, installing Linux, reverting the hybrid MBR to a conventional pure-GPT setup by using GPT fdisk (gdisk) to rewrite a "clean" protective MBR, booting with Super GRUB 2 Disk, removing grub-pc, installing grub-efi, and tweaking the GRUB configuration (it referenced the wrong partitions when I tried it).

I plan to work out the kinks in my installation procedure and write it up, but I'm busy with various other things at the moment, so it may be a while before I can get to it. IMHO, doing away with BIOS booting and hybrid MBRs is the way to go if you don't need to boot Windows on a Mac.

This sounds very interesting to me. Can you post your results here? I might want to publish an article dedicated to this.

---

### Post by rmcellig on 2010-11-10
Thanks srs5694! I just want to install a clean copy of Ubuntu because I can't find a way to uninstall Ubuntu Elementary. I also have a ton of applications I installed that I now don't need. Is there a way to bring Ubuntu back to it's original state without having to reinstall a clean copy?

I don't really need to back up anything from my current install of Ubuntu. If I need to back up I guess I could use Clonezilla?

Another reason I want o do a clean install is because I can't get the iMac webcam working or the audio in from the sound preferences (this one is the most important for me because that is what I need to do most. I record radio shows from my attached radio.

---

### Post by srs5694 on 2010-11-10
I don't know of a way to restore a Linux system to its newly-installed state short of re-installing it or restoring it from a backup made at that time. If you think you might need to do this, though, you could install using Btrfs or an LVM and use the "snapshot" feature to take a snapshot immediately after installation. This will consume more and more disk space as time goes on, though. If you do this, I strongly recommend keeping a separate /home partition, since otherwise any reversion you do will wipe out all your user file changes, in addition to the system file changes.

---

### Post by rmcellig on 2010-11-10
I would like to report that I successfully reinstalled Ubuntu 10.10 in my iMac partition. Went well and pretty straight forward. Thanks for all of your help!!!

---

