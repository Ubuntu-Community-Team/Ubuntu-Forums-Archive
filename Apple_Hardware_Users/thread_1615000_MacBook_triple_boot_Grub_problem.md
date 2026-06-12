---
title: "MacBook triple boot Grub problem"
date: 2010-11-06
forum: Apple Hardware Users
---

### Post by Jamou on 2010-11-06
Hi guys,

I'm a new user here and I've decided to make my unibody MacBook triple boot: OSX 10.6, Windows 7 and Ubuntu 10.10

So I've installed OS X first, then I've install rEFIt. After that I've partionned my disk in 4 partitions, OSX, WINDOWS, UBUNTU, UBUNTUSWAP. Then I installed windows and then installed Ubuntu. Long story short, it worked fine. The only thing is, on the rEFIt menu, whenever I choose to boot Linux or Windows I get to the Grub menu, in which I can choose Ubuntu or Windows 7 if I want. How can I fix that ? I'd like to boot directly on Windows or Ubuntu without passing by the Grub.

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    262549087  Mac OS X HFS+
 3      262811648    420526079  Basic Data
 4      420526080    480583679  Basic Data
 5      480583680    488396799  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    262549087  af  Mac OS X HFS+
 3 *    262811648    420526079  07  NTFS/HPFS
 4      420526080    480583679  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 262811648:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS, active

Partition at LBA 420526080:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 480583680:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap
```



> hen you run it, it looks at the partitions and file systems on the first hard disk, and generates a report. You are affected if the report contains something like this:

MBR contents:
 Boot Code: GRUB

To fix this problem, you need to install GRUB / LILO in the boot sector of your Linux partition instead, then remove it from the MBR. I’m not aware of a ready-made tool that can safely do that removal. Please ask for help on a Linux forum if needed.

I'm far from being a Ubuntu Guru, in fact, I've start using Ubuntu today. Is there an easy to fix my stuff ? :)

Thanks for any response!

---

### Post by srs5694 on 2010-11-06
I'm not positive, but my impression is that rEFIt can't boot Linux directly; it *must* use GRUB (or some other Linux-capable boot loader) to boot Linux. That said, you can reduce the GRUB timeout value so that it only appears on the screen for a second or so. Change the default in /etc/default/grub (it's the GRUB_TIMEOUT value), then type "sudo update-grub" to have it take effect.

---

### Post by vincebs on 2010-11-06
I have the same problem. Mac OS X boots up directly from rEFIt but both the Linux and Windows options go to the same GRUB menu. I don't mind Linux going into GRUB, but rEFIt should be able to boot Windows directly.

---

### Post by Jamou on 2010-11-07
> That said, you can reduce the GRUB timeout value so that it only appears on the screen for a second or so. 

But if I do so, I won't be able to boot my Windows 7 partition at all, since I need to select it through the GRUB menu. :(

---

### Post by Jamou on 2010-11-15
Has anyone found something ?

---

### Post by willnight on 2010-11-15
- refit should be able to see all 3 platforms on start-up.

- when reducing grub timeout in ubuntu to 0, make sure default is set to boot ubuntu. that way, when you choose ubuntu from refit, it *seems* like you're going straight into ubuntu and bypassing grub, but in fact, you did go thru grub. just a bit of booting sleight-of-hand :-P


it works for me.

---

### Post by Talsian on 2012-12-02
This is an old topic, but a Google search for this issue turned up this thread as the top result, so answering it may help others who have the same issue.

Fire up the command line in OS X and put in the following to fix your MBR.

sudo fdisk -u /dev/disk0

---

### Post by trogdor1138 on 2012-12-05
Holy resurrected thread, Batman! ;-)

> **Talsian said:**
> Fire up the command line in OS X and put in the following to fix your MBR.

sudo fdisk -u /dev/disk0

I mean this as nicely as possible, but no, no no! I can't say this enough: most dual-booting Apple users should NOT use fdisk!!!

Here's why:

- fdisk is ignorant of GPT. Though not technically required, by default a Mac computer is using GPT for its disk partitioning scheme

- As part of enabling BIOS-based OS's to boot, which is probably how most people set up Windows or Linux on their Macs, OS X creates a hybrid MBR

- This hybrid MBR is ignored by OS X for its disk operations; any changes made with the Disk Utility app or the diskutil command line tool will nuke the ability to boot other OS's

- OS X does not bother synchronizing the hybrid MBR with the actual GPT partition tables

- At best, you have four or less partitions and fdisk will turn out OK. At worst, fdisk will create completely nonsensical partition entries

Instead, please use Rod Smith's gdisk (GPT fdisk) utility instead: [http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)

gdisk is aware of GPT, and has the ability to write a hybrid MBR that will work for other OS's on a Mac. It will scan for GPT partitions, then allow you to choose which three to add to the MBR and set one (or more, though not the best idea) as active.

As Rod explains ([http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)) hybrid MBR's are bad enough as it is. Trying to use fdisk with them can only make things worse.

---

