---
title: "Windows 7 has three partitions?"
date: 2011-04-24
forum: Any Other OS
---

### Post by HunkirDowne on 2011-04-24
Why do I have three partitions on a "Windows only" laptop?  (OK, I have wubi installed but that resides as a file on one of the partitions.)

I have a laptop that came with Windows 7 installed.  There are three primary partitions for Windows: sda1, sda2, sda3.  I can identify sda2 as the main working partition but do not know for sure what the others are doing there.  I think (operative word) that sda1 is for vendor support of Windows.  I also think that sda3 could have been corrected when I made recovery disks.  Furthermore, I think that I can safely delete one or both of the 'recovery' partitions.

How do I know for sure what I think I know?

sda2 is most definitely a keeper: running wubi and wubi /host is on sda2.

fdisk accounts for all but 2,232 KB:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
6 heads, 63 sectors/track, 1292056 cylinders
Units = cylinders of 378 * 512 = 193536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           6        1084      203776    7  HPFS/NTFS
/dev/sda2            1084     1222624   230871040    7  HPFS/NTFS
/dev/sda3         1222624     1292050    13121536    7  HPFS/NTFS

If I have to keep sda3, fine, but it's 13 GB that I could use elsewhere.  Furthermore, it would be nice to have that volume space for the extended partition rather than get my partition numbers out of order.  Don't know how Windows will react to it.

Furthermore, sda2 contains the C:\Users folders but I will be creating a logical partition to contain D:\Users data.  In the end I will have C:\Users and D:\Users but user-generated files (Documents, Pictures, etc.) will be contained in the D: (sda5) partition.

Broadly, my method will be to:
(1) [win7]: Reduce the file count in the Users folders by backing up to external and then deleting the files.
(2) [boot CD]: Image sda2.
(3) [win7]: Create sda4 as extended and sda5 as NTFS (Type 7).
(4) [win7]: Convert C:\Users (partially) to D:\Users.
(5) [boot CD]: Create sda6-15 (as types 82, 83) for GNU/Linux distros.
(6) [boot CD]: Install GNU/Linux distro.

---

### Post by |{urse on 2011-04-24
One of those partitions is most likely a restore partition some oem kewldood decided you needed with your new pc.

---

### Post by lisati on 2011-04-24
My current laptop, which came with Vista preloaded, had 3 partitions out of the box. One was the main Vista partition, and one a recovery partition. I'm still not sure what the third partition was for, but think it had something to do with installation. After making a set of recovery disks, I was able to remove the non-Vista partitions without any obvious signs of distress. (Currently dual-boot with Ubuntu)

---

### Post by HunkirDowne on 2011-04-24
> **lisati said:**
> My current laptop, which came with Vista preloaded, had 3 partitions out of the box. ... I was able to remove the non-Vista partitions without any obvious signs of distress. (Currently dual-boot with Ubuntu)

OK, that's good to know.  But I guess my main concern is that should I have to perform "disaster" recovery, would I be in a pickle without one or more of the non-Windows partitions?  I do have the recovery CDs (DVDs?) somewhere safe, if not handy at the moment.

That said, one of the main reasons for having Windows in the first place was to have Microsoft Office for professional reasons.  Instances are very rare that I prefer MS-Office over LibreOffice, but those rare instances are rather important to me.  And that said, the lines betwixt the two are becoming fuzzier every day with adoption of OpenDocument features by Microsoft.  Hat's off to them for that one.

My wubi install is showing it's age and is past it's prime.  I may "buy" some time by uninstalling it and reinstalling a more recent version, but I am starting to see some instability that is really starting to hurt.  Much better to have a more permanent GNU/Linux solution than this wonderful but quite temporary solution.

My "ultimate" dream (for this laptop) is to have Win7 there when I really need it, but multi-boot with Win7, Ubuntu (Unity?), and one or more of Aptosid (KDE), Debian Stable (currently Squeeze) running GNOME, and Linux Mint Debian Edition (probably the last -- at least at first ;-) ).

Thanks!

---

### Post by oldfred on 2011-04-24
Windows 7 on new computers usually uses all 4 primary partitions. The first is a (hidden in windows) boot/recovery partition. The main install, a vendor recovery which is just an image of your drive as purchased, and then a vendor utility partition. 

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

In addition to saving recovery to DVDs and making a windows repair CD.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

You should have a repair CD or liveCD for every system installed.

---

### Post by mips on 2011-04-25
You can install Win7 to a single partition. Just create install media from the Win7 media partition. The 100MB partition is a recovery partition that you don't have to use.

---

### Post by wolfen69 on 2011-04-25
> **mips said:**
> You can install Win7 to a single partition. Just create install media from the Win7 media partition. The 100MB partition is a recovery partition that you don't have to use.

The 100mb partition is the boot partition. I've only done 18 million windows installs. ;)

---

