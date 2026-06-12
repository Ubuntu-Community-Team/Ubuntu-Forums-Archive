---
title: "New partition strategy"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by leavingOS2 on 2007-01-05
After having some problems with achieving my multiboot setup with Ubuntu, I have a new partion strategy that I would appreciate some feedback (should it work? are there obvious disadvantages? etc.)

I had put /boot and / on separate partitions, but I suspect this lead to a problem with the download updates.  I noticed these comments in the Grub How To: "If /boot is mounted on another partition and you use update-grub, then you may run into problems . . . when grub boots, it looks at whatever partition it is installed on. update-grub (and grub-install) assumes that everything is in /boot. When /boot is on the same partition as /, then all is OK, as menu.lst will be in /boot/grub. If /boot is on a separate partition, then grub sees /boot as / . . . "

As an Ubuntu noobie, I think I'd like to preserve the simplicity of the download updates.  Here's my proposed solution:

Grub in the MBR (choose from Ubuntu and IBM Boot Manager)
IBM Boot Manager 1st primary 7MB (choose from OS2, Win98 and WinXP)
Win98 2nd primary 1.5GB
Ubuntu / root, /boot 3rd primary 6GB
Ubuntu swap 1st logical 1.5GB
Ubuntu /home 2nd logical 15GB
OS/2 3rd logical 1.5GB
FAT32 Data 4th logical 15GB
NTFS Data 5th logical 15GB

WinXP on 2nd hard drive

Is it ok to use ext3 for all Ubuntu partitions except for swap?

During Ubuntu setup, is it sufficient to specify root on the 3rd primary and /home on the 2nd logical?  Will it boot Ubuntu from the 3rd primary?  Will everything except my data files (in /home) install to the 3rd primary, which is what I intend, or do I need to indicate the partitions differently during setup?

Thanks

---

### Post by mahy on 2007-01-05
I use XFS wherever possible, then ReiserFS, then ext3. Benchmarking speaks clearly.

---

### Post by Stephen Howard on 2007-01-05
Is the IBM Boot Manager partition a bit redundant?  I think that grub will happily boot all the systems you have installed.

---

### Post by pseudonym on 2007-01-05
> **leavingOS2 said:**
> I had put /boot and / on separate partitions, but I suspect this lead to a problem with the download updates.  I noticed these comments in the Grub How To: "If /boot is mounted on another partition and you use update-grub, then you may run into problems . . . when grub boots, it looks at whatever partition it is installed on. update-grub (and grub-install) assumes that everything is in /boot. When /boot is on the same partition as /, then all is OK, as menu.lst will be in /boot/grub. If /boot is on a separate partition, then grub sees /boot as / . . . "
As an Ubuntu noobie, I think I'd like to preserve the simplicity of the download updates. 
Was that GRUB howto from tldp.org? Most documentation from that site is horribly out of date. I'm pretty sure GRUB is smarter than that these days. Because when I installed my hand-compiled kernel (which involves a GRUB update), GRUB was updated fine on my separate /boot partition. And kernel updates/installations is the only time update-grub comes into play, AFAIK. 

But if you feel more comfortable leaving /boot inside /, then go ahead. A separate /boot is only useful if you have more than one Linux distro installed, anyway. 

> **leavingOS2 said:**
> Here's my proposed solution:

Grub in the MBR (choose from Ubuntu and IBM Boot Manager)
IBM Boot Manager 1st primary 7MB (choose from OS2, Win98 and WinXP)
Win98 2nd primary 1.5GB
Ubuntu / root, /boot 3rd primary 6GB
Ubuntu swap 1st logical 1.5GB
Ubuntu /home 2nd logical 15GB
OS/2 3rd logical 1.5GB
FAT32 Data 4th logical 15GB
NTFS Data 5th logical 15GB

WinXP on 2nd hard drive
Other than the fact that I don't know anything about IBM Boot Manager (or OS/2), this looks fine to me. Will GRUB pick up IBM Boot Manager instead of the 'native' bootloaders of your other OSes?...

> **leavingOS2 said:**
> Is it ok to use ext3 for all Ubuntu partitions except for swap?
Yes. Reiserfs is fine, too. XFS is fast and good on very large files (I use it because I do video editing), but GRUB doesn't like being installed to it.

> **leavingOS2 said:**
> During Ubuntu setup, is it sufficient to specify root on the 3rd primary and /home on the 2nd logical?  Will it boot Ubuntu from the 3rd primary?  Will everything except my data files (in /home) install to the 3rd primary, which is what I intend, or do I need to indicate the partitions differently during setup?
Yes, yes, and yes. GRUB can also boot off of a logical partition, in case you didn't know.

HTH and welcome to Ubuntu! :)

---

### Post by louieb on 2007-01-05
Two of my four Linux PC's have a separate /boot partition, two don't. GRUB update hasn't had a problem with kernel updates either way. Getting GRUB to boot OS/2 will be interesting. Please post your menu.lst entry for it.. 

My experience with the installer is it doesn't care where you put your / partition or if you decide to mount your /home on another partition. As long as you have a / and swap partition it will happily go on its way.

In the mid 90's I maintained a fax server running OS/2. It was replaced by email and EDI. But I am curious did not know OS/2 was still around. What on earth are you using it for.

---

### Post by Sef on 2007-01-05
> In the mid 90's I maintained a fax server running OS/2. It was replaced by email and EDI. But I am curious did not know OS/2 was still around.

IBM's support for OS/2 was discontinued on 31 December 2006.

---

### Post by leavingOS2 on 2007-01-06
First, let me say many thanks to all for your comments and assistance.  While I have many years of experience setting up multiboot systems with Win and OS/2, I'm a complete newbie with Linux.  Now for a somewhat longwinded reply to a number of your comments and questions:

