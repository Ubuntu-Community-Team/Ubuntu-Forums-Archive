---
title: "Trying to boot Lucid from GPT w/rEFIt (with / at 6th partition) on MBP 6,2"
date: 2010-08-27
forum: Apple Hardware Users
---

### Post by ivtz on 2010-08-27
Hi all,

I have a MacBook Pro 6,2 (got it June 2010) that I've set up to triple boot Mac OS X 10.6, Windows XP, and Lucid. Since Windows XP needs to be in the MBR, and since I wanted a "share" partition that all three OSes could access (meaning that it also had to be in the MBR), I created 5 new partitions (for a total of 7 altogether) and installed Ubuntu Lucid to partitions 5 (swap), 6 (/), and 7 (/home), with GRUB installed to partition 6.

Although installing Lucid seemed to work OK, I've been unable to boot it. The Linux option is available in the rEFIt boot menu, but the first time I tried it, the result was a black screen with "Error loading operating system" (or a similar message); ever since then, choosing the Linux option starts up Windows XP, presumably because XP installed itself in the MBR. (I installed XP first, then Lucid.)

I've wondered if installing GRUB to the MBR might help, but I'm reluctant to risk messing up a machine that currently works otherwise.

My questions for you all:

(1) Should it be possible to boot Lucid if it's entirely out of the MBR (that is, not in any of the first four partitions)? I thought it should be possible, given that GRUB2 is now standard, but I wasn't sure.

(2) If it is possible to boot Lucid this way, do you have any suggestions on what I can do to make it work?

(3) As you can see in the report below, the share partition (#3) has a Windows boot code, since I unsuccessfully tried to install Windows there at one point. Thus, there's now an extra Windows icon in the rEFIt boot menu. Do you have any suggestions on how to safely clear the boot code on that partition (and thus hopefully remove that extra icon from the rEFIt menu)?

Many thanks. I appreciate it a lot.

ivtz

Here's the report from rEFIt's Partition Inspector, with extra comments in square brackets:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    432050263  Mac OS X HFS+
 3      432314368    504313855  Basic Data
 4      504576000    553402367  Basic Data
 5      553402368    563167231  Linux Swap
 6      563167232    596367359  Basic Data
 7      596367360    625141759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    432050263  af  Mac OS X HFS+
 3      432314368    504313855  07  NTFS/HPFS
 4 *    504576000    553402367  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

[The mysterious EFI partition]
Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

[Mac OS X]
Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

[A data partition for all three OSes to share;
mistakenly has a boot code because of a previous
failed WinXP install to that partition]
Partition at LBA 432314368:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS

[Windows XP; currently marked with the boot flag, not sure why]
Partition at LBA 504576000:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active

[Ubuntu Swap]
Partition at LBA 553402368:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

[Ubuntu /]
Partition at LBA 563167232:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 6, type Basic Data

[Ubuntu /home]
Partition at LBA 596367360:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 7, type Basic Data
```

---

### Post by Sidolin on 2010-08-27
1+2: Yes this works but needs some tinkering to get it running. See [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

You need to start grub with efi not via the bios emulation.

---

### Post by srs5694 on 2010-08-28
Linux is perfectly happy to boot from GPT-only disks, or from GPT-only partitions on hybrid MBR disks. My personal experience with such configurations, however, is on BIOS-based commodity PCs, not Macs or other EFI-based systems. Thus, I can't offer any specific advice based on personal experience. I did, however, come across [this Web page](http://arunraghavan.net/2010/02/pure-efi-linux-boot-on-macbooks/) with some information on the topic. Perhaps it will give you some useful pointers.

If you can't seem to get it to work that way, you could use my [GPT fdisk](http://www.rodsbooks.com/gdisk/) to create a hybrid MBR that includes the Windows and Linux boot partitions rather than the Windows and OS X partitions. Note that some versions prior to 0.6.9 had a bug that caused improper hybrid MBRs to be created, so be sure to use 0.6.9 or later. (The last I checked, the version included in Ubuntu's APT repositories was 0.5.1 or thereabouts -- in other words, ancient!)

---

### Post by ivtz on 2010-08-28
Thanks for your quick replies. I've been looking at the TestingOnMacbook page, and it seems doable. It looks like the webpage that srs5694 linked to is based on similar information (related page on the same website). It makes sense that I'd need to boot GRUB using EFI and not BIOS emulation.

As mentioned in my first post, I'm relatively comfortable with doing things that add on to the current setup (such as adding another option in the rEFIt menu), but uncomfortable with trying things that make major changes to the current setup, especially changes that are either irreversible (well, irreversible unless I re-install everything) or hard to change back... I guess I'm sort of cowardly like that. :( If necessary, I can always wait until the next release and see if it has more built-in support.

I'll probably need to wait a day before I can try the instructions on the TestingOnMacbook page. I installed the i386 version of Lucid, btw. I'll need to check what version of the kernel was installed; it's presumably whatever version can be found on the Lucid LiveCD, assuming that the CD has only one version.

It looks like I have the same machine that was causing some issues on the thread [http://ubuntuforums.org/showthread.php?t=1557326&page=2](http://ubuntuforums.org/showthread.php?t=1557326&page=2) (such as the second post on the page) Speaking of which, from my Energy Saver preferences page, it looks like I can't choose a specific graphics card, just either allow for automatic graphics switching or enable high-performance graphics only regardless of power consumption.

I had a few questions on the instructions on the TestingOnMacbook page:

What is PC mode? Is it the same as BIOS emulation mode? How can I boot into it? It looks like it's needed to be able to get some video BIOS information. Is it possible to get that information if I boot using the LiveCD and chroot into my installation on the hard drive?

How do I set up the key mappings that the author talks about (towards the bottom of the page)?

Again, thanks for your help.

ivtz

---

