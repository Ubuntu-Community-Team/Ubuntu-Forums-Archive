---
title: "Macbook 3,1 and reefit"
date: 2010-03-01
forum: Apple Hardware Users
---

### Post by relux on 2010-03-01
I'm sorry if this has been gone over multiple times - a search brings up tons of info but I am failing to find anything to help me here. I am an experienced Ubuntu user and certainly not new. However, this is giving me a headache.

On my MacBook 3,1 I have it bootcamp setup with Windows XP. I partitioned a drive and installed Linux. reefit fails to show Ubuntu on startup.  Here is what the partition inspector shows:


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    247368869  Mac OS X HFS+
 3      283370535    312576704  Basic Data
 4      247368870    247370823  Unknown
 5      247370824    281773167  Basic Data
 6      281773168    283370534  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    247368869  af  Mac OS X HFS+
 3      283370535    312576704  0b  FAT32 (CHS)
 4      247368870    247370823  ef  EFI System (FAT)

MBR contents:
 Boot Code: Unknown, but bootable

Why does  it show my Linux partition in MBR as FAT32?

---

### Post by linuxopjemac on 2010-03-01
first thing: did you sync the partition table from within rEFIt with the partition tool ?

---

### Post by las_vegas on 2010-03-01
First, the MBR partition was setup by Bootcamp and is unrelated to your current linux install. I suggest that you install and use the Grub2 EFI loader. If you also have Windows installed, keep the rEFIt, but if you're only booting between Mac OS X and Ubuntu, you'll find Grub a bit easier to configure.

---

### Post by relux on 2010-03-01
> **linuxopjemac said:**
> first thing: did you sync the partition table from within rEFIt with the partition tool ?

When I startup the partition tool  I get the following error:

Status: GPT partition of type 'Unknown' found, will not touch this disk.

I also have Windows installed..

---

### Post by las_vegas on 2010-03-01
Please see my post [here]("http://ubuntuforums.org/showpost.php?p=8898880&postcount=39") to get the grub.efi loader.

In your case, you'll need to add a Windows menu, but it shouldn't be too difficult. Do a Google search for "grub efi" for instructions about how to setup the grub.cfg file.

LasVegas

---

### Post by linuxopjemac on 2010-03-02
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

