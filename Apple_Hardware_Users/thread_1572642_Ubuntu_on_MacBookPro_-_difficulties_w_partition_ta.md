---
title: "Ubuntu on MacBookPro - difficulties w partition tables"
date: 2010-09-11
forum: Apple Hardware Users
---

### Post by david.macquigg on 2010-09-11
I'm having difficulty getting Ubuntu installed on my MacBookPro.  Following the instructions at [https://help.ubuntu.com/community/MacBookPro3-1/Lucid](https://help.ubuntu.com/community/MacBookPro3-1/Lucid), I seem to end up with messed up partition tables.  I see several suggestions in the Ubuntu forums, including give up and use VirtualBox, but before experimenting any more, I would like to know if there is a simple fix.  Ubuntu installed nicely on my desktop (Generic PC > XP > VirtualBox).  It should be just as easy on a Mac.  I must be doing something wrong.

```

---------  My laptop
MacBookPro3,1 with Intel Core 2 Duo and Mac OS X 10.5.8.
---------  CD to install
ubuntu-10.04.1-desktop-i386.iso, verified.
---------  Links where I found useful information
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
---------  Step-by-step instructions I attempted to follow
[https://help.ubuntu.com/community/MacBookPro3-1/Lucid](https://help.ubuntu.com/community/MacBookPro3-1/Lucid)

---------  Install log                                       9/10/2010
#     My comments.
#err  Notes where there seems to be errors in the instructions.

Boot Camp Assistant (Applications/Utilities)
  Partition the HD:         88  :   60  GB
  # 60GB partition is labelled "Windows", no choice here.

Install rEFIt-0.14.dmg from refit.sourceforge.net
  Running on:
    EFI Revision 1.10
    Platform:  x86_64 (64bit)
    Firmware:  Apple 1.10
    Screen Output:  UGA Draw (EFI 1.10), 1440 x 900

Boot from CD
  System > Administration > Partition Editor
#err  Partition Editor is not on menu.  Used GParted instead.
  Delete new partition /dev/sda3.
  # Now have:
  /dev/sda1   fat32   EFI     200.00 MB     boot
  /dev/sda2   hfs+             87.88 GB
  unallocated                  60.98 GB

Install Ubuntu from CD
  dave-laptop
  ext4 filesystem
  install to "largest continuous free space"
#err Skip the advanced "install grub to /dev/sda3."  /dev/sda3 not on the list.

Fix the Partition Tables
  Select "partition tool" from rEFIt menu
  # Response is different than expected.  Screen says
  "Starting gptsync.efi"
  Current GPT partition table:
  ...
  Current MBR partition table:
  ...
  Status: MBR partiton table is invalid, partitions overlap.
  Error: Not Found returned from gptsync.efi 
  # This might have something to do with skipping the grub install above.

#err  Cannot fix the partition tables, as directed in help document.  There
#err  is no option to do so.  Hitting any key returns to the rEFIt menu.

# Cannot boot to Ubuntu from rEFIt menu.  System just freezes.

Try again install from CD.
Hold "c" while booting.
Select "Install Ubuntu" from menu.

# Ubuntu installer shows current partition table as:
  fre space                0     MB
  /dev/sda1   fat32        209   MB 
  /dev/sda2   hfs+         94355 MB 
  free space               1     MB
  /dev/sda3   biosgrub     1     MB
  /dev/sda4   ext4         62758 MB
  /dev/sda5   swap         2715  MB
  free space               0     MB

# What is biosgrub?  Maybe this is causing the problem.
Delete all partitions after /dev/sda2.
# Cannot save modified table.  Error says "No root file system is defined.

Try instead with GParted
Boot from Ubuntu CD.
System > Administation > GParted
Delete all partitions after /dev/sda2.
  /dev/sda5 has a lock icon, which needs to be removed by clicking
    Partition > SwapOff

Install Ubuntu from CD
Restart
rEFIt now shows two Linux systems (HD and CD)   ???

Install Ubuntu from CD
  install to "largest continuous free space"
  dave-laptop
  ext4 filesystem
  Advanced: Install boot loader on /dev/sda        ???
# Install looks normal, but restart crashes out.

Second restart OK.
Start rEFIt partition tool.
# Same error as before - partitions overlap.
Back to rEFIt menu.
Boot Ubuntu from HD.  Hangs at startup screen.

Boot Ubuntu from CD.
# Ubuntu installer shows partition table identical to above, including 
# biosgrub.

```

---

### Post by srs5694 on 2010-09-11
I've seen reports of badly damaged hybrid MBRs being created by some versions of rEFIt. If you want to know if this is happening, type "sudo fdisk -lu /dev/sda" at a Linux shell prompt (use the installer's live CD mode) and look for overlapping partitions. Post the results here (in a code block, as you did above) if you need help interpreting the results.

If you've got the sort of overlapping partitions I suspect you've got, there are at least two, and possibly three or more, solutions:


[list]
[*]Use Linux's fdisk to delete the offending MBR partition(s), leaving *one* type-0xEE (EFI GPT) partition and however many other partitions you need.
[*]Use another utility, such as my [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) to create a fresh hybrid MBR. (Note that some versions of GPT fdisk have their own hybrid MBR bugs, so I recommend you download the latest version from the program's [Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) rather than use the version from the Ubuntu APT repository, which is old.) You probably only need the Linux ext4 partition in the MBR -- and maybe not even that (see the next point).
[*]I've heard that it's possible to boot Linux on a Mac using a conventional pure-GPT configuration rather than a hybrid MBR. Unfortunately, I don't know the details of how to get this to work. From a disk point of view, this is the best option, since hybrid MBRs are ugly and dangerous. Whatever the other details, you'll need to use GPT fdisk or some other utility to create a fresh protective MBR. In GPT fdisk, you'd do this from the expters' menu (type "x" at the main menu), using the "n" option. Then type "w" to save your changes.
[/list]


Good luck!

---

### Post by david.macquigg on 2010-09-12
SRS, thanks for your helpful response.  I ran fdisk, and there are indeed overlapping partitions (see output below).  I saw this also in the output from rEFIt partition tool, but just showed it as ... in my original posting.

I'm a little hesitant to start doing surgery using fdisk or gdisk.  My "luck" with brain surgery is not so good.  :>)  Also, now that I'm more confident that the problem is not just some stupid mistake from my misreading of the instructions at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation), I think we really need to correct those instructions.  There must be thousands of Mac users who have hit the same problem.  

We could edit that wiki page, and suggest using gdisk as part of the standard setup.  That would get the attention of the MactelSupportTeam, some useful discussion, and maybe a better procedure overall.  Meanwhile, I'm going to look further at using VirtualBox as an alternative to a dual boot.  I need something real soon to recommend to graduate students in a class at the University.  VirtualBox has millions of users, so I expect they have worked out the kinks, and my one experience (installing XP > VirtualBox > Ubuntu) was excellent.

