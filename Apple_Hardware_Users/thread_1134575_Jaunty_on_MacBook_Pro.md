---
title: "Jaunty on MacBook Pro"
date: 2009-04-23
forum: Apple Hardware Users
---

### Post by freakalad on 2009-04-23
My MBP (SantaRosa) is still running Hardy 64.

I know that Jaunty (well, Ibex actually) has now brought in a lot of stability in drivers in hardware management.

If anyone does a full Jaunty install from scratch (on the MBP SP, or any other), could you please report back & let us know if it flies?
It's time to lobotomise my box...

Cheers

-J

---

### Post by Yashiro on 2009-04-24
I doubt Jaunty at this point in time is as stable as Hardy.

---

### Post by Chris Weaver on 2009-04-24
I must admit I'm going to wait a few weeks before wreaking my install. Although, there's a large itch to press the Upgrade button.

---

### Post by freakalad on 2009-04-26
Did a dist-upgrade on the system on my MBP, and did not work out too well :(

Expect things to improved as additional updates come out, but I'll likely have to do q fresh install (which may not be such a bad thing).

All-in-all I mush say this distro does not exactly blow me away, but I understand that many of the improvements are under the hood, where my MBP install was a bit lacking

---

### Post by transmition on 2009-04-26
I would wait a month. I just did a fresh install on my macbook, only to discover that my graphics card is blacklisted in compiz, which means to special effects, AWN, or transparent terminal.

---

### Post by rsglewin on 2009-04-27
I just did the distribution upgrade on a MacBook Pro 1,2 and was very pleasantly surprised - only a few things were broken or reset and I was able to get everything working normally again very quickly.  Nice job on this one!

---

### Post by Salohcin on 2009-04-27
Just did a fresh install of Jaunty (not an upgrade), and everything is working pretty well for me.  Wireless is actually working without a hitch now, where as it used to constantly freeze the system.

The only problem i found when doing the install, was that the mactel documentation is still be written for my model (4,1), and there doesn't see to be a lot of knowledge about how applicable the software in the mactel repos are, it doesn't look like many people have experimented enough to figure out where the bugs are.

Other than that - i'm running fine.

---

### Post by swarup on 2009-04-27
I am looking to purchase the best 17" laptop I can, and I do all my work in Ubuntu. After a lot of research and comparisons between the Lenovo W700 series, the Dell Precision M6400, the System76 Bonobo, and the Macbook Pro 17 " 5.2 (early 2009), I feel that the MBP is the best machine-- best engineered and best built. But my main question is this: I would be purchasing it to run Ubuntu on, and of all the above-listed machines, it sounds like perhaps Ubuntu is the most shaky on the MBP. From reading this thread as well as [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) and [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty), it all sounds a bit experimental. Is it risky to purchase this 17" MBP to use with Ubuntu? Am I asking for trouble? From the hardware perspective, I'm ready to purchase the MBP today itself. But from the Ubuntu perspective, I'm a bit concerned. Should I be?

---

### Post by freakalad on 2009-04-27
swarup: I'm pretty happy with Ubuntu on my MBP, though if you're very concerned with stability, I'd recommend LTS version (Hardy being the last).
If you wand better driver compatibility & cutting-edge features, run the latest distro (though I'd advise holding off for now, and wait for some minor bugs to get ironed out)
If you're very concerned about void'ing you EULA or warantee, install a VM server, like VirtualBox (FOSS counterpart to Parallels). But doing this would sacrifice some performance & no 3D

Others:
I also got an issue with my NVidia 3D drivers after a dist-upgrade; no compiz :(
For the other hardware; is everything OK? Sensors & monitors, IR remote, sudden motion sensor (/dev/input/...), keyboard backlight, power management, etc?
Been doing hacks on my machine for a while now, and getting pretty tired of hotch-potch patching. So far it's been good enough, but not perfect.

On the upside; my MBP (SR) hardware it virt-capable, so on my new/fresh setup I hope to be able to do some more advanced KVM stuff (& maybe a bit of Enomaly/Eucalyptus). Wonder if it'll be possible to run OS/X in it...

---

### Post by swarup on 2009-04-27
The MBP 5.2 17" (early 2009) has 4 GB of RAM, and to utilize that I'd want like to put the 64-bit Ubuntu onto it. Does the 64-bit run well on the MBP? 

As for Hardy vs Jaunty, I think I'd probably try Jaunty first, as the newer version. If it didn't work well, I could always go back to Hardy.

---

### Post by HeiniX on 2009-04-28
Xubuntu on Macbook Pro 3.1

Few days ago I installed Xubuntu 9.04 on my MBP. Up to now there are two big problems:
1. Wireless network acquisition does not work reliably. Sometimes it works sometimes it doesn't.
2. I have not found a way how to insert special characters like the "pipe" character, the "at" character etc. I installed the pommed package but that did not help.

Has anyone advice for the second issue?

In spite of all the trouble, have fun!

---

### Post by freakalad on 2009-04-28
TTBOMK, pommed has been depricated, though I may be wrong

---

### Post by undertakingyou on 2009-04-30
I just did a fresh install of Jaunty an a MBP 3,1. Can't get keyboard backlight to work because the hal-applesmc package isn't available yet. And the 'eject' key doesn't do anything at all. Anyone else have these issues?

---

### Post by freakalad on 2009-05-03
Did a full fresh install from scratch this yesterday on my MBP Santa Rosa 3,1.
Went REALLY well (a lot better than I expected).
Loosely based on these 2 articles (thanks a bunch, btw):
[https://help.ubuntu.com/community/MacBookPro3-1/Intrepid](https://help.ubuntu.com/community/MacBookPro3-1/Intrepid)
[https://help.ubuntu.com/community/MacBookPro4-1/Jaunty](https://help.ubuntu.com/community/MacBookPro4-1/Jaunty)

Trickiest bit was rEFIt. Set up very basic/skinny mac partition in order to install rEFIt hook.

Partitioning scheme (GPT-enabled HDD via mac install):
/dev/sda1 - 200M - EFI boot partition (don't touch once finished)
/dev/sda2 - 10G  - HFT+ OS/X (can mount & use this from within Ubuntu via hfsplus driver)
/dev/sda3 - 45G  - EXT3 root partition
/dev/sda4 - 45G  - EXT3 home partition
/dev/sda5 - 8.5G - SWAP partition
/dev/sda6 - 500M - boot partition

Had to install little bits like applesmc & pommed (keyboard backlight), but overall the install went VERY well, and didn't require too much fiddling.

Now that the system is pretty stable, I may consider a RemasterSys ISO.

Hoping to use the KVM installed (3.1 SR MBP is Hyper-V enabled, btw) on the system to hook into the OS/X HFS+ partition as a block device & so run the mac within Ubuntu. But more on that later

Thanks again for all your help, guys

- J

---

### Post by inphektion on 2009-05-03
> **swarup said:**
> The MBP 5.2 17" (early 2009) has 4 GB of RAM, and to utilize that I'd want like to put the 64-bit Ubuntu onto it. Does the 64-bit run well on the MBP? 

As for Hardy vs Jaunty, I think I'd probably try Jaunty first, as the newer version. If it didn't work well, I could always go back to Hardy.

I'm running Jaunty on the MBP 5.2 with 8GB ram so using 64-bit.
I have zero major issues left.  Only issues remaining for me are that it doesn't reboot (hangs on reboot) and the keyboard backlight doesn't work with the fn keys but I can get them working with a script to say on/off.

Other than that I'm all set even using ext4 on / and /home but ext3 on /boot.  I've contributed a lot to the mbp5,2 jaunty wiki and will keep it updated as any of my remaining issues get solved.  

Basically I'd say go for it.  It was my decision too as the best 17" hardware I could find.

---

### Post by freakalad on 2009-05-03
> **inphektion said:**
> Only issues remaining for me are that it doesn't reboot (hangs on reboot) and the keyboard backlight doesn't work with the fn keys but I can get them working with a script to say on/off.

pommed addresses the Fn-key & keyboard backlight issue quite well on mine.
Reboot, hibernate & power-management issues was a bigg-ish problem on my previous setup (Ibex, no rEFIt), but seems pretty stable thus far.
I've seen buggy issues relating to acpi(d) abound (bit of an issue on my Hardy desktop @ the moment), so it may be related to that.

Ubuntu's power-management of the MBP is still not as efficient as what it could be, compared to native OS/X, and is a bit of a concern, considering how hot my system runs. Battery-time is pretty sucky

Gone through powertop & applied suggestions, and used the CPU frequency control to set CPU-utilisation to "power efficiency", for what it's worth.

---

### Post by cyberdork33 on 2009-05-03
> **freakalad said:**
> 

Trickiest bit was rEFIt. Set up very basic/skinny mac partition in order to install rEFIt hook.

Partitioning scheme (GPT-enabled HDD via mac install):
/dev/sda1 - 200M - EFI boot partition (don't touch once finished)
/dev/sda2 - 10G  - HFT+ OS/X (can mount & use this from within Ubuntu via hfsplus driver)
/dev/sda3 - 45G  - EXT3 root partition
/dev/sda4 - 45G  - EXT3 home partition
/dev/sda5 - 8.5G - SWAP partition
/dev/sda6 - 500M - boot partition
you don't have to have OSX for rEFIt... Also, how are you booting with /boot on partititon 6? Are you sure you are not just using the root partition?

---

### Post by lambengolmor on 2009-05-04
Just updated from Intrepid to Jaunty on my macbookpro 3,1:

-Keyboard backlight works with the tutorial for 4,1

-Keyboard 3rd layer (|[]@ etc) have to be manually set in System -> Preferences -> Keyboard -> Layers -> Layers Options -> Third Level

-Following [this]("http://deekayen.net/macbook-pro-31-jaunty-setup") tutorial didn't helped much except for the wireless part: now it seems to have a better signal

-Touchpad didn't work well, actually in the beginning was awful. Now [I have fixed]("http://ubuntuforums.org/showthread.php?p=7205740#post7205740") it someway but I can't tell I'm satisfied (still tapping doesn't perfectly work, still cursor moves funny)

-Bluetooth seems to not work, but it could be I miss some packages

---

### Post by freakalad on 2009-05-04
> **cyberdork33 said:**
> you don't have to have OSX for rEFIt... Also, how are you booting with /boot on partititon 6? Are you sure you are not just using the root partition?

Installed rEFIt as per instructions. Boot-time & stability is much-improved this way. 
10G is not too bog a sacrifice to keep OS/X (tries keeping it on an external USB, but that was a bit flaky). Hoping to make use of KVM to mount the OS/X partition as a block device & run OS/X inside Ubuntu on my MBP. 
Will have to see how that goes.

Confirmed "/boot" loaded (/etc/fstab, referenced by UUID) & working an my last partition (sda6), though the OS/X HFS+ partition is the one flagged as bootable.
EFI/rEFIt on 200M primary part (sda1) loads 1st, set to boot "legacyfirst" (1s timeout), which then throws control over to GRUB on sda6 (1s timeout).

I see that linux/ubuntu/grub have some EFI/GPT tools around, but have not mucked about with it yet. (if it aint broken...)

---

### Post by cyberdork33 on 2009-05-05
> **freakalad said:**
>  Confirmed "/boot" loaded (/etc/fstab, referenced by UUID) & working an my last partition (sda6), though the OS/X HFS+ partition is the one flagged as bootable.
EFI/rEFIt on 200M primary part (sda1) loads 1st, set to boot "legacyfirst" (1s timeout), which then throws control over to GRUB on sda6 (1s timeout).Interesting. Can you post the output of /Applications/Utilities/Partition Inspector ?

rEFIt, by default is installed to the OSX partition not the EFI partition.

Also, keep in mind that you have two different partition tables that you are dealing with. The OSX partition might be marked as bootable on the GPT side, but not the MBR side...

> **freakalad said:**
> I see that linux/ubuntu/grub have some EFI/GPT tools around, but have not mucked about with it yet. (if it aint broken...)
you can actually try booting with grub-efi without modifying your current install (i.e. you can still boot in legacy mode normally.

---

### Post by lambengolmor on 2009-05-05
EDIT: keybord Fn key setting doesn't work for me. The temporary settings is fine, but all methods had failed to save that settings...

---

### Post by freakalad on 2009-05-05
> **cyberdork33 said:**
> Interesting. Can you post the output of /Applications/Utilities/Partition Inspector ?

rEFIt, by default is installed to the OSX partition not the EFI partition.

Also, keep in mind that you have two different partition tables that you are dealing with. The OSX partition might be marked as bootable on the GPT side, but not the MBR side...

you can actually try booting with grub-efi without modifying your current install (i.e. you can still boot in legacy mode normally.

Will post my "sudo fdisk -l" & "df -h" data a bit later (MBP's @ home).

Still getting to grips with the whole EFI/GPT partitioning/boot, so I don't want to break anything quite yet (all the bits & pieces are working well, so I'd like to keep it that way)

I thought rEFIt ran out of the 200MB EFI partition in a similar way that GRUB runs out of my "/boot" partition. Otherwise I see little reason for that partition to be there in the first place.

Not too sure what the stability of grub-efi is like, especially on a 64-bit environment. Once I'm a bit more informed & confident I may commit to it.

Using rEFIt has **significantly** improved my boot time & stability, compared to how it was in the monolithic installation before.

Was hoping rEFIt/EFI would open up more advanced booting features, like that of the "ExpressGate Pre-Boot OS"; having something like a functioning OS prior to the full OS being up. (but that's not a huge concern)

On a separate note; power management is better, but still not perfect. 
If put the MBP into hibernation & bring it back up again, the synaptic touchpad is not operational. To fix this I simply put it into suspend (close the lid/screen) & bring it back again, and it seems to work OK.
2-finger scrolling works fine (horz & vert), but I now have to trigger right-click with 3 fingers instead of 2. Which is actually not such a bad thing.

---

### Post by cyberdork33 on 2009-05-05
> **freakalad said:**
> Will post my "sudo fdisk -l" & "df -h" data a bit later (MBP's @ home).fdisk can only read the MBR partition table...

> **freakalad said:**
> I thought rEFIt ran out of the 200MB EFI partition in a similar way that GRUB runs out of my "/boot" partition. Otherwise I see little reason for that partition to be there in the first place.nope, unless you specifically placed it in the EFI partition, it is install in /efi/refit on your OS X partition.

The EFI partition exists because the EFI spec really requires it to be there (it is also used for firmware updates)

> **freakalad said:**
> Was hoping rEFIt/EFI would open up more advanced booting features, like that of the "ExpressGate Pre-Boot OS"; having something like a functioning OS prior to the full OS being up. (but that's not a huge concern)
rEFIt is an EFI executable. nothing is running except the Mac firmware at that point. rEFIt just gives you a nice interface to the bootselector already on the Mac (holding alt on statup will get you to the default selector). It also provides a few nice tools (also efi executables) and the partition inspector tool that I referenced above.

---

### Post by freakalad on 2009-05-05
Thanks for the info, cd33.
Obviously I don't understand it quite as well as I thought I did.

If I can port my "/boot" & GRUB into the 200MB primary (EFI) partition, I'd be a much happier camper. 
I think I read somewhere that GRUB2 has support for EFI, but at the moment it's not quite stable enough (same goes for EXT4).

Since the MBP hardware is still a [black box] to me (*hwinfo* & *lshw* can only tell you so much), regardless of how nice it is, I'm a bit hesitant to do anything that might break it. But I'll probably end up breaking it anyway (as I tend to do), so if you have any advice or references you think I should consult, I'll give it a try.

---

### Post by freakalad on 2009-05-06
> **cyberdork33 said:**
> Interesting. Can you post the output of /Applications/Utilities/Partition Inspector ?

You referring to the "Partition Inspector" under Mac? Will have to switch & post again.

In the mean time, I attached a screenshot of my gparted, fdisk & other disk info I can track down (just in case). Will amend with "Partition Inspector" screencap after reboot

fdisk
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26        1586    12530504   af  Unknown
/dev/sda3            1586        7513    47612848+  83  Linux
/dev/sda4            7514       13441    47616660   83  Linux

```

sfdisk
```

Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     25-     26-    204819+  ee  GPT
		start: (c,h,s) expected (0,0,2) found (1023,254,63)
		end: (c,h,s) expected (25,127,14) found (1023,254,63)
/dev/sda2   *     25+   1585-   1560-  12530504   af  Unknown
		start: (c,h,s) expected (25,127,15) found (1023,254,63)
/dev/sda3       1585+   7512    5928-  47612848+  83  Linux
/dev/sda4       7513   13440    5928   47616660   83  Linux

```

parted
```

Model: ATA FUJITSU MHW2120B (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   13.0GB  12.8GB  hfs+         Untitled                   
 3      13.0GB  61.8GB  48.8GB  ext3                                    
 4      61.8GB  111GB   48.8GB  ext3                                    
 5      111GB   119GB   8916MB  linux-swap                              
 6      119GB   120GB   559MB   ext2 

```

df
```

/dev/sda2              12G  9.0G  3.0G  76% /var/lib/libvirt/images/mac_hfs
/dev/sda3              45G  3.0G   40G   7% /
/dev/sda4              45G  233M   43G   1% /home
/dev/sda6             500M   15M  459M   4% /boot

```

---

### Post by freakalad on 2009-05-06
Partition Inspector (from rEFIt) data
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     25470647  Mac OS X HFS+
 3       25470648    120696344  Basic Data
 4      120696345    215929664  Basic Data
 5      215929665    233344124  Linux Swap
 6      233344125    234436544  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640     25470647  af  Mac OS X HFS+
 3       25470648    120696344  83  Linux
 4      120696345    215929664  83  Linux

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 25470648:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 120696345:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 215929665:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Partition at LBA 233344125:
 Boot Code: None
 File System: ext2
 Listed in GPT as partition 6, type Basic Data

```

Pretty weird that some partition inspectors see the EFI partition & other inspectors see the OS X HFS+ (sda2 / disk0s2) set with bootable flag

---

### Post by freakalad on 2009-05-06
...forgot to mention that the fEFIt config data IS present on the OS/X HFS+ partition

df from OS X
```

Filesystem      Size   Used  Avail Capacity  Mounted on
/dev/disk0s2    12Gi  9.0Gi  2.8Gi    76%    /
devfs          108Ki  108Ki    0Bi   100%    /dev
fdesc          1.0Ki  1.0Ki    0Bi   100%    /dev
map -hosts       0Bi    0Bi    0Bi   100%    /net
map auto_home    0Bi    0Bi    0Bi   100%    /home
/dev/disk0s6   500Mi   14Mi  459Mi     4%    /Volumes/UNTITLED

```

---

### Post by Romu on 2009-05-06
If you're not too much regarding about the wireless connection, yes Jaunty works well.

I've never got the wireless speed and quality I had on Hardy with the madwifi driver.

---

### Post by cyberdork33 on 2009-05-06
> **freakalad said:**
> Pretty weird that some partition inspectors see the EFI partition & other inspectors see the OS X HFS+ (sda2 / disk0s2) set with bootable flag
All the data seems normal for how you are booting.

The difference in the boot flag, is the difference between the GPT and MBR partition table. in the MBR table, the OSX volume is set as bootable (that is what you want since that is where rEFIt is) and in the GPT the EFI partition is set as bootable (which is correct as well).

I still don't know how you got grub to boot from partition 6, but if it works, it works.

---

### Post by freakalad on 2009-05-06
cd33, IYO, do you reckon that grub-efi & grub2 are stable enough?
Are there any advantages in implementing it & wouls it improve my boot time & stability, or would I only be complicating things needlessly?

---

### Post by cyberdork33 on 2009-05-06
> **freakalad said:**
> cd33, IYO, do you reckon that grub-efi & grub2 are stable enough?
Are there any advantages in implementing it & wouls it improve my boot time & stability, or would I only be complicating things needlessly?
If what you have works and you are happy with it, then leave it alone. If you want to try out grub-efi, then it would be helpful to those developing it.

---

### Post by freakalad on 2009-05-06
Tried looking at the [qemu efi-bios]("http://www.nongnu.org/qemu/efi-bios.tar.bz2") so that I can emulate EFI for my KVM clients, but that's a bust; 32-bit only requires Qqemu to be built from SVN (which isn't an issue in itself, but is needlesly complicated at the moment). It also replaces all cleint's BIOS, so I can only do EFI or BIOS; not both

Thanks again for the great advice

---

### Post by rumblpak on 2009-05-07
i got compiz working using the compiz-check program on the 180.53 drivers.  How do I make it so that right click is using only two fingers rather than three?

---

### Post by cyberdork33 on 2009-05-08
> **rumblpak said:**
> i got compiz working using the compiz-check program on the 180.53 drivers.  How do I make it so that right click is using only two fingers rather than three?


There should be a section on the touchpad for your hardware:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by sjatkins on 2009-05-20
Just install Kubuntu Jaunty on MBP.  What version of MBP?  Whatever was sold new in Jan. 2008.  How does one tell anyway?

So things look cool cept I can't get the beast to sleep correctly, specially on lid close.  Set up the power settings.  close the lid.  nada cept screen blanks.

If I tell it to sleep explicitly through the menus it does sleep but can't wake it up *until* I close the lid and reopen it.  When I do that the system does it wake from sleep noises, the disk powers up and the screen stays black.

SIGH.  I have been waiting years to get a version of linux I can run fulltime dependably on a MBP laptop.  Still not here.   What is the big deal about getting some basic laptop functionality correctly baked into the install?   This is hugely frustating.  

So you linux gurus out there, what are the magic incantations that will make this "just work"?

---

### Post by freakalad on 2009-05-20
For hardware info, run `lshw`.
Power-management is still not perfect, though getting close (you may have to install the additional components). This IS a bit of an issue in Linux, IMO, but is being resolved (this is due in large to vendor closed-source...politics)

On my MBP, pretty-much everything works well in Jaunty (9.04)

The *magic* trick is: research. 
Do your homework before scrathing your system, and even then you'll proably break something & have to start again...and again. 
Don't be afraid to fail; that's how we learn.
You may also want to have another machine spare that's able to connect to the net, for when you need to refence help, & download patched. 
Keep a CD/DVD-RW & emptuy USB flash disk spare

Check out the wiki's too. cyberdork33 here is doing an EXCELLENT job of looking after & catalogueing a lot of info relating to Ubuntu/Linux on Mac

---

### Post by maflynn on 2009-05-20
> **sjatkins said:**
> 
If I tell it to sleep explicitly through the menus it does sleep but can't wake it up *until* I close the lid and reopen it.  When I do that the system does it wake from sleep noises, the disk powers up and the screen stays black.

SIGH.  I have been waiting years to get a version of linux I can run fulltime dependably on a MBP laptop.  Still not here.   What is the big deal about getting some basic laptop functionality correctly baked into the install?   This is hugely frustating.  

I agree, but it appears from what I've read here the sleep issue is a bug that needs to be resolved in subsequent issues.  I tried upgrading/downgrading/using beta video drivers because the initial advice was that it was a video driver issue but I can confirm that's not the case at least with my MacBook Pro.

YMMV but I disagree with your assessment that Ubuntu is not ready to run full time.  I'm about 80% in Ubuntu, the other 20% is needed for some Mac specific apps that I've not found a linux counterpart. Aside from the sleep issue (which is a major headache) Its a very stable OS and has a lot to offer.

---

### Post by freakalad on 2009-05-20
I agree.
Ubuntu's been stable & ready for laymen desktop use since Hardy 8.04 (even earlier, depending on your requirements)

Other than a very few apps (1 or 2; most of which runs fine or better in Wine), there is very little reason not to completely switch over full-time to Ubuntu/Linux. 
You just can't beat `apt-get install`

In the CLI, type in lswh, and see if your CPU is para-virt capable. Odds are it is (despite all the gripes, Apple & M$ still make pretty good gear).

If that is the case, you can run windoze inside a VM; either KVM (the preferred Ubuntu & RHEL platform), or VirtualBox (re-branded as "Parallels" in the proprietary world).
Unfortunately I've been unable to mount my OS/X partition & fire it up inside KVM yet, due to the use of EFI, as opposed to BIOS

---

### Post by cyberdork33 on 2009-05-20
> **freakalad said:**
> In the CLI, type in lswh, and see if your CPU is para-virt capable. Odds are it is (despite all the gripes, Apple & M$ still make pretty good gear). as far as I know, all Core 2 CPUs are para-virt capable.

> **freakalad said:**
> If that is the case, you can run windoze inside a VM; either KVM (the preferred Ubuntu & RHEL platform), or VirtualBox (re-branded as "Parallels" in the proprietary world).
I hope you are not suggesting that parallels IS VirtualBox... ? They are similar, but are not the same thing. (Plus there is also VMWare)

---

### Post by freakalad on 2009-05-21
> **cyberdork33 said:**
> I hope you are not suggesting that parallels IS VirtualBox... ? They are similar, but are not the same thing. (Plus there is also VMWare)

Close-enough for laymen use. I'm into KVM myself, so I'm not paying it too much attention at the mo'.
VirtBox is FOSS, and runs OK on OS X, so it's a-OK in my book.

VMWare is VERY good software, and other than the actual OS, that was the only piece of software I actually forked $$s for a license (such good s/w & got such good service from the co, I didn't mind)

---

