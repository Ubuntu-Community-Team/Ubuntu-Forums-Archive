---
title: "From doubleboot to tripleboot"
date: 2008-03-29
forum: Apple Intel Users
---

### Post by Tribe on 2008-03-29
Hi there,

If got a MacBook Pro (2nd gen. i think) and i've been running happily MacOS X (i think i used it less than 10 times :) and a Kubuntu Feisty which runs pretty much all the hardware quite well.

Now happens that i need to install WinXP SP2.

I've red some tripleboot guides and some threads in this forum but i wanted some advice before start, because i don't want to make a mess of it because i need the GNU/Linux box for work.

I think my confusion comes from the EFI+GPT vs MBR stuff, GPT/MBR sync and partition order in disk.

In my current system disk i have, in order, these partitions: a 0.2GB FAT32 (that's EFI stuff) one, a 40GB HFS+ (MacOS X stuff), a 60GB EXT3 one (GNU/Linux home), a 10GB one (GNU/Linux root) and a 1GB one for GNU/Linux swap.

Also i have rEFIt installed and GRUB (with timeout 0) in hda3 partition (the linux one).

What i'd like to do is to resize/move them and add a 20GB FAT32 partition somewhere. I've red that it must be at the end of the disk geometry because if not windows won't boot, is this true? Or can i add the windows partition in the middle of the disk geometry?

Also, i've red that since Feisty parted/GParted is able to sync GPT and MBR partition tables, and that parted is able to resize HFS+ partitions (disabling journaling before?) So one question is that if i resize the HFS+ partition and the 60GB ext3 partition my box i gonna boot as usual or do i need to do any extra step? 

The next question is about windows booting; if i install it, will it "destroy" my current MBR partition table? Do i need to check anything else?

Thanks for your help.

---

### Post by ronocdh on 2008-03-29
Installing Windows will definitely overwrite your MBR, but that's not a problem. As long as you preserve your Linux install, you can just reinstall GRUB and it will find Windows fine. Then you'll have to "chain-load" from rEFIt to GRUB, then choose Linux or Windows. It's possible to setup an EFI-aware bootloader, but I've never found it worth the effort, as I don't boot into Windows often enough to make it worthwhile.

I recommend using the GParted LiveCD to resize your partitions. IIRC, GParted can shrink HFS+ but not expand it. In any case, you can definitely shrink your Linux install, creating free space, which you can make a new partition out of (I use FAT32 so I don't have to bother with ntfs-3g, which was unstable a year ago when I last tried it—also, OSX doesn't really support NTFS that well). Once that new partition is created, boot to the Windows CD and install on that last partition (Windows likes to be at the end of the drive for some reason).

After installing and setting up Windows, reboot to a Linux LiveCD and reinstall GRUB. On the next reboot you might have to sync the GPT and MBR in rEFIt, but other than that, you'll be good to go.

---

### Post by cyberdork33 on 2008-03-29
Windows needs to last of the first **_4_** partitions! And you also want the Ubuntu root partition in the first four, otherwise you will run into trouble booting. Other partitions that you do not want to access from windows can go beyond 4.

Now whether you can resize and move things around and still get it all working is another story. 

Since you have grub installed on the linux partition I don't think you will have an issue with Windows overwriting the MBR (since there is nothing there yet) then you will be able to boot to windows or Ubuntu from rEFIt.

---

### Post by Tribe on 2008-03-29
Thanks for your help guys, very appreciated.

I have a doubt left, related to this:

> **cyberdork33 said:**
> [...]And you also want the Ubuntu root partition in the first four, otherwise you will run into trouble booting [...]

At the moment my linux root partition is /dev/sda4 but it's the 5th in the hard disk geometry (at least this is what gparted suggests, screenshot attached).

So my plan is something like this (with GParted liveCD):

- delete that 4GB ext3 partition that i'm not using
- resize the linux home partition with 15 GB less
- create a 19GB FAT32 partition for windows, which happens to be the number 4 if im not wrong (can anyone confirm?) from left to right
- not to touch the linux root partition (it seems it's the 5th but now linux booting is working fine)
- install windows in the FAT32 partition with the bootcamp driver CD, it will install its bootloader in the MBR.
- reinstall grub (not sure if this is needed)
- syncronice BMR and GPT with gptsync from rEFIt command line (not sure if this is needed).

Thanks!

// edit: i've downloaded lastest rEFIt, which has a partition inspector. Its output confuses me even more, it looks that GPT and MBR are not synced at all:

> *** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     84295719  Mac OS X HFS+
 3      231975901    234436544  Linux Swap
 4      219052072    231975900  EFI System (FAT)
 5       84295720    210696232  Basic Data
 8      210696233    219052071  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     84295719  af  Mac OS X HFS+
 3      231975901    234436544  82  Linux swap / Solaris
 4 *    219052072    231975900  83  Linux

---

### Post by cyberdork33 on 2008-03-29
the partition inspector output looks right. The EFI sees Linux partitions oddly for some reason...

The physical layout on the disk does not matter. sda4 is the 4th partition. windows needs to be sda4 (or maybe something less if you can get it to work that way).

---

### Post by Tribe on 2008-04-01
Hi there,

Well, i created the FAT32 partition and had to do a $ gptsync in rEFIt console to be able to start GNU/Linux as usual.

The problem comes when trying to install windows; i boot from the windows CD and it says something like "Press a key to start installation from CD" but i can't do that because keyboard is unresponsive at that time :confused:

Any thoughts?

p.s: It's XP + SP2

---

### Post by Tribe on 2008-04-01
> **Tribe said:**
> Hi there,

Well, i created the FAT32 partition and had to do a $ gptsync in rEFIt console to be able to start GNU/Linux as usual.

The problem comes when trying to install windows; i boot from the windows CD and it says something like "Press a key to start installation from CD" but i can't do that because keyboard is unresponsive at that time :confused:

Any thoughts?

p.s: It's XP + SP2

Nevermind, fixed updating to last EFI firmware from MaxOS X software updater.

---

### Post by cyberdork33 on 2008-04-01
> **Tribe said:**
> Nevermind, fixed updating to last EFI firmware from MaxOS X software updater.yep... You might also get this issue still if you have a bad combo of USB devices connected. every once in awhile I have to change the port my keyboard is connected to to get it to work.

---