```
=== Output from $ sudo fdisk -lu /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00004950

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   184696871    92143616   af  HFS / HFS+
/dev/sda3               1   184700927    92350463+  ee  GPT
/dev/sda4       184700928   307275775    61287424   83  Linux

Partition table entries are not in disk order
```

---

### Post by srs5694 on 2010-09-12
I don't think the problem is with the instructions on that page per se; I think the problem is that some utility (probably a specific version of gptsync) is buggy. Unfortunately, I don't have a real Intel-based Mac to experiment with, so it's hard for me to nail this down precisely. (I've got an ancient PowerPC-based Mac and various BIOS-based PCs.) That said, there certainly are other Mac users who've run into this problem; I've seen it reported several times.

As to fixing the issue yourself, you need to use fdisk to delete /dev/sda3. Thereafter you'll have a legal MBR partition table (albeit not quite GPT-compliant, since hybrid MBRs by definition are not GPT-compliant). Alternatively, if you install GPT fdisk for Linux (version 0.6.9 or later), you could use this command:

```

sudo sgdisk -h 2:4 /dev/sda

```

This creates a new hybrid MBR that contains GPT partitions 2 and 4, using the default mapping of GPT to MBR partition type codes in GPT fdisk. If anybody else reads this, be sure to change the partition numbers appropriately for *your* disk. One caveat: I'm not sure how the boot loaders work on Macs. If they require the partition *numbers* to match for bootable GPT and MBR partitions, you'd need to specify the partitions as "2:3:4" or "2:5:4" to get your partitions 2 and 4 in the right positions. (MBR partition #1 will be the protective partition.)

If you want some insurance against mistakes, you can launch gdisk first and use the "b" option on the main menu to make a backup of your partition table, or use sgdisk's -b option (as in "sudo sgdisk -b backup.gpt /dev/sda"). This option backs up both the MBR (warts and all) and the GPT data to a file, which you can then copy to a USB flash drive or whatever for safekeeping. If something goes wrong, you can use the "c" option on the recovery & transformation menu to restore the backup. FWIW, I recommend doing this for *any* GPT disk you've got. Having a backup of your partition table can save a lot of trouble should something go wrong.

---

### Post by david.macquigg on 2010-09-12
SRS, thanks again for the suggestions.  I posted a long reply, previewed the post, then hit submit.  It came back with a login screen (in spite of the fact that I was already logged in).  I entered my login again, as requested.  My post was gone, and I don't have time now to re-type it.  I'll try again later.

Meanwhile, I'll post a note linking to this thread in the installation instructions at [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation).  There is a note at the top of that page saying the developers are working on a major revision.  Let's hope they finally get all the kinks worked out.

---

### Post by srs5694 on 2010-09-13
> **david.macquigg said:**
> SRS, thanks again for the suggestions.  I posted a long reply, previewed the post, then hit submit.  It came back with a login screen (in spite of the fact that I was already logged in).  I entered my login again, as requested.  My post was gone, and I don't have time now to re-type it.  I'll try again later.

I've had the same problem from time to time. It seems that the forum software logs you out after a period of inactivity. Unfortunately, typing in the reply box doesn't count as activity until you click "Submit Reply." If I type a lengthy reply, I make it a point to first cut-and-paste the reply into a local text editor so that if the forum software has logged me out, I don't lose the whole thing!

---

### Post by cdambo on 2010-09-15
I am having the same problem with rEFIt. I dont understand the gdisk or fdisk comments could you explain them or what I must do again for someone who isn't great with computer talk.

---

### Post by david.macquigg on 2010-09-16
fdisk and gdisk are utilities that partition your disk and create partition tables specifying the location of the partitions.  fdisk is for old format partition tables.  gdisk is for the newer, more versatile format.  The setup recommended at [https://help.ubuntu.com/community/MacBookPro3-1/Lucid](https://help.ubuntu.com/community/MacBookPro3-1/Lucid) generates both types of tables, and the problem we seem to be having is an inconsistency between the two.  rEFIt is supposed to fix that inconsistency, but for some reason, it often fails.

The alternative to installing different systems on different partitions is to install virtual machines.  What appears to be an isolated disk (partition) to a virtual machine is just a big file on the host system.    This is a superior solution in every way, including not having to re-boot when you switch from one system to another.

I went with partitioning initially, on the assumption that it would be simpler to set up, and I really didn't need the advantages of a VM.   Having wasted days on trying to get these partitions working, I have now concluded that it was a waste of time.  VirtualBox is a much simpler setup, in spite of the fact that VMs are orders of magnitude more complex in design than partitions.  Sun deserves a lot of credit for encapsulating that complexity, and making the user interface and installation procedure relatively simple.

Unless I run into some problems with VirtualBox, I probably won't be working any further on this partitioning problem.   If you would like to discuss Ubuntu on MacBookPro using VirtualBox, join us in the Virtualization forum at [http://ubuntuforums.org/showthread.php?t=1569053](http://ubuntuforums.org/showthread.php?t=1569053).

---

### Post by skakillers on 2010-09-22
I'm having the same problem and also attempting to fix it. I've deleted the partition dev/sda3 using gparted from the ubuntu live cd. This fixed the partition synchronizing error in rEFIt, but now I'm wondering where I should install my bootloader. Can I put it in the EFI partition? I don't think I can, I'm not suuuper knowledgeable about this. I have installed ubuntu before on this same computer (a last generation, pre-unibody macbook pro) without any problems, but this time it's not playing nice.

---

### Post by tpievila on 2010-10-06
Could someone post their working GPT and MBR tables? After half a year I tried to get ubuntu working again, got it booting and upgraded to Maverick, but after creating a new partition (tried to setup TrueCrypt) the whole thing broke down and I'm no longer able to boot into Ubuntu.

All in all, it feels like Ubuntu on MacBook is horribly unstable and the documentation doesn't really say how to fix problems. I've tried a _lot_ of combinations in getting the MBR right, with various results (grey "legacy os" symbol, "Missing operating system" and black screens) but even the EFI shell doesn't work in rEfit. And nothing tells us what rEfit really expects; what MBR partition types, bootable status and so on (where is it even getting that "legacy os").

---

### Post by david.macquigg on 2010-10-06
> Ubuntu on MacBook is horribly unstable

The problem is in rEFIt, not Ubuntu.  Ubuntu installed easily in VirtualBox on my MacBookPro, and I've had no problems since installing it two weeks ago.  See my earlier post.

---

### Post by tpievila on 2010-10-07
> **david.macquigg said:**
> I've had no problems since installing it two weeks ago.  See my earlier post.

Could you post your MBR and GPT tables so that I could try reversing whatever damage gptsync did?

---

### Post by srs5694 on 2010-10-07
> **tpievila said:**
> Could you post your MBR and GPT tables so that I could try reversing whatever damage gptsync did?

You may want to read my [Web page on hybrid MBRs,](http://www.rodsbooks.com/gdisk/hybrid.html) perhaps in conjunction with other pages in my [GPT fdisk documentation,](http://www.rodsbooks.com/gdisk/) and perhaps the [Wikipedia entry on GPT.](http://en.wikipedia.org/wiki/GUID_Partition_Table) You could also post those partition tables here, as revealed by "sudo fdisk -lu /dev/sda" and "sudo gdisk -l /dev/sda" (the latter will require you to install GPT fdisk from the gdisk package).

---

### Post by david.macquigg on 2010-10-07
TP, you don't need to fix any unsynchronized partition tables.  You don't need disk partitions at all.  Just remove the new partition entirely.  VirtualBox installs within the existing partition.

Is there some reason you want to use partitions?  Even if we get the current problems fixed, new problems will arise as the dominant vendors (Microsoft and Apple) try to hog the machine and make life difficult for competing systems.  VirtualBox seems to have avoided these problems.

---

### Post by tpievila on 2010-10-08
Rod: Your pages were invaluable, and I indeed had already read them. The problem was that I wasn't really aware what rEFIt expects to find, and that wasn't documented. In the end I read the source code to understand the behaviour I was getting. Thank you for the great tool you made.

David: I would have responded already earlier, but flaky GPRS in train ate two of my replies earlier. But what you are suggesting is that I, nor many others do not understand what they want and that our questions and problems are invalid. When the question is "How can I do A?", answer "Well, you should be doing B anyway" is not helping at all. I already do, and did have Ubuntu running virtualized. But that wasn't often good enough and didn't solve any problems I had with OS X annoyances.

Running Virtualbox won't stop configd from locking up twice a day when running mobile broadband. Running Virtualbox won't stop the Apple X11 from refusing connections after mysterious events. Running Virtualbox won't give me back the memory that booting into OS X took when I wanted to get into Ubuntu, nor dozens of other reasons to change OSes. I was fed up with OS X, and wanted Linux. Instead of, not in addition to.


For what's it worth, I think I now understand the problem of Ubuntu on  Macbook very well, and if anybody else is having problems, please  contact me. I intend to document the whole process with all dead ends  and frustrations soon, I just need to run a couple of tests to see what is ok and  what will break the system (my suspicions go towards OS X doing  anything to partitions after the multiboot has been set up and secondly towards using  extended partitions while installing Ubuntu, which might confuse the  gptsync badly indeed).

---

### Post by srs5694 on 2010-10-08
> **tpievila said:**
> For what's it worth, I think I now understand the problem of Ubuntu on  Macbook very well, and if anybody else is having problems, please  contact me. I intend to document the whole process with all dead ends  and frustrations soon, I just need to run a couple of tests to see what is ok and  what will break the system (my suspicions go towards OS X doing  anything to partitions after the multiboot has been set up and secondly towards using  extended partitions while installing Ubuntu, which might confuse the  gptsync badly indeed).

If by "extended partitions" you mean MBR extended partitions with contained logical partitions on a hybrid MBR, then that is indeed a *Very Bad* approach. Keeping the GPT and MBR partitions synchronized in such a case would be a nightmare. I know of no utility that attempts to do the job. If such a utility ever emerges, I personally would consider it bordering on malware, the practice would be so bad.

Since Linux understands GPT perfectly well, my personal preference would be to use a conventional GPT when installing Linux on a Mac, unless Windows is also involved. Unfortunately, I don't know if the Mac boot process, including the commonly used boot loaders like rEFIt, can handle that. There could also be Ubuntu-specific complications, particularly with respect to installation, since installers sometimes impose limitations that can be overcome once the OS is installed.

---

### Post by inphektion on 2010-10-09
without reading this whole thread i can tell you right now that directly after the hfs+ partition mac wants a small 100-200mb slice.  its not formated anything just empty.  if you boot into mac mode and re-bootcamp a large partition you'll see it created again.  Instead of deleting the bootcamp part and that little chunk and re-partitioning i just carved up the bootcamp piece.  without that little piece there you can't upgrade mac osx ( i was stuck on leopard for a while which i why i know of this).


> **david.macquigg said:**
> I'm having difficulty getting Ubuntu installed on my MacBookPro.  Following the instructions at [https://help.ubuntu.com/community/MacBookPro3-1/Lucid](https://help.ubuntu.com/community/MacBookPro3-1/Lucid), I seem to end up with messed up partition tables.  I see several suggestions in the Ubuntu forums, including give up and use VirtualBox, but before experimenting any more, I would like to know if there is a simple fix.  Ubuntu installed nicely on my desktop (Generic PC > XP > VirtualBox).  It should be just as easy on a Mac.  I must be doing something wrong.

```

---------  My laptop
MacBookPro3,1 with Intel Core 2 Duo and Mac OS X 10.5.8.
---------  CD to install
ubuntu-10.04.1-desktop-i386.iso, verified.
---------  Links where I found useful information
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
---------  Step-by-step instructions I attempted to follow
[https://help.ubuntu.com/community/MacBookPro3-1/Lucid](https://help.ubuntu.com/community/MacBookPro3-1/Lucid)

---------  Install log                                       9/10/2010
#     My comments.
#err  Notes where there seems to be errors in the instructions.

Boot Camp Assistant (Applications/Utilities)
  Partition the HD:         88  :   60  GB
  # 60GB partition is labelled "Windows", no choice here.

Install rEFIt-0.14.dmg from refit.sourceforge.net
  Running on:
    EFI Revision 1.10
    Platform:  x86_64 (64bit)
    Firmware:  Apple 1.10
    Screen Output:  UGA Draw (EFI 1.10), 1440 x 900

Boot from CD
  System > Administration > Partition Editor
#err  Partition Editor is not on menu.  Used GParted instead.
  Delete new partition /dev/sda3.
  # Now have:
  /dev/sda1   fat32   EFI     200.00 MB     boot
  /dev/sda2   hfs+             87.88 GB
  unallocated                  60.98 GB

Install Ubuntu from CD
  dave-laptop
  ext4 filesystem
  install to "largest continuous free space"
#err Skip the advanced "install grub to /dev/sda3."  /dev/sda3 not on the list.

Fix the Partition Tables
  Select "partition tool" from rEFIt menu
  # Response is different than expected.  Screen says
  "Starting gptsync.efi"
  Current GPT partition table:
  ...
  Current MBR partition table:
  ...
  Status: MBR partiton table is invalid, partitions overlap.
  Error: Not Found returned from gptsync.efi 
  # This might have something to do with skipping the grub install above.

#err  Cannot fix the partition tables, as directed in help document.  There
#err  is no option to do so.  Hitting any key returns to the rEFIt menu.

# Cannot boot to Ubuntu from rEFIt menu.  System just freezes.

Try again install from CD.
Hold "c" while booting.
Select "Install Ubuntu" from menu.

# Ubuntu installer shows current partition table as:
  fre space                0     MB
  /dev/sda1   fat32        209   MB 
  /dev/sda2   hfs+         94355 MB 
  free space               1     MB
  /dev/sda3   biosgrub     1     MB
  /dev/sda4   ext4         62758 MB
  /dev/sda5   swap         2715  MB
  free space               0     MB

# What is biosgrub?  Maybe this is causing the problem.
Delete all partitions after /dev/sda2.
# Cannot save modified table.  Error says "No root file system is defined.

Try instead with GParted
Boot from Ubuntu CD.
System > Administation > GParted
Delete all partitions after /dev/sda2.
  /dev/sda5 has a lock icon, which needs to be removed by clicking
    Partition > SwapOff

Install Ubuntu from CD
Restart
rEFIt now shows two Linux systems (HD and CD)   ???

Install Ubuntu from CD
  install to "largest continuous free space"
  dave-laptop
  ext4 filesystem
  Advanced: Install boot loader on /dev/sda        ???
# Install looks normal, but restart crashes out.

Second restart OK.
Start rEFIt partition tool.
# Same error as before - partitions overlap.
Back to rEFIt menu.
Boot Ubuntu from HD.  Hangs at startup screen.

Boot Ubuntu from CD.
# Ubuntu installer shows partition table identical to above, including 
# biosgrub.

```

---

### Post by david.macquigg on 2010-10-09
> Running Virtualbox won't stop configd from locking up twice a day when running mobile broadband. Running Virtualbox won't stop the Apple X11 from refusing connections after mysterious events. Running Virtualbox won't give me back the memory that booting into OS X took when I wanted to get into Ubuntu, nor dozens of other reasons to change OSes. I was fed up with OS X, and wanted Linux. Instead of, not in addition to.

TP, thank you for at last answering my question why anyone would prefer dual boot over VirtualBox.  I have not encountered these problems myself, but that may be because I am not pushing the limits.   I still have Mac OSX 10.5 as the main system on my MacBookPro.

Sorry for suggesting B when your question was - How do I do A?  My understanding was that our objective (A) was simply to get Ubuntu running on a MacBookPro.

I encourage your efforts to "document the whole process with all dead ends and frustrations soon".  A wiki page would help get that started, and encourage others to participate.  What is lacking in the current documentation is a good overview of the alternatives (VMs vs partitioning).  We waste a lot of time pursuing what seems like the simpler option (partitions) only to find that this option has hidden problems, is not well supported, and may even be fighting what Apple wants - to weld their OS to their hardware.

I suggest that the basic choice of VM vs partitions be discussed in the first paragraph.  Then describe in some detail the problems you have encountered with one of the VMs (VirtualBox).   For example, what program are you using for mobile broadband?  It might be that someone using a different program doesn't see these problems, and they could add a note to your wiki page.  There might also be some settings in VirtualBox that could solve the problem.  Mac OSX is one of their supported platforms, and we might get some help on their forums.

There must be a dozen different ways to get Ubuntu running on a Macbook.  We need a well-organized tree of choices in our documentation.

---

### Post by srs5694 on 2010-10-09
> **inphektion said:**
> without reading this whole thread i can tell you right now that directly after the hfs+ partition mac wants a small 100-200mb slice.  its not formated anything just empty.  if you boot into mac mode and re-bootcamp a large partition you'll see it created again.  Instead of deleting the bootcamp part and that little chunk and re-partitioning i just carved up the bootcamp piece.  without that little piece there you can't upgrade mac osx ( i was stuck on leopard for a while which i why i know of this).

It might be worth reviewing Apple's [Secrets of the GPT](http://developer.apple.com/library/mac/#technotes/tn2006/tn2166.html) Web page, and particularly the "Advice for Partitioners" section. This section lays out how Apple recommends partitioning disks. I suspect the "100-200mb slice" to which you refer is actually an *unpartitioned* part of the disk. (The use of the word "slice" should be avoided when referring to unpartitioned space, since that word is synonymous with MBR partitions in some contexts, such as among BSD users.) Apple recommends putting 128 MiB of empty space after most partitions, and Apple's GUI Disk Utility enforces this. Without it, Apple's installer may refuse to install or upgrade the OS. Linux isn't fussy about this issue.

Another requirement is an EFI System Partition (ESP), which Apple creates as a 200 MiB partition. IIRC, the EFI spec says the ESP should be 100-200 MiB in size.

Incidentally, that document (written in 2006) is pretty firm (as is the EFI specification) in saying that the MBR of a GPT disk should contain *one* MBR partition, of type 0xEE, that covers the whole disk (or as much as MBR size limits permit). In other words, hybrid MBRs are verboten. It's ironic that Apple itself began pushing hybrid MBRs as a way to make its Boot Camp work, thus creating a whole string of problems down the road -- the very problems they warned about in their 2006 "Secrets of the GPT" document!

---

### Post by tpievila on 2010-10-11
> **srs5694 said:**
>  It's ironic that Apple itself began pushing hybrid MBRs as a way to make its Boot Camp work, thus creating a whole string of problems down the road -- the very problems they warned about in their 2006 "Secrets of the GPT" document!

Regarding this and your earlier comment about pure GPT setup: According to the rEFIt documentation ([http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/)), Linux currently needs BIOS or equivalent emulation mode to get accelerated 2d/3d, and at least in Intel Macs the only way to get into this mode is to boot the "legacy OS" via MBR. This is where my knowledge is second hand at best, but at least Google nor IRC could find any indication that this info would have been superseded (unfortunately). Would be great to find someone who actually knows why this is, and if anything can be done about it.

To get started on the documentation I still need to find out what exactly can cause the multiboot setup to break. After the last time I wrote here, I've also gotten a scary new bunch of error messages from rEFIt about not finding volumes and what not, but after clicking "any key to continue" it still gets to the boot menu and can boot to Ubuntu. Didn't try OS X during the weekend for the fear of breaking the whole thing down while away from home and my other computers.

---

### Post by srs5694 on 2010-10-11
First, on most real BIOS-based systems, a conventional GPT boot works just fine. Therefore, it's not clear to me why rEFIt requires a hybrid MBR. I can think of three possibilities:


[list]
[*]Apple's BIOS emulation is buggy in a way that necessitates use of a hybrid MBR. My [Legacy BIOS Issues with GPT](http://nessus.rodsbooks.com/gdisk/bios.html) page might help somebody interested debug such problems.
[*]The rEFIt boot loader may be crippled in such a way that it can only read MBR partitions. IMHO, if this is the case then it's broken by design. I'd look into trying to use GRUB 2 without rEFIt. (I don't know if that's possible, but it's worth investigating.)
[*]The rEFIt developers (or whoever insists that hybrid MBRs are required to boot Linux on a Mac) are mistaken. This would be the easiest fix, since no fix would be required, but it'd be a shame that so many peoples have gone through so much needless frustration.
[/list]


Second, the page to which you link is wrong on at least one other point: the "you need a MBR partition table to use LILO/GRUB" issue. I'm not sure about LILO (I've seen conflicting stories on it and my own tests have been inconclusive), but GRUB 2 definitely works on GPT-only systems. There are also patched versions of GRUB Legacy that work with GPT-only systems. (I think that the version of GRUB Legacy that Ubuntu offers as an option is so patched, but I'm not 100% positive of that.) My comments apply to these boot loaders on a conventional BIOS-based system, though; if there's some Mac-specific wrinkle involving a Mac's BIOS emulation mode, I don't know what it is.

---

### Post by tpievila on 2010-10-11
> **srs5694 said:**
> First, on most real BIOS-based systems, a conventional GPT boot works just fine. Therefore, it's not clear to me why rEFIt requires a hybrid MBR. I can think of three possibilities:


[LIST]
[*]Apple's BIOS emulation is buggy in a way that necessitates use of a hybrid MBR. My [Legacy BIOS Issues with GPT]("http://nessus.rodsbooks.com/gdisk/bios.html") page might help somebody interested debug such problems.
[*]The rEFIt boot loader may be crippled in such a way that it can only read MBR partitions. IMHO, if this is the case then it's broken by design. I'd look into trying to use GRUB 2 without rEFIt. (I don't know if that's possible, but it's worth investigating.)
[*]The rEFIt developers (or whoever insists that hybrid MBRs are required to boot Linux on a Mac) are mistaken. This would be the easiest fix, since no fix would be required, but it'd be a shame that so many peoples have gone through so much needless frustration.
[/LIST]


Second, the page to which you link is wrong on at least one other point: the "you need a MBR partition table to use LILO/GRUB" issue. I'm not sure about LILO (I've seen conflicting stories on it and my own tests have been inconclusive), but GRUB 2 definitely works on GPT-only systems. There are also patched versions of GRUB Legacy that work with GPT-only systems. (I think that the version of GRUB Legacy that Ubuntu offers as an option is so patched, but I'm not 100% positive of that.) My comments apply to these boot loaders on a conventional BIOS-based system, though; if there's some Mac-specific wrinkle involving a Mac's BIOS emulation mode, I don't know what it is.

rEFIt is not implying that it needs MBR, just that having an MBR triggers the BIOS emulation in Macs. Based on history, this makes sense: Apple introduced BIOS emulation as a firmware updated when it released Boot Camp, and Boot Camp specifically makes the bastard hybrids when it repartitions the hard drive for Windows. Based on googling it's also clear that at least before the video acceleration did really need the BIOS emulation, but I'm not sure if that situation has been improved on.

Also while Grub can now boot from GPT, I usually find this with disclaimers about the feature being relatively untested, so it just might be outdated info. Also they do specifically mention elilo as being a GPT capable bootloader, and mention that rEFIt is not even needed to boot Linux.

---

### Post by srs5694 on 2010-10-11
Thanks for your post, tpievila; that clears up a few things in my mind. I wonder what it is about the hybrid MBR that triggers Apple's BIOS emulation. I'm wondering if it might be possible to do the job by creating something that's less horrible than a hybrid MBR, such as creating a 0xEE protective partition that's just a little bit short. Alternatively, in principle you could partition the disk so that it's got a tiny little throwaway partition (even just one sector in size) at the very end of the disk and create a hybrid MBR that contains nothing but that one partition. That way, the 0xEE protective partition will cover all the interesting partitions on the disk, making dangerous screw-ups much less likely than would be the case with a hybrid MBR that includes all the regular partitions.

---

### Post by tpievila on 2010-10-12
> **srs5694 said:**
> Thanks for your post, tpievila; that clears up a few things in my mind. I wonder what it is about the hybrid MBR that triggers Apple's BIOS emulation. I'm wondering if it might be possible to do the job by creating something that's less horrible than a hybrid MBR, such as creating a 0xEE protective partition that's just a little bit short. Alternatively, in principle you could partition the disk so that it's got a tiny little throwaway partition (even just one sector in size) at the very end of the disk and create a hybrid MBR that contains nothing but that one partition. That way, the 0xEE protective partition will cover all the interesting partitions on the disk, making dangerous screw-ups much less likely than would be the case with a hybrid MBR that includes all the regular partitions.

I haven't been able to find a proper technical discussion on how the Apple EFI works. But just having the MBR there won't be enough, you need to boot the first bootloader from a MBR partition too, if I understood it correctly. Finding someone who actually has first hand knowledge about the EFI would be great, but I'm not sure how much effort anyone in the Linux community is yet putting there, there's no indication that the industry would be moving away from BIOS yet (though GPT will be here sooner than later given the 2TB barrier, thus the work on GPT enabled tools).

---

### Post by srs5694 on 2010-10-12
On EFI, the "first bootloader" is in the EFI itself. My understanding is that it reads files from the EFI System Partition to determine what to boot. None of this requires any MBR partitions (aside from the MBR's protective partition, which is part of the EFI specification); in fact, creating any MBR partitions aside from the protective partition is a flat-out violation of the specifications. Of course, this refers to standard EFI; Apple's implementation is said to be a bit weird, and their BIOS emulation mode clearly inserts some extra wrinkles. I don't know how rEFIt gets loaded or what its requirements are.

For general EFI information, you could read the relevant documents. Intel's [EFI page](http://www.intel.com/technology/efi/) includes links to the EFI 1.x specification; and you can find the UEFI 2.x specification [here.](http://www.uefi.org/specs/) Apple's EFI implementation is said to be closer to 1.x than to 2.x. I've read parts of both, but mostly I was interested in the GPT information rather than how the system boots.

---

### Post by cath0dez on 2010-10-14
I am running on an iMac, but I did run into the exact same situation as you. I use the following steps to get rEFIt working - it now either boots me straight into OSX or hands off to grub which takes me into Ubuntu.

*Lets assume that you already have free space on your hard drive and rEFIt installed and you can boot to the bootcamp loader by holding the option key.  Also, read the whole guide first - if you just did an install, deleted the bios partition, and synced the tables in rEFIt you can jump ahead to step 7.

1.  Boot to the lucid live CD/USB (I think you have to use bootcamp's loader on this one).
 
2.  Use Gparted to delete the partitions from the last install. You may have to turn off the swap partition before it allows you to delete it (right click on the partition, swapoff).

3.  Install to the largest continuous space/  Don't bother with any of the advanced options - grub is installed to to the ext4 partition by default.  Just click through and fill out your user info and do the normal install.

4.  DONT CHOOSE THE RESTART OPTION WHEN ITS FINISHED INSTALLING. You have already waited for the Live CD to boot once and you dont need to do it again.

5.  Go back to Gparted.  If you are dual booting OSX and went with the default install options the table should show:
/sda1=EFI,/sda2=NFTS+,/sda3=Bios (I think it has a bios flag on it), /sda4=ext4, /sda5=swap.

Delete /sda3.  I don't know the exact reason why its there, but its going to cause the overlapping partition error in rEFIt if you leave it.

6. Now you can do a full shutdown.  Go to rEFIt and sync the partition tables.

7. At this point (I think you have already gotten here once..) rEFIt is sync'ed but freezes on the penguin if you try to go straight to Ubuntu.  Restart your computer and hold down option to go to the bootcamp loader.  Ubuntu should show up as "Windows" on this page - boot it.

8. You should get to the grub prompt... yay.  All you need to do know is let it boot into the GUI and shut down (don't resart or log out). Next time the computer boots to rEFIt click on the penguin and it will take you to grub.  Any time you change your partition table you will need to use the bootcamp loader the first time, but from here out it should work.

Let me know if this gets you going.  I tried to figure out the logic of this process in another thread - there has got to be an easier way.  I cant see Ubuntu expecting the guy that bought his computer at a place called the "genuis bar" to be able to discern the dynamics of hybrid boot tables (no offense to mac users, I own two).

---

### Post by srs5694 on 2010-10-14
> **cath0dez said:**
> 5.  Go back to Gparted.  If you are dual booting OSX and went with the default install options the table should show:
/sda1=EFI,/sda2=NFTS+,/sda3=Bios (I think it has a bios flag on it), /sda4=ext4, /sda5=swap.

Delete /sda3.  I don't know the exact reason why its there, but its going to cause the overlapping partition error in rEFIt if you leave it.

If I understand you correctly, /dev/sda3 at this point is a [BIOS Boot Partition.](http://grub.enbug.org/BIOS_Boot_Partition) this is a partition that holds part of the GRUB 2 boot code when booting using GRUB on a BIOS-based computer. As described on the Web page to which I just linked, GRUB 2 is less reliable without it than with it. AFAIK, it's not required when using GRUB on an EFI system; however, as it seems you're using BIOS compatibility mode in this procedure, I'm not sure how GRUB will treat the system -- as EFI or BIOS. If the latter, it's best to leave the BIOS Boot Partition in place, from a GRUB perspective.

If the presence of that partition is triggering a bug in whatever creates the hybrid MBR, then the best solution is to fix that bug. Of course, that's something that you probably can't do, so as a practical matter for individuals, the best solution is probably to substitute another program when creating the hybrid MBR. I don't know what's creating the hybrid MBR in the procedure you're using, but I do know that the two Linux programs that are often used for this purpose are gptsync and my [GPT fdisk (gdisk or sgdisk).](http://www.rodsbooks.com/gdisk/) I just checked the latest version of GPT fdisk, and it does *not* create the duplicate 0xEE MBR partition, so it should be safe to use. (Some earlier versions had a hybrid MBR creation bug, but the symptom wasn't quite what I've seen reported rather frequently in these forums of late.)

FWIW, I've recently ordered a refurbished Intel-based Mac mini, so I'll be able to study all this stuff myself in detail. With any luck I'll be able to come up with a better solution to these installation problems than are currently being used.

---

### Post by cath0dez on 2010-10-14
I have no idea how grub is treating it.  This was really a trial and error process to get to these steps - they were the only way I could get hitch free, fast boots into both OS X and Ubuntu and not have to worry about the option/alt bootloader.

It seems like a pretty safe method so far for me.  I ended up shrinking my OSX partition and putting an ex4 partition before my original ex4 partion (it takes up the /sda3 label vacated by the bios) - the same procesess I used for the install worked to get this setup running fast.

---

### Post by tpievila on 2010-10-15
> **srs5694 said:**
> None of this requires any MBR partitions (aside from the MBR's protective partition, which is part of the EFI specification); in fact, creating any MBR partitions aside from the protective partition is a flat-out violation of the specifications. Of course, this refers to standard EFI; Apple's implementation is said to be a bit weird, and their BIOS emulation mode clearly inserts some extra wrinkles.

Well, like I mentioned, the hybrid MBR concept comes straight from Apple's Bootcamp. Before Bootcamp, there was no BIOS emulation whatsoever in Mac EFIs, so it seems pretty logical that it uses the hybrid to infer that the machine has been configured for Windows and thus requires acting like a BIOS.

---

### Post by tpievila on 2010-10-15
> **cath0dez said:**
> Any time you change your partition table you will need to use the bootcamp loader the first time, but from here out it should work.

It's wonderful how computers are logical machines and you can just deduct why they do what they do.

</sarcasm>

What on earth is the Apple EFI doing when it loads a legacy os... it shouldn't _modify_ any data on hard drives, should it? Can you compare your GPT and MBR after and before booting with EFI? And maybe also the MBR bootloader data (the first 440 bytes)?

Did you mean changing the partitions in Linux, OSX or both?

---

### Post by cath0dez on 2010-10-15
> **tpievila said:**
> It's wonderful how computers are logical machines and you can just deduct why they do what they do.

</sarcasm>

What on earth is the Apple EFI doing when it loads a legacy os... it shouldn't _modify_ any data on hard drives, should it? Can you compare your GPT and MBR after and before booting with EFI? And maybe also the MBR bootloader data (the first 440 bytes)?

Did you mean changing the partitions in Linux, OSX or both?


I'm sorry but I do not have all of this documented.  All I can tell you is that, in the event of rEFIt hanging on the penguin logo, you can use the Apple boot loader to boot to grub.  Maybe rEFIt is pointing incorrectly to /sda3 and the Apple boot loader corrects the error and ponts to the proper grub partition...  

It seems like the apple boot loader does a probe if anything changes from the last time it was ran - rEFIt doesn't seem to identify the correct partition when you run its sync command.

---

### Post by MountainX on 2010-10-16
> **cath0dez said:**
> I am running on an iMac, but I did run into the exact same situation as you. I use the following steps to get rEFIt working - it now either boots me straight into OSX or hands off to grub which takes me into Ubuntu.

*Lets assume that you already have free space on your hard drive and rEFIt installed and you can boot to the bootcamp loader by holding the option key.  Also, read the whole guide first - if you just did an install, deleted the bios partition, and synced the tables in rEFIt you can jump ahead to step 7.

1.  Boot to the lucid live CD/USB (I think you have to use bootcamp's loader on this one).
 
2.  Use Gparted to delete the partitions from the last install. You may have to turn off the swap partition before it allows you to delete it (right click on the partition, swapoff).

3.  Install to the largest continuous space/  Don't bother with any of the advanced options - grub is installed to to the ext4 partition by default.  Just click through and fill out your user info and do the normal install.

4.  DONT CHOOSE THE RESTART OPTION WHEN ITS FINISHED INSTALLING. You have already waited for the Live CD to boot once and you dont need to do it again.

5.  Go back to Gparted.  If you are dual booting OSX and went with the default install options the table should show:
/sda1=EFI,/sda2=NFTS+,/sda3=Bios (I think it has a bios flag on it), /sda4=ext4, /sda5=swap.

Delete /sda3.  I don't know the exact reason why its there, but its going to cause the overlapping partition error in rEFIt if you leave it.

6. Now you can do a full shutdown.  Go to rEFIt and sync the partition tables.

7. At this point (I think you have already gotten here once..) rEFIt is sync'ed but freezes on the penguin if you try to go straight to Ubuntu.  Restart your computer and hold down option to go to the bootcamp loader.  Ubuntu should show up as "Windows" on this page - boot it.

8. You should get to the grub prompt... yay.  All you need to do know is let it boot into the GUI and shut down (don't resart or log out). Next time the computer boots to rEFIt click on the penguin and it will take you to grub.  Any time you change your partition table you will need to use the bootcamp loader the first time, but from here out it should work.

Let me know if this gets you going.  I tried to figure out the logic of this process in another thread - there has got to be an easier way.  I cant see Ubuntu expecting the guy that bought his computer at a place called the "genuis bar" to be able to discern the dynamics of hybrid boot tables (no offense to mac users, I own two).

This is the only post in the whole thread that I understood.

I did understand enough from some of the other posts to gather that maybe deleting /sda3 isn't the best solution. But I also didn't see a single other suggested solution that looked approachable. So... what to do?

---

### Post by mediamind on 2010-10-16
> I am running on an iMac, but I did run into the exact same situation as you. I use the following steps to get rEFIt working - it now either boots me straight into OSX or hands off to grub which takes me into Ubuntu.

*Lets assume that you already have free space on your hard drive and rEFIt installed and you can boot to the bootcamp loader by holding the option key. Also, read the whole guide first - if you just did an install, deleted the bios partition, and synced the tables in rEFIt you can jump ahead to step 7.

1. Boot to the lucid live CD/USB (I think you have to use bootcamp's loader on this one).

2. Use Gparted to delete the partitions from the last install. You may have to turn off the swap partition before it allows you to delete it (right click on the partition, swapoff).

3. Install to the largest continuous space/ Don't bother with any of the advanced options - grub is installed to to the ext4 partition by default. Just click through and fill out your user info and do the normal install.

4. DONT CHOOSE THE RESTART OPTION WHEN ITS FINISHED INSTALLING. You have already waited for the Live CD to boot once and you dont need to do it again.

5. Go back to Gparted. If you are dual booting OSX and went with the default install options the table should show:
/sda1=EFI,/sda2=NFTS+,/sda3=Bios (I think it has a bios flag on it), /sda4=ext4, /sda5=swap.

Delete /sda3. I don't know the exact reason why its there, but its going to cause the overlapping partition error in rEFIt if you leave it.

6. Now you can do a full shutdown. Go to rEFIt and sync the partition tables.

7. At this point (I think you have already gotten here once..) rEFIt is sync'ed but freezes on the penguin if you try to go straight to Ubuntu. Restart your computer and hold down option to go to the bootcamp loader. Ubuntu should show up as "Windows" on this page - boot it.

8. You should get to the grub prompt... yay. All you need to do know is let it boot into the GUI and shut down (don't resart or log out). Next time the computer boots to rEFIt click on the penguin and it will take you to grub. Any time you change your partition table you will need to use the bootcamp loader the first time, but from here out it should work.

Let me know if this gets you going. I tried to figure out the logic of this process in another thread - there has got to be an easier way. I cant see Ubuntu expecting the guy that bought his computer at a place called the "genuis bar" to be able to discern the dynamics of hybrid boot tables (no offense to mac users, I own two).
Last edited by cath0dez; 2 Days Ago at 11:53 AM..

Thank you cath0dez - your instructions worked perfectly for my iMac (Snow Leopard & Ubuntu 10.10 dual boot)!

---

### Post by MountainX on 2010-10-16
> **mediamind said:**
> Thank you cath0dez - your instructions worked perfectly for my iMac (Snow Leopard & Ubuntu 10.10 dual boot)!

What model iMac do you have? My 11,1 iMac 27" won't boot with a LiveCD.

---

### Post by MountainX on 2010-10-17
> **srs5694 said:**
> 
If the presence of that partition is triggering a bug in whatever creates the hybrid MBR, then the best solution is to fix that bug.

I just realized that the Ubuntu 10.10 installer is creating this sda3 partition. (I guess everyone else in this thread already knew that.)

Now I'd like to know what is creating the hybrid MBR... rEFIt?

---

### Post by mediamind on 2010-10-17
> What model iMac do you have? My 11,1 iMac 27" won't boot with a LiveCD.

24" aluminum iMac 9,1 (purchased August 2009).

---

### Post by darkvad0r on 2010-10-31
Ok, so I just bought a new macbook pro (MacBookPro6,2) and after reading this thread I almost abandoned the idea of installing ubuntu on it.

I finally gathered the courage to do it and, based on [cath0dez' post]("http://ubuntuforums.org/showpost.php?p=9971694&postcount=26") and some common sense, and I'm glad to report that I now have a fully working dual boot with Leopard and Maverick. So here's what I did (your mileage may vary) :

1. install refit (though I'm almost sure it's not needed). In order to see the refit boot menu, you need to reboot TWICE

2. use the bootcamp assistant to make place for ubuntu

3. Boot the live cd (I tried booting an ubuntu flash drive made with unetbootin and one made with the ubuntu tool, and none worked, it appears it's a mac firmware bug, but I didn't find any reliable information)

4. Install ubuntu choosing manual partitioning : you will see 3 partitions /dev/sda1 is the efi boot partition, /dev/sda2 is the OS X partition, and /dev/sda3 is the partition created by the bootcamp assistant. Delete the last partition (/dev/sda3), create a root partition for ubuntu ("Use as: Ext4", "Mount to: /"), leaving enough free space for the last partition you'll create : the swap partition. At this point you'll have the following partitions : /dev/sda1 is the efi boot partition, /dev/sda2 is OS X partition, /dev/sda3 is ubuntu root partition and /dev/sda4 is the swap partition. Before proceeding to the next installation step,** choose /dev/sda3 as the device for boot loader installation on the drop-down menu**. Now you can finish the ubuntu installation.

> 6. Now you can do a full shutdown. Go to rEFIt and sync the partition tables **(you might not need this as the partition tables might already be synced)**
7. At this point rEFIt is sync'ed but freezes on the penguin if you try to go straight to Ubuntu. Restart your computer and hold down option to go to the bootcamp loader. Ubuntu should show up as "Windows" on this page - boot it.

8. You should get to the grub prompt... yay. All you need to do know is let it boot into the GUI and shut down (don't resart or log out). Next time the computer boots to rEFIt click on the penguin and it will take you to grub. Any time you change your partition table you will need to use the bootcamp loader the first time, but from here out it should work.


So basically, you should avoid letting the ubuntu installer do the partitioning, and install grub to the ubuntu root partition, then you can follow [cath0dez' post]("http://ubuntuforums.org/showpost.php?p=9971694&postcount=26") from step 6 to the end, and have a fully working dual boot.

---

### Post by Lingonsylt on 2010-11-02
I tried to follow darkvad0rs instructions and do the partitioning of the free space manually. For each partition I made, an empty free space of 1 MiB was automatically created, dont know why.
When I came to the "click advanced and choose to install grub on sda3"-step, it wouldnt let me put it anywhere else than default anyway.

So I tried cat0dez version and now it works. The sda3 partition that I deleted was labeled bios_grub and almost 2 MiB. Think it was created automatically, as happened when I tried to do the partitioning manually, and became the bios_grub-whatever just because it was there.

But I dont know this well, didnt understand much of the thred, else than the instructions I followed. Just know that it works now, and that next laptop I buy will be a PC that is know to work out of the box with Ubuntu...

> ...may even be fighting what Apple wants - to weld their OS to their hardware.

If thats true its a scandal. One of the marketing arguments for the macbook I bought was that it could be used with both windows and linux. If they are fighting that they are doing false marketing and should be suited! No,no, PC next time! Thanks anyway for helpful info.

---

### Post by sum_ozzi on 2010-11-13
Guys,

I had similar problems with setting up my MacbookPro with an 2.66 i7

I installed rEEIt before I started and initially after restarting all seemed fine.

Then I noticed that the rEEIt menu had disappeared unless I pressed a key or two during boot. (like the arrow keys)

When I managed to get the menu up I noticed that the Partitioning tool would tell me that my MBR was invalid and that partitions overlap.
<Whole Bunch of Photo's Showing this are here --> [http://gallery.me.com/noxid/100272](http://gallery.me.com/noxid/100272)

The rEEIt program wouldn&#8217;t fix this. Despite the problem both OS&#8217;s did seem to work, however for how long and how well was unknown. Since I wanted the rEEIT menu on boot I thought I&#8217;d try to resolve this further.

I tried the option of booting from the Live Unbuntu 10.0.4 LTS CD.

I noticed that unless I cold booted and held down the &#8220;c&#8221; key while booting I had problems with the CD even booting.  (ie. It would hang on the penguin boot logo)

Anyway after managing to start up the live Ubuntu CD. I then deleted the bootloader partition, which on my system was dev/sda3

On shutting down Ubuntu and restarting the Mac I automatically got my rEEIt menu. 

On choosing the Partitioning tool it then told me it wanted to Synchronise the GPT partition and the current MBR (Yes...! )

On accepting this it updated the MBR successfully. 
I rebooted the Mac another time.

On opening the Partitioning tool the next time  (See pictures) it told me my tables were synchronised and that there was no need to do further syncing. 

Problem fixed..
I am now able to boot into the MacOSX successfully.
I am now able to boot into Ubuntu 64bit successfully.
:guitar:

---

### Post by jjinux on 2010-11-21
I know this is kind of lame, but my solution to this problem was to not dual boot.  That made my life so much easier.  I just used a normal MBR and didn't install OS X.  Fortunately my wife has my old MacBook running OS X in case I need it.  I may eventually buy an external harddrive and put OS X on that for the rare cases in which I might need it.

---

### Post by MountainX on 2010-11-21
> **jjinux said:**
> I know this is kind of lame, but my solution to this problem was to not dual boot.  That made my life so much easier.  I just used a normal MBR and didn't install OS X.  Fortunately my wife has my old MacBook running OS X in case I need it.  I may eventually buy an external harddrive and put OS X on that for the rare cases in which I might need it.

Actually, I would have done the same thing. Compared with the alternatives, it's not that lame IMO. What stopped me from doing this was the other problem I hit - my graphics card sends all output only to the external monitor. So unless I have a second monitor hooked up to my iMac I see nothing but a blank screen.

---

### Post by dec1bel on 2011-01-11
It seems that the installer isn't installing Grub2 correctly when I follow darkvad0r's instructions for lack of a bios-grub partition.  Does anybody know more about this?  I've tried and re-tried this a few different times and I'm getting a fail for all of them.

---

### Post by Wnutt on 2011-12-26
We're now almost in 2012, but the post ([#26]("http://ubuntuforums.org/showpost.php?p=9971694&postcount=26")) of cath0dez saved my life while trying (really hard!) to install dual boot MacOS (Lion) / Ubuntu 10.04LTS on my MacBookPro2,1.

Many, many thanks, because I followed that documentation: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Everything went fine until the "freezed linux" on the final reboot. This documentation states to try to restart again. I did not work for me:

I tried to reinstall once again following cath0dez's instructions and it worked. I was especially the step 7 were it was more precise than the general howto.

THANKS!

Fred

---

### Post by imclerran on 2012-08-11
> **david.macquigg said:**
> 

```
=== Output from $ sudo fdisk -lu /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00004950

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   184696871    92143616   af  HFS / HFS+
/dev/sda3               1   184700927    92350463+  ee  GPT
/dev/sda4       184700928   307275775    61287424   83  Linux

Partition table entries are not in disk order
```

I am attempting to install Ubu 12.04 on my MBP 8,1. When booting to Ubu from rEFIt, i get a line of text telling me "No operating system found" I assume this is a problem with the MBR.

Attempted to correct the partition table using rEFIt, but that failed, so here I am. I read the first few pages of this forum, and observed the output David got, as shown in the quote. He clearly has two overlapping MBR partitions. However, when I run the fdisk list tool, my partition table does not appear to over lap. 

The fdisk output is as follows:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xad8d1b45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   391430623   195510492   af  HFS / HFS+
/dev/sda3       391430624   392700167      634772   af  HFS / HFS+
/dev/sda4       392701952   397002751     2150400   82  Linux swap / Solaris

Disk /dev/sdb: 2013 MB, 2013265920 bytes
255 heads, 63 sectors/track, 244 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     3932159     1966064   af  HFS / HFS+

```

---

### Post by Xon399 on 2012-08-15
My MBP 7,1 runs on Mountain Lion. Anyone can guide me how to use VirtualBox to run Ubuntu 12.04 on it?

---