Stephen:

"Is the IBM Boot Manager partition a bit redundant?"

IBM's solution to booting from a logical partition above the 1024 cylinder is tied into use of it's boot manager (a specific implementation of LVM that is compatible for use with Linux, while OS/2 is not completely compatible with Linux' LVM implementation.  

I'm told by the OS/2 community that Boot Manager can boot Linux.  However, under this scenario, Grub would need to be installed on the /boot partition and not the MBR.  As a Linux noobie, I'm still trying to see if I can limit the complexity level (Ok, stop laughing at me <g>)

Pseudonym:

"Was that GRUB howto from tldp.org? Most documentation from that site is horribly out of date. I'm pretty sure GRUB is smarter than that these days."

Nope.  I saw it here: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
While I haven't proven to myself that the update caused a problem for Grub when /boot was on another partition, it is one of my leading hypotheses.  After partitioning my HD with OS/2's LVM (but not formatting any drives) and installing OS/2 and Win98, I successfully installed Ubuntu.  After reboot, it tells me there are 66 updates which install successfully.  Then rebooting to OS/2's LVM to add all of the bootable partitions to the Boot Manager, Win98 and OS/2 boot, but Ubuntu tells me "Partition not formatted."  

Aside <BTW This order for installation is recommended by the OS/2 crowd.  For those who didn't realize it was still around, a few interesting facts: While it has been many years since IBM actively marketed OS/2, they have supported it because a number of European banks were deeply invested in it.  Some development (e.g., Real Player compatibility) continued when one of these large clients was willing to pay, but often the technology would trickle down to the remaining community.  It seems that many (not myself) remaining OS/2 users are computer professionals that have moved onto Linux support for their profession.  There are a number of Linux style community development projects ongoing, but the smaller numbers of users and the obstacle of having the underlying proprietary operating system code has stifled much progress.  Ironically, IBM can't release the source code to the open source community because Microsoft, which partnered in the very early development (after the split, they released NT, which sometimes returns OS/2 error codes that were never changed) has a legal share in a number of key components.>

I did receive a response from an OS/2 forum on this Ubuntu install problem that the same problem was solved by allowing linux to install lilo to the MBR, add Boot Manager as a choice under lilo and add any other operating systems under Boot Manager.

However, after reading the comment in the GrubHowTo about /boot and root being on the same partition would make the update install happy, I'm considering doing this and the idea in the previous paragraph (but with Grub instead of lilo).

My original idea about having /boot separate from root was to free up space under the 1024 cylinder, where I had planned several operating systems and/or bootloaders that require such.

"Will GRUB pick up IBM Boot Manager instead of the 'native' bootloaders of your other OSes?..."  I have confirmed this with the gentleman from the OS/2 forum that suggested his solution (referenced above) might help me.

Louieb: "Getting GRUB to boot OS/2 will be interesting. Please post your menu.lst entry for it.. "  I was advised that Grub can launch OS/2's Boot Manager which would in turn boot OS/2.  While I haven't modified the menu.lst yet, here are the instructions I was provided with for doing so: "LILO (and presumably GRUB) replace the MBR code with code of their own and these boot the boot loader they belong to. It then decides what to do. Both ignore the 'active' flag and boot what they're told to as either their default choice, after some configurable timeout period, or the o/s that you select from their menu. BM counts as an 'o/s' as far as they're concerned. BM should still be marked as the active partition as it expects to be that way and then operates just as normal. You can still use it to boot anything that it successfully boots at present and just add the additional things to GRUB/LILO that BM will not handle. You have to add an 'other' section to LILO and tell it to boot the right partition number - not sure how GRUB handles it but it should have something similar."

"My experience with the installer is it doesn't care where you put your / partition or if you decide to mount your /home on another partition. As long as you have a / and swap partition it will happily go on its way."  It worked for me, until the first update.  As I said above, while it happened three consecutive times on reinstalls, I haven't attempted another reinstall and tried move Grub to /boot partition, where Boot Manager would be looking for it.

"But I am curious did not know OS/2 was still around. What on earth are you using it for."

See my comments above about "still around".  I've been using it as my home desktop computer operating system since 1994, as my personal economic vote against Microsoft.  In the last few years, as more and more effort was required to remain compatible with basic internet access requirments (flash, mp3, pdf, etc.) the payoff has diminished below the cost of learning linux.  After some research, Ubuntu is my choice.  

However, I have one program, my checkbook, with 12 years of data in it, that I would like to keep.  In fact, it is a Windows 3.1 program, which runs better under OS/2's Win31 emulation than it does under native DOS/Win31.  After restoring a backup of my OS/2 partition to my new disk1 (Disk Image 2.0) I've been getting a number of strange error messages.  I have about seven years of desktop settings invested in that backup, so I was really looking forward to avoiding a fresh install of OS/2.  At this point, with all the trouble in getting my computer to boot OS/2 with Ubuntu, I'm considering dumping it and installing DOS/Win31 to run my checkbook.

Thanks again.

---

### Post by leavingOS2 on 2007-01-11
louieb:

"Getting GRUB to boot OS/2 will be interesting. Please post your menu.lst entry for it.. "

Well, I have got everything working, for now from a boot floppy and I have yet to try to update my new install ("71 updates available").  Next I'll try to update my menu.lst on my /boot folder. 

My menu.lst as requested (note that grub menu points to OS/2's Boot Manager partition, which then boots OS/2):

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
# savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows 98 & XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# For booting OS/2
title		OS/2
root		(hd0,0)
makeactive
chainloader	+1

---

