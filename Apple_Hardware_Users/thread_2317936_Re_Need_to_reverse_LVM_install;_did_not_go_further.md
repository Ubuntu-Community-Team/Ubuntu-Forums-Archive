---
title: "Re: Need to reverse LVM install; did not go further with install; have LVM backups."
date: 2016-03-21
forum: Apple Hardware Users
---

### Post by Gavi on 2016-03-21
Ubuntu Install Helps Destroy MAC -- MAYBE I CAN REVERSE IT?

I have a Mac with OSX and wanted to install Ubuntu Studio on a 40GB USB drive. By carelessness (and being a victim of the install menu trap), I went into LVM install without noticing that it didn't untick the first item where it warns about over-writing. Now my HDD has had its partition record changed (MBR) and it has had VG and LV structures added.

Needless to say, my MAC OS partitions and data are probably history.

Giving me some hope, I've been attacking this problem and found that utilities vgcreate and lvcreate have left backup files at /etc/lvm/archive/ which seem to correspond to the vg (volume group) and lv (logical volume) structures written. These appear to be in sda (new location and dimensions).

Now I'm curious to know if sfdisk (or whatever was used in the install script (or the script writer? (/sbin/lvm ? source code))) was kind enough to backup the MBR? If so, where is it? Better, where is the LVM install script so I can review exactly what was done.

As a footnote, Ubuntu install should always provide restore information and backup files; and the install menu should be redesigned with LVM as a subcategory of the 'warned overwrite' choice.

Also, being a new MAC, is the MBR system GPT (probably) or some form of BSD?

Otherwise, this Ubuntu Studio 14.04.4. (xfce) Live works great from an 8GBb Trans-it USB flash stick (4GB casper).

Can anybody help me? I,m desperate -- this isn't even my MAC! (my ex!).

This topic posted on askubuntu stackexchange 
[http://askubuntu.com/questions/748566/what-and-where-are-backup-files-for-ubuntu-install-of-lvm-installation-mbr-vg]("http://askubuntu.com/questions/748566/what-and-where-are-backup-files-for-ubuntu-install-of-lvm-installation-mbr-vg")
with some follow-up investigating.  Also posted at ubuntu discourse.  Now here.  Why so many forums?

The three big questions are:
1) Is there a LVM made backup of the MBR when it over-writes it?
2) Does LVM install to a vg/lv filesystem format immediately and thus preempt chosing a filesystem on logical volumes?  When?
3) Has anybody who designs the Ubuntu install anticipated this problem/need and knows how to help me?

---

### Post by oldfred on 2016-03-21
A Mac does not have an MBR to backup. But generally it is your responsibility to backup before installing.

All Macs since conversion to Intel chips use EFI which is a somewhat older version of UEFI. That uses gpt partitioning and boots from an ESP - efi system partition which is FAT32 formatted with boot flag.

---

### Post by howefield on 2016-03-21
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by Gavi on 2016-03-23
Thanks for the link.  I'm aware of the EFI and Recovery HD partitions that were on my MAC 1T drive.  I have there locations from /media/casper-rw/bin/partman  text log file.  I also have the backup images from lvm install.  Hope to reverse lvm, and put my GPT tables back to what they were before partman-auto and preseed.cfg changed them.  Before acting I want to know exactly what was done and by what program -- still investigating.  I'm also investigating about the tools required, namely the best GPT editor.  I'm aware of the responsibility to backup, but in this case Ubuntu was negligent.  It only takes 3 mouse clicks to rewrite the default HDD once the first live-USB menu is up, and the menu is misleading.  I didn't intend to touch the main MAC drive.  The 'bug' of the menu is that it has 3 choices: over-write (warning), LVM, and manual partition. Normally such choices in menus are mutually exclusive, but in the Ubuntu menu, the LVM choice doesn't cancel the first with the warning!  I went into manual partition hoping to install on a 40GB USB drive but didn't see it shown in gparted(?).  So, I backed out to the main menu and quickly chose LVM to see if it had a better way.  I didn't notice that when you click LVM the first box is also checked with it!  It's a clear trap!  And it should have had another window layer to warn about rewriting the active disk!  I have 35 years of working with software, including buying and programming the original IBM PC, and now web programming.  I'm not ignorant, just in this case I carelessly thought Ubuntu was more professional and didn't worry enough.

The Ubuntu Install process appears to be a black hole in the system, particularly partman-auto and 'preseed'.
I'm still investigating, but 'preseed' appears to be a kernel option that may link the Ubuntu install server (carbon) 
to retrieve a partman configuration file and maybe partman itself -- I haven't found it on my live system. 
Why does partman leave its log file in casper-rw/bin/ ?  At least the logical volume manager monolithic program 'lvm'
was decent enough to make image backups and place them in /etc/lvm/archive/.  I have found a reference to 
partman docs in the debian archives.  I'm looking for the line-by-line script for the install process with lvm.
I'm expecting something as simple as the following, based on inferences from what I've found:

partman-auto -f=lvm.cfg
lvm -install vg=/dev/sda

The above is my imagination, just a rough idea, because I don't yet know exactly about this process.
But where is the code?  Also, if lvm overwrites the filesystem upon setting up the volume group and logical volumes,
then my efforts are in vain.  But, if it does this, why bother with making image backups of what was on disk before 
its structure writing -- unless the images cover the fs structures too?

Any information would be greatly appreciated.  Thanks in advance.)

Meta: I see a big need in Ubuntu for an install process that's clear and reversable.  Maybe after this I'll try to help.

---

### Post by oldfred on 2016-03-23
I have always partitioned in advance and then installed, even back in DOS days. 

I do use gpt on my PC, do not have a Mac.
        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... 

I believe gdisk started with the Mac.
      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html](http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