### Post by krapp on 2011-04-25
> **wolfen69 said:**
> The 100mb partition is the boot partition. I've only done 18 million windows installs. ;)

Why is it formated as fat32?

---

### Post by mips on 2011-04-25
> **wolfen69 said:**
> The 100mb partition is the boot partition. I've only done 18 million windows installs. ;)

Nonsense, it's a recovery type partition for diagnostics purposes. You don't need it and you can install Win7 without it, I never let win7 create the 100MB partition.

---

### Post by oldfred on 2011-04-25
If you look at any of the outputs from a boot info script the boot/recovery partition has these two files:
/bootmgr /Boot/BCD

The main install has this boot file.
/Windows/System32/winload.exe

Installs with Vista or win7 to one partition have all three files in the main install.

Windows supposed created the 100MB partition to let you encrypt the main install as the boot could not be encrypted. Also to get users used to the idea of a separate boot partition as with UEFI & gpt drives you have to have an efi partition with boot files. But I would not put it past windows to make it so with the system recovery partition and a vendor partition that all 4 primary partitions are used and then you have difficultly installing another system.

---

### Post by wolfen69 on 2011-04-25
> **mips said:**
> Nonsense, it's a recovery type partition for diagnostics purposes. You don't need it and you can install Win7 without it, I never let win7 create the 100MB partition.

