---
title: "Help with triple-boot partitioning on MacBook Pro"
date: 2010-04-18
forum: Apple Hardware Users
---

### Post by Jonathan Swift on 2010-04-18
Greetings Earthlings.  I have installed all the operating systems for a triple-boot first generation MacBook Pro (Core Duo 32-bit, not Core 2 Duo 64-bit).  The problem I've got is that my partitioning for Ubuntu screwed up my Windows XP boot.  I have a basic idea of what is wrong, but hestitate to fix it until I am sure of what I am doing.

I did know that after adding my Ubuntu partitions, I needed to edit WinXP's C:\boot.ini, but I think I need more than that.

The problem is that Windows XP needs to be one of the partitions in the Master Boot Record's partition table; there can be up to four such partitions.  Any additional partitions in the older MBR style of partitioning have to be logical partitions within an extended partition.

What seems to have happened is that when I used the OS X Disk Utility to divide my OS X partition into a bunch of smaller partitions for Ubuntu's use, the Windows XP partition is no longer one of my MBR partitions.

It *is* one of my GUID Partition Table (GPT) partitions, but my understanding is that WinXP doesn't know how to boot from GPTs - it can only use MBR.

So here is what I need to know: is there a way I can rearrange my partition specifications so that my WinXP partition will be found in my MBR, without deleting any of my existing data?

I set up Ubuntu to have separate /boot, root, swap and /home partitions.  I also created two extra partitions that will be shared among all my operating systems.  Here is what my GPT partition map looks like:

1 fat32 EFI System Partition
2 hfsx Mac OS X
3 ext2 /boot
4 ext4 /
5 swap
6 unused
7 ext4 /home
8 unused
9 nfts Windows XP

If I use fdisk, it shows the partition map as specified by my MBR:

1 ee GTP
2 af HFS / HFS+
3 83 Linux
4 83 Linux

So you see my NTFS partition is no longer included in my MBR partition table.

When I boot from rEFIt, I get the Grub menu, which offers Windows XP as an option.  When I select it, the Windows boot loader runs for a little while, then I get a blue screen followed very quickly by a reboot.

Thank you for any advice you can give me.

---

### Post by srs5694 on 2010-04-18
> **Jonathan Swift said:**
> Greetings Earthlings.  I have installed all the operating systems for a triple-boot first generation MacBook Pro (Core Duo 32-bit, not Core 2 Duo 64-bit).
...
The problem is that Windows XP needs to be one of the partitions in the Master Boot Record's partition table; there can be up to four such partitions.  Any additional partitions in the older MBR style of partitioning have to be logical partitions within an extended partition.

***Nononononononononono!!!!!!!***

Do *not,* ***under any circumstances,*** create an extended partition to hold logical partitions on a hybrid MBR disk!!!!!!!! To understand why, you need a pretty complete understanding of MBR, GPT, and hybrid MBRs. The short explanation is that such a configuration is an invitation to future disasters because of the fact that logical partitions require unallocated space between partitions to hold the partition definitions. AFAIK no GPT disk utilities will take that into consideration or know how to sync MBR logical and GPT partitions, and MBR partition editors usually don't understand the GPT side, making all sorts of inconsistencies likely when partitions are changed.

In case you're wondering about my vehemence on this point, please understand that I wrote [GPT fdisk,](http://www.rodsbooks.com/gdisk/) one of just a few utilities that can create hybrid MBRs. I understand the data structures involved, so I know the risks. Although such a configuration could be made to work in the short term, you'd be risking data corruption whenever you attempted to modify it. If anybody has written software to do it, that program's author is a menace. Sorry if I sound extreme on this point; but the mere thought of trying to support such a configuration in GPT fdisk gives me heart palpitations.

> What seems to have happened is that when I used the OS X Disk Utility to divide my OS X partition into a bunch of smaller partitions for Ubuntu's use, the Windows XP partition is no longer one of my MBR partitions.

It *is* one of my GUID Partition Table (GPT) partitions, but my understanding is that WinXP doesn't know how to boot from GPTs - it can only use MBR.

Correct -- at least on BIOS-based systems. My understanding is that Apple's Boot Camp emulates BIOS, so you're stuck with those limitations when using Boot Camp, too.

> So here is what I need to know: is there a way I can rearrange my partition specifications so that my WinXP partition will be found in my MBR, without deleting any of my existing data?

Yes. You can have up to three primary MBR partitions, and they can be any partitions you like. (I recommend putting all the hybrid MBR partitions at the end of the disk, if possible, for reasons described on my [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) page.) To do this, you must use a tool that's flexible enough to let you specify which GPT partitions to include in the hybrid MBR. To the best of my knowledge, only my own GPT fdisk or [a modified gptsync](http://www.insanelymac.com/forum/index.php?showtopic=177505) will do the job.

---

### Post by m.prebble on 2010-08-02
Hi, I had a very similar problem. Having installed Windows first, I then tried to install Ubuntu (which worked fine) but Windows stopped with BSOD. So I just deleted the XP partition and lived without it :) 

I'm hoping someone can help or advise with another partitioning problem though, heres the scenario. 

- The HDD on my MBP suffered failure and as the machine was under warranty it was sent to Apple for repairs. Before doing so, I took out the HDD and copied my Linux partition to an external HDD using gparted (from a LiveCD). I then mounted the HSF partition and managed (albeit slowly) to backup my MacOSX data.

- Machine arrives back, new HDD.
- I install reFit and resize the HSF+ to make room for Ubuntu, swap and XP respectively. (Note: Bootcamp assistant was not used)
- I copy (again using gparted) the linux ext4 from the external HDD to sda
- After rebooting, reFit identifies there is a linux OS, but when I try to boot from it, a flashing cursor appears up the top of the screen and the machine has to be hard reset.

I have tried the excellent tutorial at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and various others to reload Grub (including the chroot technique). This fails saying that BIOS Compatibility mode is not enabled or something (can provide more comprehensive messages if rqd) 

After having the Ubuntu set up how I like it, I don't really want to have to re-install it ... Can anyone advise what I may be doing wrong? (or have done wrong)

Partition order is: 

EFI     /dev/sda1
HSF+ /dev/sda2
ext4  /dev/sda3
swap /dev/sda4
ntfs   /dev/sda5 (empty)

On a sidenote, if I were to purchase a bigger disk in the future, can gparted be used to transfer these partitions (and grow them) and everything still work if the partition order is maintained?

Thanks in advance,

---

