---
title: "Difficulty Booting Windows 7 With Triple Boot (Mountain Lion/Windows 7/Ubuntu)"
date: 2013-03-02
forum: Apple Hardware Users
---

### Post by NinjaBlob on 2013-03-02
[FONT=arial]I'm pretty new to Ubuntu and Linux as a whole, so forgive me if I'm missing something obvious, but I've been trying to fix this for a few hours now with little luck, so I thought I'd post and see if I'm missing something.

So I've been running Mountain Lion with a Windows 7 Bootcamp partition for quite a while now, and decided that I wanted to add Ubuntu to the mix. Following the guide here ([http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)), I successfully installed reFIt and Ubuntu got both it and my Mac partition working fine. However, when I try to boot into Windows, it first brings up the grub bootloader, and then gives me the following error after I select Windows 7 from the list:

> [COLOR=#323232]Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:[/COLOR]
[COLOR=#323232]1. Insert your Windows installation disc and restart your computer.[/COLOR]
[COLOR=#323232]2. Choose your language settings and then click "next."[/COLOR]
[COLOR=#323232]3. Click 'repair your computer'.

[/COLOR][COLOR=#323232]If you do not have the disc, contact your system administrator or computer manufacturer for assistance.[/COLOR]
[COLOR=#323232]File: \Boot\BCD[/COLOR]
[COLOR=#323232]Status: 0xc0000225[/COLOR]
[COLOR=#323232]Info: An error occured while attempting to read the boot configuration data.[/COLOR][COLOR=#323232]
I looked this up online, and the consensus seemed to be to put in my Windows 7 disc and run the repair tool, but when I attempted to do so, the tool didn't recognize any of my partitions. I did some further research, and ended up following the instructions here ([/COLOR][http://ubuntuforums.org/showthread.php?t=1908210&highlight=triple](http://ubuntuforums.org/showthread.php?t=1908210&highlight=triple)) to attempt to fix my MBR table. After doing so, I was able to boot Windows 7 through the grub bootloader from my Bootcamp partition; however, when I attempted to boot Ubuntu, I received a "no bootable device" error. Interestingly, I could actually get Ubuntu to load fine by selecting my Windows partition in reFIt and [COLOR=#323232]then selecting Ubuntu in grub, but it's not really an ideal solution. Finally, I ran reFIt's partition checker tool, which apparently reset my MBR table to its previous state, as I now have the original set of errors again (working Ubuntu, failing Windows).

Here's my partition setup as given by reFIt's Partition Inspector:
> [/COLOR][/FONT]

*** Report for internal hard disk ***


Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    703534615  Mac OS X HFS+
 3      703534616    704804151  Mac OS X Boot
 4      704804864    851288063  Basic Data
 5      851290112    861052927  Linux Swap
 6      861054976    976773119  Basic Data


Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    703534615  af  Mac OS X HFS+
 3      703534616    704804151  ab  Mac OS X Boot
 4 *    704804864    851288063  83  Linux


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


Partition at LBA 703534616:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot


Partition at LBA 704804864:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active


Partition at LBA 851290112:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap


Partition at LBA 861054976:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 6, type Basic Data
[FONT=arial][COLOR=#323232]Does anybody know what could be wrong and/or how I could go about fixing this problem? Thanks in advance for any help!
[/COLOR][/FONT]

---

### Post by NinjaBlob on 2013-03-02
Just managed to fix it somehow! I'm not exactly why what I did worked, but here's the steps I took in case anybody finds this later:

1. Installed grub into the Ubuntu partition and removed it from the MBR

At this point, attempting to boot Windows should give a 0xc0000225 error.

2. Followed the MBR fixing instructions here: [http://ubuntuforums.org/showthread.php?t=1908210&highlight=triple](http://ubuntuforums.org/showthread.php?t=1908210&highlight=triple)

At this point, if you're where I was, attempting to boot Windows should give an 0xc000000e error.

3. Run the Startup Repair tool from the Windows install disc. Attempting to repair should automatically bring up a dialog asking you to repair and restart. Upon doing so and booting back into Windows, you may get another 0xc000000e error (I know I did); however, if you reboot again into Windows, it should work.

The end result is a working triple boot where Windows boots as if there is no Ubuntu installation (e.g. skips grub). You should be able to tell if everything's working from reFIt because the Linux and Windows options will say 'Boot from Partition X' (where X is the partition number) instead of 'Boot from Linux HD' or something like that. I'll post back if something goes awry, but for now, everything seems to be working!

---

