---
title: "Someone please help"
date: 2009-12-31
forum: Apple Hardware Users
---

### Post by rwltrz4 on 2009-12-31
I have tried over 7 times to install karmic on my intel mac mini and no matter what i get "missing os"

I download iso file from ubuntu.com 
burned to cd in disc utility
set up 2 extra partitions in disc utility one 15 gig for karmic and one 2 gig for swap
ran cd install
selected manual
selected sda 3 (15 gig) for karmic setting as ext3 file and formatting selected, and selected "/", and the 2 gig for a swap
in advanced tab i selected boot loader for sda 3

installed reboot and get the no os thing

can someone provide a easy to understand step by step process, right now my mac is set back up normal with full hd for mac

help

---

### Post by avtolle on 2009-12-31
Found this: [http://blog.costan.us/2009/03/ubuntu-810-or-904-on-mac-mini.html](http://blog.costan.us/2009/03/ubuntu-810-or-904-on-mac-mini.html) and hope it is of merit.

---

### Post by tom4everitt on 2009-12-31
INSTALL REFIT! Its that simple I would say. When you install ubuntu you change two partitions, which will take your partition tables out of sync. When partition tables are out of sync, you can't boot. 

What to do?
Before you do anything, install refit in os x:
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Then every boot you should be presented the refit menu, where you can choose to boot into os x. If you don't get this menu, run:
sudo /efi/refit/enable.sh
in os x. Then you should get it. 

When refit is installed, you can install ubuntu exactly the way you've been doing. When it is installed, you will still get the refit menu at startup. Choose the 'partition tool' option, and it will tell you your partition tables are out of sync, and ask you whether you want to sync them. Sync them. Reboot. Everything will be working!

Good luck!

---

### Post by rwltrz4 on 2009-12-31
refit is installed, partitions are synced, all that is fine problem is i have two options

osx
windows diamond shaped looking icon (not tux) that says "legacy"  not "ubuntu" when i enter that it just hangs, nothing happens.


I followed the instructions two posts up to a "T", only thing i am not sure about is he says to:

Mark ubuntu partition as ext4, shouldnt it be ext3 if ubuntu is on sda3?
And he says to keep bootloader at hd0, shouldnt it be sda3 too?

also in refits partition summary screen in gpt it lists ubuntu partition as "basic data" but in mbr it says "linux"


now in disc utlity in osx it lists 3 partitions:

osx
discOs3 (it says "Which appears to be partitioned by boot camp", format=ms-dos)
linux swap (it says "Which appears to be partitioned by boot camp",format= os extended journaled)


the refit disc info is as followed:




*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    128073767  Mac OS X HFS+
 3      128073768    152300330  Basic Data
 4      152300331    156300331  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    128073767  af  Mac OS X HFS+
 3      128073768    152300330  83  Linux
 4      152300331    156300331  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 128073768:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 152300331:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

---

### Post by tom4everitt on 2009-12-31
> **rwltrz4 said:**
> refit is installed, partitions are synced, all that is fine problem is i have two options

osx
windows diamond shaped looking icon (not tux) that says "legacy"  not "ubuntu" when i enter that it just hangs, nothing happens.
[\QUOTE]


This is normal. Its because of grub2, which is not recognized by refit yet.


[QUOTE]
I followed the instructions two posts up to a "T", only thing i am not sure about is he says to:

Mark ubuntu partition as ext4, shouldnt it be ext3 if ubuntu is on sda3?
[\QUOTE]

ext3 and ext4 are file systems, sda3 is the name of the third partition on the first hard drive (a=1). So you could definitively partition your third partition as ext4.  

[QUOTE]
And he says to keep bootloader at hd0, shouldnt it be sda3 too?
[\QUOTE]

This is sometimes (and sometimes not) a good idea. Usually it doesn't matter which you choose. 

But it could be a good idea to try installing ubuntu with that option. You don't have to redo everything, just install ubuntu again but with this option instead. 

[QUOTE]
also in refits partition summary screen in gpt it lists ubuntu partition as "basic data" but in mbr it says "linux"




Your respective partition tables look sane to me.

---

### Post by rwltrz4 on 2009-12-31
seems to be issue with refit because if i hold alt button at boot i have two options

refit
windows

if i select windows, bam i am in and ubuntu loads up fine

so the "refit" is/was the isssue

---

