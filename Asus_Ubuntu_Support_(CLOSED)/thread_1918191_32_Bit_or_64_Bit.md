---
title: "32 Bit or 64 Bit ?"
date: 2012-01-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by WebNewbie on 2012-01-31
Hi,

I've been out the loop for quite a bit, haven't built a system from scratch for about 6 years. Can't even seem to remeber the basics. So here's a few daft questions. First of all, back in the day's of 32 Bit, didn't have any chioce.

Now I'm thinking, what about 64 Bit !? do I need 64 Bit. I'm no too bothered about the cost difference, I just want a machine that will cope with everything I throw at it.

I read a couple of reviews on the ASUS mother boards, interested in the P8P67 range of boards, now comes the daft question ... if I buy a 64 Bit CPU, do I have to purchase a 64 Bit mother board ?

---

### Post by oldfred on 2012-01-31
Your question is not 32bit vs 64. In fact you will be hard pressed to find any chip now that is only 32bit, they are 64bit with 32 bit capability.

But each chip has a socket and the motherboard must support that socket. 

The ASUS [I][I]P8P67 use socket 1155 which is the Intel i3, i5 or i7 series of chips.

[http://en.wikipedia.org/wiki/LGA_1155](http://en.wikipedia.org/wiki/LGA_1155)
[/I] [/I]

---

### Post by WebNewbie on 2012-01-31
Thanks oldfred, the main reason why I ask is, I'm to build the new system as a dual boot, Ubuntu & Window 7. Would this mean that my wondows software and programs wouldn't work on my new machine ?

Just to clarify; 64 Bit Ubuntu as OS, on 64 Bit Intel i5 core, and windows 7 32 Bit ? :confused:

---

### Post by oldfred on 2012-01-31
Windows 7 will work as 32bit. 

But the new Intel chips/motherboards have an update from BIOS to UEFI. You can still use BIOS/MBR, but UEFI is the new thing. Windows 64 bit works with UEFI but 32bit will only work in BIOS/MBR mode.

If you have a hard drive over 1TB and install Ubuntu first it will format drive as gpt not MBR. Then your Windows will not install as with gpt it has to boot with UEFI and then has to be 64bit. If you install Windows 32 bit first it will just be MBR and will boot with BIOS mode. Best to figure out format/partition sizes and format in advance.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

---

### Post by WebNewbie on 2012-01-31
Wow, oldfred, your obviously very knowledgable on these things.
I'll have to hit the books, or should I say 'the net'. Not as straight forward as I thought.

When I say I'll be dual booting, one thing I have avoided at all costs for years, is actually putting two operating systems on one drive.

What I actually do, is install my 'main OS' on my prime drive. And the second OS, in this case windows 7 on my second drive.

If I purchased a windows 7 64 Bit version, then both systems would boot via UEFI, correct ?

---

### Post by oldfred on 2012-01-31
I suggest two drives if you can.

Then each has its own boot on its own drive. I do not yet have an UEFI system but hope to soon, so I have been following the issue. Grub2 has a few bugs with UEFI but some report success if they format in advance with gpt and the efi partition has to be the first partition. I am now only formating new drives with gpt and leaving 200 or 300MB for an efi partition as the first partition. But I will not be putting Windows on any new drives and only run my old XP drive occasionally. 

Some links as a starting point - quotes are from posts:
Older Windows info on gpt - 2008
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by WebNewbie on 2012-01-31
Thanks oldfred, very good info, lots to read up on.
Loads of links I wasn't aware of.
I'll re-post if I get stuck.

---