[http://www.urtech.ca/2011/04/solved-what-is-the-100mb-partition-on-all-windows-7-boot-disks/](http://www.urtech.ca/2011/04/solved-what-is-the-100mb-partition-on-all-windows-7-boot-disks/)

It contains boot loader files. Whether or not you need it, isn't the question, as it still exists on most installs. If you installed windows with the 100mb partition, and then deleted it after install, your pc won't boot. Check the windows forums my friend. Next!

---

### Post by HunkirDowne on 2011-04-26
> **wolfen69 said:**
> [http://www.urtech.ca/2011/04/solved-what-is-the-100mb-partition-on-all-windows-7-boot-disks/](http://www.urtech.ca/2011/04/solved-what-is-the-100mb-partition-on-all-windows-7-boot-disks/)

It contains boot loader files. Whether or not you need it, isn't the question, as it still exists on most installs. If you installed windows with the 100mb partition, and then deleted it after install, your pc won't boot. Check the windows forums my friend. Next!

Since *I* did not install Windows (the "factory" did) I have at least two partitions OEM, sda1 and sda2.  Since creating Recovery Disks using the installed solution, I have three partitions with sda3, if not originally there (don't really know, but...) then created when I created my Recovery Disks.

Let's say for a moment that I completely trashed my sda and had to physically replace it.  Would not the previously created Recovery Disks assist me in reimaging my sda?

Also, all three partitions have 
> Boot files/dirs:   /bootmgr /Boot/BCD
... Wouldn't this mean that I could delete sda1 and sda3 and still use the sda2?


> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

... Perhaps I would need to run the Windows boot utility but once Grub was installed I think this would be unnecessary, or am I missing something?

By the way...
> **krapp said:**
> Why is it formated as fat32?
... I do not (currently) have a fat32 partition here but seem to recall that is the way Vista had it.  Only a clue.

All this would be moot if other operating systems were as easy to install and maintain as your average GNU/Linux distro.  Canonical really did a good thing by streamlining this process for the average user.  Much easier than my RedHat install years ago.  (Although I must say slackware's install was a breeze -- just text-mode and probably a little daunting for the Windows user with little or no *ix experience).

---

### Post by _outlawed_ on 2011-04-26
> **HunkirDowne said:**
> ...

Partition 1: Recovery
Partition 2: Primary
Partition 3: System reserved

P1 is used as a recovery, which basically contains your factory OS in case you decide to restore/repair your installation. P2 is your primary, and is what you boot into. P3 contains the system reserved files such as the MBR and other boot/system related files.

---

### Post by oldfred on 2011-04-26
Windows uses the boot flag to know which partition to boot from and jumps to the added code in the windows partition boot sector (PBR). Grub just jumps to the PBR when it chain loads to windows. So you have to make sure you have the boot flag on the partition you boot from and that it is bootable.

Lots of detail, but pictures worth reviewing. How windows boots, dual boots and how MBR (msdos) systems work.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by HunkirDowne on 2011-04-26
> **oldfred said:**
> Lots of detail, but pictures worth reviewing. How windows boots, dual boots and how MBR (msdos) systems work.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Been busy -- too tired to look at this anymore tonight but I will look at this again tomorrow (including your post).  First blush says that this is what I need to know, but I'm just looking at the pictures for now.  ;-)

Thanks!

---

### Post by srs5694 on 2011-04-26
> **oldfred said:**
> Windows uses the boot flag to know which partition to boot from and jumps to the added code in the windows partition boot sector (PBR). Grub just jumps to the PBR when it chain loads to windows. So you have to make sure you have the boot flag on the partition you boot from and that it is bootable.

Actually, it's the Windows *boot loader* that relies on the boot flag. Windows itself will boot when the boot flag is absent, provided you use another boot loader (such as GRUB) to get it started. At least, this is true of recent versions of Windows -- IIRC, anything based on Windows NT, which includes NT, XP, Vista, and 7. Windows 9x/Me requires that the boot flag be present on its boot partition, even when using GRUB or some other boot loader to start the process. It's possible that Windows requires the boot flag to be present for some non-routine operations, like upgrading the OS, but I've not researched or tested this point extensively. I *have* booted Windows Vista with the boot flag absent, though.

---

### Post by HunkirDowne on 2011-04-27
> **oldfred said:**
> Lots of detail, but pictures worth reviewing. How windows boots, dual boots and how MBR (msdos) systems work.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

OK. Read multibooters and this thread a couple more times.  I gather that if I want Windows to handle my recovery of Windows, I need to leave the boot (sda1) and recovery (sda3) partitions alone so that if Windows (sda2) takes a nosedive I can recover.  But I do not ever recall needing to let Windows do my work for me.  The only times that I have, the ultimate solution was to reinstall Windows which it sounds as if I can do with my Recovery DVDs anyway.

So since my goal is to install one or two GNU/Linux distros that contain GRUB I can choose to let Windows continue to manage my boots for me or I can let GRUB do it.  Frankly, repairing a damaged GRUB installation is almost trivial but since DOS 6.22 I have not had much success with the solution from Redmond.

Get out your guns so you can shoot holes in my plans:

_Assuming_:
[FONT="Courier New"][SIZE="2"]/dev/sda1 | Windows System (**hidden**)
/dev/sda2 | Windows Operating System (**C:**)
/dev/sda3 | Windows Recovery (**D:**)
/dev/cd0  | CD/DVD-+=/*^ (**E:**)
[/SIZE][/FONT]
 0.  Make Temporary Backup
 1.  Uninstall Wubi - Declutter - De-dupe.
 2.  Make Backup:
	 2.a. Mark Default State Backup w/ Date and Machine.
	 2.b. Archive Backup to "Permanent" (quasiperm).
	 2.c. Optionally Delete Temporary Backup.
 3.  Make "(U:\)" partition (for now, /dev/sda5):
	 3.a. Shrink /dev/sda2.
	 3.b. Create /dev/sda4 (extended).
	 3.c. Create /dev/sda5 (logical U:, if possible).
 4.  Selectively Move Users' Files and Folders:
	 4.a. mkdir -p D:\Users\hunkirdowne 
		(well, the Windows equivalent ;-).
	 4.b. move non-critical files & folders to U:\Users.
	 4.c. point Windows in the right direction.
 5.  Make Backup (Complete start to new device & 
	Mark New State Backup...)
 6.  Reformat /dev/sda1 to ext3 (for /boot).
 7.  Shrink /dev/sda2.
 8.  Delete /dev/sda3.
 9.  Make /dev/sda3 ext3 (for /boot) in such a way that partition 
	is orderly.
10.  Expand /dev/sda4 to fit remaining space.
11.  Make /dev/sda6+(<=15) for GNU/Linux usage.
12.  Install a GNU/Linux distro with GRUB to MBR and chainload 
	Win7 accordingly.

That's it -- my 12-step recovery process.

Thoughts?

---

### Post by oldfred on 2011-04-28
The windows boot/recovery in sda1 has nothing to do with and is separate from an ext3 /boot partition. I would not touch it, but if you do want to delete it, move boot flag & repair windows to get it to boot directly first. 

Many of us do not recommend /boot partitions for standard desktops. Servers, RAID, & LVM partitioning may have some advantages with a separate /boot. Also old systems with a 137GB BIOS boot limit may need  a separate /boot or the entire / (root) inside the first 137GB.

---

### Post by HunkirDowne on 2011-04-28
> **oldfred said:**
> The windows boot/recovery in sda1 has nothing to do with and is separate from an ext3 /boot partition. I would not touch it, but if you do want to delete it, move boot flag & repair windows to get it to boot directly first. 

Thanks!  I should have thought of that but didn't.

Tried (not real hard) to find the quote from the movie Kelly's Heroes by Oddball (Donald Sutherland) talking about the mods he did to his tank.  Salient point was to be able to back-up out of a mess quicker than you got into it.  Your advice certainly falls along these lines.

> **oldfred said:**
> Many of us do not recommend /boot partitions for standard desktops. Servers, RAID, & LVM partitioning may have some advantages with a separate /boot. Also old systems with a 137GB BIOS boot limit may need  a separate /boot or the entire / (root) inside the first 137GB.

LOL!  It was the older 8GB BIOS boot limit that got me started down this road and I just never changed my ways!  Been doing a separate /boot now for how many years?  Too funny how some habits die hard because we don't even realize they are just that -- habits.

Thanks again,
-HD.

---

