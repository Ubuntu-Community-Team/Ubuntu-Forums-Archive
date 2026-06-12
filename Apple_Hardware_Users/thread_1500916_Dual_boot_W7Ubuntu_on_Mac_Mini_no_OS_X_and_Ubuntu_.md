---
title: "Dual boot W7/Ubuntu on Mac Mini: no OS X and Ubuntu is confused about my MBR."
date: 2010-06-03
forum: Apple Hardware Users
---

### Post by bigmamab on 2010-06-03
Well, ***I'm*** confused, but Ubuntu isn't sure what's going on either :)

Since Windows is pickier about boot tables, I installed it first, setting up the partitions in a dual-boot friendly way (deleted all existing partitions first): 40Gb NTFS, 39Gb unallocated space, and the 100Mb 'system reserve' that W7 likes to have. 
Formatted the whole drive to do this. 
Installed W7 as usual.
Booted up with Ubuntu 10.04 install disk and proceeded through the install till I got to the partition section when Ubuntu reported that no OS was installed and it was allllll unallocated space.

I booted into Ubuntu from the disk, and GParted tells me it's 75Gb of unallocated space, while the Disk Utility sees the partitions. fdisk gives me the error that 'GPT detected on /dev/sda' and to use GNU Parted. Despite this warning fdisk gives me the partitions that Disk Utility sees.

After some digging, it looks like my problem largely stems from a GPT/MBR hybrid partition table that Windows likely set up. But I would *think* that Ubuntu should be able to handle this. Or even if it's an EFI problem, doesn't 10.04 recognize all of these? Disk Utility does.

With no OS X I can't really put on rEFIt can I? There is no EFI directory to bless. 

So the question is: can I easily fix the GPT/MBR problem without having to put on OS X, put on rEFIt, delete OSX via W7 installation and THEN Ubuntu? 
My Google-fu is too weak to find the solution, because every document I've dug up so far all assumes that if you have a Mac, you want to keep an OS X partition on there.

Any assistance is greatly appreciated! Thanks!

---

### Post by srs5694 on 2010-06-03
I'm uncertain how Windows 7 will see the computer, or the drive, in your configuration. Windows 7 can boot from GPT disks on EFI-based systems, but I know that Apple's Boot Camp sets up a "fake" BIOS environment for Windows, and in such an environment, Windows will only boot from MBR. I don't know which way it'll work on a Mac without an OS X installation. I can conceive of three possible causes for your problems:


[list=1]
[*]The problem is a bad MBR configuration, such as the one I describe on [this Web page.](http://nessus.rodsbooks.com/missing-parts/index.html) If so, you could fix the problem by editing the MBR table in the way described. I think this is a bit unlikely, though.
[*]Your system has an old GUID Partition Table (GPT) in addition to a new MBR that is *not* configured with a GPT protective partition. This could be confusing GParted. If so, the solution is to either eliminate the GPT data structures, leaving an MBR-only disk, or to create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) similar to what Apple's Boot Camp sets up.
[*]You've already got a hybrid MBR configuration, but it's corrupt in a way that's confusing GParted. If so, you'll need to either eliminate the GPT data and the protective partition in the MBR (type 0xEE) or regenerate the hybrid MBR, using either the GPT or the MBR data as a base.
[/list]


In the case of #2 or #3, you can fix the problems with my [GPT fdisk (aka gdisk).](http://www.rodsbooks.com/gdisk/) You should be able to install a somewhat old but still serviceable version in an Ubuntu live CD by typing "sudo apt-get install gdisk" at a shell prompt; or download the latest version from the [project download page on Sourceforge.](http://sourceforge.net/projects/gptfdisk/files/) (I recommend the latter approach, if possible, since there have been quite a few improvements and bug fixes since the version in the Ubuntu repositories. Note you can use the Windows version if that's convenient.) Check the GPT fdisk project page, and particularly the sub-pages on [partitioning advice,](http://www.rodsbooks.com/gdisk/advice.html) [hybrid MBRs,](http://www.rodsbooks.com/gdisk/hybrid.html) and [repairing GPT disks,](http://www.rodsbooks.com/gdisk/repairing.html) for more advice.

If you want to create a disk with a plain MBR configuration, use the 'z' option on the experts' menu to destroy the GPT data.

If my hypothesis #2 is correct, then GPT fdisk may ask you whether to use the MBR or GPT data when it launches. Chances are the MBR data is correct, but you should check both of them to be sure.

If my hypothesis #3 is correct, then GPT fdisk will report the problems if you use the 'v' option. Regenerating the hybrid MBR (via 'h' on the recovery & transformation menu) will then be necessary. (You'll also need to regenerate the hybrid MBR if you use the MBR data as a basis for a new hybrid MBR if my hypothesis #2 is correct.)

Feel free to post again if you've got more specific questions. If you do, the output of "sudo gdisk -l /dev/sda" and "sudo fdisk -lu /dev/sda" will be helpful.

---

### Post by sha.goyjo on 2010-06-04
If I may step in and clarify a few things, it is not boot camp that sets up bios emulation, but rather the EFI (enhanced firmware interface) itself. One of the benefits of this is that it is possible to set up entirely non-GPT disks without the benefit of boot camp. This is why it is possible for you to nuke the GPT table completely, as was mentioned in the previous post. I can testify this because I am writing this message from a MacBook 1,1 with nothing but XP and Lucid. All on a pure ms-dos MBR table. So it is possible to do this, and indeed for your purposes (unless you intend to install OSX at a later date) probably a better and simpler option. Go for a full on MBR table and things will probably be better for you.

EDIT:
BTW I simply use gparted to clear the entire disk by creating a new ms-dos table across the whole thing. I don't think this should pose problems, but feel free to correct me if I'm wrong.

---

### Post by bigmamab on 2010-06-14
Sorry for the late reply, but thank you very much for the great info!

GDisk worked a treat, and as suspected, the problem was that GPT and MBR were both present. Deleting the GPT partition left only the MBR, which was immediately recognizable by the install process. Since I had proof that MBR alone would work (thanks!) I went with that.

GRUB now boots showing both Ubuntu and Windows 7, so I'm hoping  this problem is fixed. And with far less hassle then I was anticipating! *bonus points*

The only problem now is that the USB keyboard is dead at GRUB, so I can't select Windows 7.  Aaaargh...

I'm still in the mental triage stage with this one, as I just fixed the boot record problem this morning. I may have backed myself into a corner with no EFI for the USB keyboard (aluminum or otherwise). Once Ubuntu boots the keyboard works fine.

Thanks so much for your help!

---

