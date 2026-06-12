---
title: "GRUB bootloader at beginning of 1st Partition with Ubuntu System"
date: 2012-11-30
forum: Apple Hardware Users
---

### Post by Painted Turtle on 2012-11-30
We're trying to figure out how to put the GRUB bootloader and the Ubuntu system on the first partition.

We are using an imaging and deployment tool called "Deploy Studio" to create double and triple boot Macs. And this is what they suggest.

The Ubuntu installer appears to have an option to do this. But, so far our attempts to do this have not resulted in a bootable system. 

[INDENT][http://www.deploystudio.com/Tips/Entries/2009/10/11_Triple_boot_best_practices.html]("http://www.deploystudio.com/Tips/Entries/2009/10/11_Triple_boot_best_practices.html")[/INDENT]

Any ideas would be welcome. Thanks in advance for any help.

---

### Post by oldfred on 2012-12-01
Welcome to the forums.

Since related to Mac, moving to Apple sub-forum where those who know Macs can respond.

Now older but some info on Mac
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
       Boot loader comparison
[https://wiki.ubuntu.com/EFIBootLoaders](https://wiki.ubuntu.com/EFIBootLoaders)

    
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

Not sure if not installing Windows you need to worry about MBR. Everything should be just gpt.

---

### Post by Painted Turtle on 2012-12-01
The "Triple Boot" configuration is to boot Ubuntu, OS-X and Windows. So yes, Windows is an issue. 

But I think the bigger issue here is how to do what the link suggests in terms of putting the bootloader on the same partition with Ubuntu, as is suggested in the link.

Or am I badly misunderstanding something here?

---

### Post by oldfred on 2012-12-01
Since Apple does not use the newer UEFI you have to boot Windows in BIOS/MBR and have the hybrid gpt/mbr configuration. All I know is then you have to work hard to keep them synchronized.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

    
Hopefully someone that knows booting a Mac will offer some help as I know nothing.

---

### Post by Painted Turtle on 2012-12-06
Might anyone know how to install Linux "on the first partition, the GRUB bootloader at the begining of this partition (not in the MBR)"?

Those are the directions for installing Linux so that it can be imaged using a tool named Deploy Studio.

[http://www.deploystudio.com/Tips/Entries/2009/10/11_Triple_boot_best_practices.html]("http://www.deploystudio.com/Tips/Entries/2009/10/11_Triple_boot_best_practices.html")

---

### Post by trogdor1138 on 2012-12-06
I'm not sure why they're recommending that approach; it makes no sense to me.

I actually triple-boot myself, with:

OS X 10.8.2
Windows 8 Pro x64
Kubuntu 12.10 amd64

My GPT hard drive is set up as:

sda1: 200MB EFI system partition, holds GRUB (FAT32)
sda2: 200GB OS X partition (JHFS+)
sda3: 650MB OS X recovery partition (JHFS+)
sda4: 100GB Kubuntu partition (ext4)
sda5: 200GB Windows 8 (NTFS)

This works really well for me, but it does require that you set up Ubuntu in EFI mode. If you don't want to or can't do that, I would recommend doing:

sda1: EFI system partition
sda2: OS X partition
sda3: Ubuntu partition
sda4: Windows partition

This setup will allow you to have a hybrid MBR that exactly matches the actual GPT partitions. In this case, you would end up using either GRUB to boot Linux and chain-load Windows, or the Windows boot loader to chain-load GRUB and boot Windows. This is because both OS's would be operating under the same BIOS/MBR implementation; Apple computers don't magically provide a different MBR for each legacy OS.

rEFIt isn't a boot loader itself; it's a boot manager. The subtle difference is that rEFIt can't directly launch OS's. This means that although both Windows and Linux might show up separately in rEFIt, it's difficult to get them to boot independently. I don't use rEFIt or its derivatives because I feel they don't offer much benefit, and they're much more trouble than they're worth. You can easily set up multi-boot environments without them.

You might be able to find success by installing GRUB to the partition boot code, but I still don't like that idea. You would do this while setting up partitions in the Ubuntu installer. You should see an option of where to install GRUB, and you would simply select the root Linux partition.

If you do insist on going the rEFIt route, please use the much-improved fork, rEFInd: [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by Painted Turtle on 2012-12-07
This issue is NOT getting Ubuntu to run on a Mac.

The issue is how to install Ubuntu, so that you can image it with Deploy Studio and install it on many more Macs.  For those who are Windows users, Deploy Studio is sorta like a free version of Windows Ghost, but for the Macintosh. Schools often use it to quickly image 100s or even 1000s of Macs over a network.

For anyone reading this later, Deploy Studio works quite well with OS-X on Macs. It seems to work adequately with Windows partitions on Macs.

They provide some information about setting up a Triple Boot Mac. 
[INDENT][http://www.deploystudio.com/Tips/Tips.html]("http://www.deploystudio.com/Tips/Tips.html")[/INDENT]
And they say that one should:

[INDENT][FONT="Courier New"]-Linux
Install the system on the first partition, the GRUB bootloader at the begining of this partition (not in the MBR) and use a swap file instead of a dedicated partition,[/FONT][/INDENT]

And they have another one that says:
[INDENT][FONT="Courier New"]
Triple boot configurations require the Linux boot loader (GRUB or LILO) to be installed at be beginning of the related partition.[/FONT][/INDENT]

Since I'm a newbee to Ubuntu and Linux, I'm trying to figure out how to follow their advice. I tried ignoring it and that didn't work all that well either.

Again, I'm a newbee, but I think the deal is, that if the GRUB bootloader isn't part of the Linux partition, then it doesn't get copied up to the Deploy Studio Server and it doesn't then get copied to the new machine.

---

### Post by oldfred on 2012-12-07
Grub2 does not like to be installed to a partition but can be. Old grub legacy used to work just fine from a partition's PBR.

With grub2 your have to add the force option -f to get it to install to a PBR. And it will complain about blocklists. Block lists means it uses hard coded addresses to find the rest of its code not search functions. Then on a major update or even aggressive fsck a grub file may get moved and the address is wrong. You then have to reinstall grub to the PBR. Usually not often but not as reliable.

> Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 

    
       reinstall grub2
grub-install --help

    
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by trogdor1138 on 2012-12-07
> **Painted Turtle said:**
> This issue is NOT getting Ubuntu to run on a Mac.

The issue is how to install Ubuntu, so that you can image it with Deploy Studio and install it on many more Macs.  For those who are Windows users, Deploy Studio is sorta like a free version of Windows Ghost, but for the Macintosh. Schools often use it to quickly image 100s or even 1000s of Macs over a network

Again, I'm a newbee, but I think the deal is, that if the GRUB bootloader isn't part of the Linux partition, then it doesn't get copied up to the Deploy Studio Server and it doesn't then get copied to the new machine.

If this is the case, I don't see how installing GRUB to the partition will make a difference. Windows is going to need something in the MBR to boot it, and I don't see why this Deploy Studio would back up one MBR bootcode and not the other.

Regardless, during your install of Ubuntu you can select where to install GRUB. It's generally right when you verify your configuration before files are actually written and copied. I did an install of OpenSUSE just last night, and the option to change where GRUB is installed was presented on the verify settings screen. If you're dealing with an already existing installation, oldfred's instructions are exactly correct.

My overall point in my recommendations though is to help you get a setup that will be the most stable and reliable, through firmware updates and other shenanigans. Though it will run in other situations, OS X is happiest in multi-boot environments when: there is one, and only one EFI system partition on the disk (MBR partition code 0xEE), GPT partitions come first before hybrid MBR partitions, only one MBR partition is marked as active, and Windows is last.

Linux is different from OS X and Windows in these environments. For most people, a multi-boot environment on a Mac entails:

- OS X installs under a GPT partition and boots in EFI
- Linux installs under a GPT partition and boots in the CSM BIOS
- Windows installs under a hybrid MBR partition and boots in the CSM BIOS

The only reason I could see setting up the way they've described is to be able to use the Boot Camp Assistant in OS X, which is not at all necessary. The Boot Camp Assistant refuses to run if more than one partition comes after the OS X partition. Additionally, most Linux distributions are confused by Apple's hybrid MBR and overwrite with a single EFI protective entry. They probably want you to:

- Install Linux first, as Linux will overwrite any hybrid MBR with a single EFI protective partition
- Install OS X, so that the Boot Camp Assistant will be able to shrink the partition and create one for Windows
- Install Windows by using the Boot Camp Assistant

However, you don't need the Boot Camp Assistant. Intel x86_64 Macs will boot Windows installation media from any source, not just one burned by the assistant (with the exception of USB install media, which is only supported by certain Macs). The Boot Camp Assistant also downloads drivers for your Mac, but you technically don't have to have those either. Even if you want them, the assistant will still allow you to download drivers if it can't partition the drive. For actual partitioning, the command line utility diskutil can slice and dice partitions however you want.

For the reasons given by me above and oldfred in his posts, I really think you should keep away from installing GRUB on a partition if at all possible. However, as I mentioned above earlier the install process of Ubuntu does allow you to configure GRUB's install location.

---

