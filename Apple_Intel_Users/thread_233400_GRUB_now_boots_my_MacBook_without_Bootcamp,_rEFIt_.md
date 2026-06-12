---
title: "GRUB now boots my MacBook without Bootcamp, rEFIt or lilo."
date: 2006-08-10
forum: Apple Intel Users
---

### Post by Entity on 2006-08-10
FYI, I've managed to install Ubuntu 6.06 LTS on my MacBook and it boots using GRUB without BootCamp, rEFIt, elilo or lilo. I have submitted a Howto here on this site that shows how I've proceed. I'm waiting for a moderator to accept it. ;-)

In short, I've converted the GUID Partition Table (GPT) of my hard drive to an ms-dos partition table using the Disk Utility of the Tiger's disk 1.

After I installed Ubuntu using the LiveCD. It installs without the GRUB error because it can now fully understand the partition table. I needed to set the active partition using parted.

When the installation was complete, I had to install a patched version of GRUB (I created the .deb already and it is attached to the howto) in order to boot the system without hanging at stage2.

Voilà! I boot Ubuntu using GRUB and I don't any other OS installed. I didn't need BootCamp, rEFIt, elilo or lilo.

---

### Post by hajk on 2006-08-10
Interesting! I have just one question: does the GRUB menu allow booting of OS X as well?

---

### Post by Entity on 2006-08-10
Here's the [Howto]("http://www.ubuntuforums.org/showthread.php?t=233243"). ;-)

---

### Post by Entity on 2006-08-10
> **hajk said:**
> Interesting! I have just one question: does the GRUB menu allow booting of OS X as well?

It would need to be tested I guess. But I think that you can not install OS X on a hard drive with an MS-DOS partition table. It needs the GUID Partition Table. In fact Tiger's installer didn't let me do so.

Maybe the best solution would be to use an external drive on which there would be a GPT. I will be able to test that when I'll be back from Greece on monday night.

---

### Post by the_webers_inc on 2006-08-10
It is true that you can not install Mac OS X to a hard drive with an MS-DOS partition table, but I was able to get it to boot from one.  Here's what I did:

Made a disk image of my Current Mac OS X installation (.dmg) while I was booted off a seperate installation of Mac OS X that I have on my external HD.

Saved the image to the external HD.

Used Disk Utility in Mac OS X to partition the internal HD into 4 partitions: /, swap, fat32, HFS+.

restored the image that I had made previously to the HFS+ Partition I had just created.

Rebooted, held down the option key and sure enough the disk poped up as a boot option, selected it and was soon using my Main Mac OS X installation on my reformated MBR based HD.  I installed Windows XP right afterwords and now have 3 boot options when I hold down my option key at boot. Windows, Macintosh HD(my Main installation), Recovery HD(My Backup installation on my external HD).

I still have to install Ubuntu.  Hopefully your patch will make that a little easier.  The way I think that It will work is that I will have to use grub to chose between Windows XP and Ubuntu.  When I want to boot into Mac OS X, I just have to hold down the option key right after rebooting.

So heres how I think it will work:

Mac OS X

Turn on > Option Key > Pick Mac Partition > it boots.

Windows or Ubuntu

Turn on > Option Key > Pick Windows Partition > Loads Grub > Pick Windows XP or Unbuntu > it boots.

I will do some testing in regards to this subject to day if I have time.  I may be off base with some of these theories, so don't take them as fact.  I will post again when I know more.

T. J.

---

### Post by the_webers_inc on 2006-08-11
It worked!

I now have Ubuntu 6.06 LTS, Windows XP SP2, and Mac OS X 10.4.7 all installed on my internal HD (4 partitions, MBR) in my iMac.  I will write more about my experience when I have time.

T. J.

---

### Post by jedsen on 2006-08-20
This is very cool, thanks!

---

### Post by LostEvil on 2007-01-19
> **the_webers_inc said:**
> It worked!

I now have Ubuntu 6.06 LTS, Windows XP SP2, and Mac OS X 10.4.7 all installed on my internal HD (4 partitions, MBR) in my iMac.  I will write more about my experience when I have time.

T. J.

that's cool, but do u know if its possible to use more partitions as extended? (1 for win, 2 for mac and 3 for /home, ubuntu and swap), cause if not, thats the same as using boot camp & refit for triplebooting in GPT ...

---

### Post by DrCR on 2007-08-14
> **LostEvil said:**
> that's cool, but do u know if its possible to use more partitions as extended? (1 for win, 2 for mac and 3 for /home, ubuntu and swap), cause if not, thats the same as using boot camp & refit for triplebooting in GPT ...
Not quite -- it gains you an additional primary partition, the one the GPT table would be taking up otherwise.

My question -- do you guys have any problems with updates or firmware upgrades? Also, as previously asked, can extended/logicals be used?


I've been going through [this guide](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp) and just when I think I've got it setup right something crazy happens again, and (since I don't have an external HD) I have to start from scratch all over again. Would be really nice to just go MBR if possible. Besides, then I could go quad-booting, which I what I would actually like to do OSX, WinXP, Vista, Linux, (plus a universal storage partition). 

Note - it may be possible to gain some extra EFI-only partitions going with the hybrid setup- GPT, OSX, Storage (or Vista), WinXP. Then after syncing the GPT and MBR shrink down the WinXP partition and create more paritions *but don't sync again*. Then you *should* be able to install EFI-recognizable Linux in the newly created disk-space. -- This is what I'm shooing for now. Yes, it would be nice to just go MBR lol.

DrCR

______________
[SIZE="1"]A5N8X, 3500+ single-core Manchester, 2x512MB Corsair XMS, MSI 7600GT
S-12 430W, HR-05, Scythe Mime, VF900 modded with Scythe 80x25mm. Dual D12SL-12 Yate Loons
WD1200JB, WD3200JB, HD501LJ
[Dual,independant WinXP installs via Grub hiding](http://www.linuxforums.org/forum/installation/66476-howto-multiple-independent-winxp-installs-same-harddrive-via-grub.html), VectorLinux 5.1.1SOHO
------
MacBook Pro Santa Rosa, 2.2GHz,  WD Scorpio 250GB WD2500BEVS, Pending Tuxized Apple Logo Mod[/SIZE]

---

### Post by benanzo on 2007-08-14
Apple says they use the 200MB EFI partition at the beginning of the disk to store firmware updates when they need to be installed.  However, I nuked that partition a long time ago and have never had problems with firmware updates, so who knows.

The only way to get OS X onto an MBR disk is to install it normally then clone it and restore it to a disk with an MBR.  OS X will refuse to *install* to an MBR disk, but will run just fine if you just untar it onto one.  GRUB will boot Ubuntu, OS X and Windows just fine.  Therefore you can use just an MBR disk with 4 primary and as many logical partitions as you want.

---

### Post by entangled on 2007-08-14
I presume this still doesn't mean that you could go to an x86 PC, copy over the Mac OSX image and and boot up Mac OSX? The hardware would be different and probably incompatible. Has anyone tried it?

---

### Post by cyberdork33 on 2007-08-14
> **entangled said:**
> I presume this still doesn't mean that you could go to an x86 PC, copy over the Mac OSX image and and boot up Mac OSX? The hardware would be different and probably incompatible. Has anyone tried it?

This is a sensitive subject, but there are ways to run OSX on some PCs, probably not legally though.

---

### Post by DrCR on 2007-08-14
> **entangled said:**
> I presume this still doesn't mean that you could go to an x86 PC, copy over the Mac OSX image and and boot up Mac OSX? The hardware would be different and probably incompatible. Has anyone tried it?
Yeah, that's something on a totally different level. It's something I'd like to look into at some point. Not sure, but I don't believe there is a technically legal way to do it. If you research it enough though you could perhaps argue from your conclusion that it is still legitimate for you to do so (man-made laws conflict you know, aka DMCA & fair use). You could start your research [here](http://wiki.osx86project.org/wiki/index.php/Installation_Guides).


> **benanzo said:**
> Apple says they use the 200MB EFI partition at the beginning of the disk to store firmware updates when they need to be installed.  However, I nuked that partition a long time ago and have never had problems with firmware updates, so who knows.

The only way to get OS X onto an MBR disk is to install it normally then clone it and restore it to a disk with an MBR.  OS X will refuse to *install* to an MBR disk, but will run just fine if you just untar it onto one.  GRUB will boot Ubuntu, OS X and Windows just fine.  Therefore you can use just an MBR disk with 4 primary and as many logical partitions as you want.
Sweet! I'm going to have to pickup a [proper HD enclosure](http://oyendigital.com/) and try it out. Going to be starting uni in a bit here so naturally I don't want anything risky, but you convinced me in that regard. :) One really nice aspect is being able to use Grub hiding, which I've become addicted to over the years to keep WinOSes in check.


Can the OSX install r/w data to the logical partitions? I know EFI doesn't like logicals, just not sure if there are inherent OSX issues with them.


DrCR

______________
[SIZE="1"]A5N8X, 3500+ single-core Manchester, 2x512MB Corsair XMS, MSI 7600GT
S-12 430W, HR-05, Scythe Mime, VF900 modded with Scythe 80x25mm. Dual D12SL-12 Yate Loons
WD1200JB, WD3200JB, HD501LJ
[Dual,independant WinXP installs via Grub hiding](http://www.linuxforums.org/forum/installation/66476-howto-multiple-independent-winxp-installs-same-harddrive-via-grub.html), VectorLinux 5.1.1SOHO
------
MacBook Pro Santa Rosa, 2.2GHz, WD Scorpio 250GB WD2500BEVS, Pending Tuxized Apple Logo Mod[/SIZE]

---

### Post by cyberdork33 on 2007-08-14
> **DrCR said:**
> Can the OSX install r/w data to the logical partitions? I know EFI doesn't like logicals, just not sure if there are inherent OSX issues with them.

Shouldn't matter, EFI doesn't like logical or extended partitions because they don't exist in the definition of GPT (the partition table for EFI). I am pretty sure OSX has no problem reading a logical partition.

---

### Post by benanzo on 2007-08-14
The only limitation that OS X has (as far as MBR/GPT goes) is that Apple has designed the installer to refuse to install to an MBR disk without first formatting as GPT.  It will, however, read and write any supported filesystem on any partition (primary,extended) on any MBR disk it encounters.  To my knowledge, OS X has to be installed on an HFS or HFS+ partition.  I personally recommend using just plain HFS for greater compatibility on the GNU/Linux side, but it's trivial to read/write either filesystem.

---

### Post by ivesjd on 2007-08-15
I am definetly going to try this when I get my new 200GB harddrive. Am I correct in beliveing that all the OS's (OS X, XP and Ubuntu) will show up in grub?

---

### Post by DrCR on 2007-08-16
I booted up in Linux and used FDisk to delete all paritions, then played with dd a little -- dd if=/dev/zero of=/dev/sda bs=1MB -- and let that run for a bit to hopefully clear off any partition/boot records etc. at the beginning of the drive.

cfdisk is giving me a problem though. I may run dban (Darik's Boot and Nuke) on it for a bit. Should I setup the partition setup I would like now, or wait until after the OSX "install"?


Here's the kicker though -- how do I pull the SuperDuper!Free-created .dmg from a network WinXP share and put it on my MBP? 

I don't have another Mac nor even a firewire external drive. One way would be a OSX "LiveCD", customized with smfFanControl and SuperDuper!Free. Not sure if anyone here knows of a how-to or something to create one from your offical disks (I wouldn't really trust some iso online, and besides I'd like to customize it anyway) like a Linux LiveCD or BartPE. 

DrCR

---

### Post by Gen2ly on 2007-08-17
Anyone out there tried just using gparted to partition the drive?  I fail to understand why diskutils is needed.

---

### Post by benanzo on 2007-08-17
The only thing I've ever used **diskutil** for is creating HFS+ partitions, or resizing partitions where interaction with a journaled HFS+ partition is necessary.  Unfortunately I don't think any of the GNU utilities are up-to-snuff yet when dealing with Apple's Journaled HFS+ filesystem.

Other than that, parted/GParted work great for everything I've had to do.

---

### Post by cyberdork33 on 2007-08-17
I have moved and resized (made smaller) HFS+ (non-journaled) filesystems with gparted but it took a bit of repair afterwards to get things working.

---

### Post by ivesjd on 2007-08-20
> **benanzo said:**
> Apple says they use the 200MB EFI partition at the beginning of the disk to store firmware updates when they need to be installed.  However, I nuked that partition a long time ago and have never had problems with firmware updates, so who knows.
I thought that you weren't running OS X at all? So you wouldn't even have firmware updates am I correct?

---

### Post by DrCR on 2007-08-21
Currently running OSX, WinXP, and Linux on my MacBookPro MBRed hard drive. :D

Used a [simple USB to SATA adapter](http://www.google.com/search?hl=en&q=+VANTEC+CB-ISATAU2), and extra hard drive and my OSX disk1 to transfer an image onto the MBP's hard drive which I had previously changed to MBR from GPT.

Current Hard Drive Layout:
sda1 - OSX
sda2- WinXP
sda3 - Vista (pending MSDN come start of uni)
sda5 - Linux Swap
sda6 - Fat32 Storage
sda7 - Linux Distro
sda8 - Linux Distro
.. free space for more distros (WD 250GB Scorpio)
Just finised installing the new Sidux 3.1 to sda8 as the latest kernel has a few mac-specific support features. 


Currently though I have to hold the Option key to select an OS on boot: OSX or WinOS (Grub to WinOS or Linux) -- otherwise it just defaults to OSX. I would like to have a choice *every time by default*, like the way [refit](http://refit.sourceforge.net/screen.html) was. Has anyone been able to make this happen, perhaps with GRUB? I'm getting sick of holding the Option key.. :mad:



DrCR

---

### Post by pxwpxw on 2007-08-22
Have you tried running refit from a cd, or reinstalling it on Macosx to see if it still functions with the MBR partitioning?
I would be interested to know what happens.

---

### Post by cyberdork33 on 2007-08-22
> **pxwpxw said:**
> Have you tried running refit from a cd, or reinstalling it on Macosx to see if it still functions with the MBR partitioning?
I would be interested to know what happens.

I was thinking the same thing. Does rEFIt require a GPT?

---

### Post by pxwpxw on 2007-08-22
Dunno - I can boot a refit usb stick, from the Apple picker (option), and refit docs say efi does not require guid.

---

### Post by DrCR on 2007-09-14
Hum, I should indeed try loading refit back on it. I'm putting it on the back burner though -- don't want to blow up my lappy in the middle of a uni term lol.

One thing I'm working on right now is getting my native OS installs to boot up virtually in VMWare Fusion. The default "bootcamp" VM [COLOR="Navy"][hangs on Grub load though](http://www.vmware.com/community/thread.jspa?threadID=90873&tstart=0)[/COLOR], so my use of it may present a challenge. But once successful and combined with that universal data partition that can also be [COLOR="Navy"][mounted in the VMs](http://www.vmware.com/community/thread.jspa?threadID=102646&tstart=0)[/COLOR], I shouldn't have too much more to ask for besides MS going Unix based for their next os... ;)

Now the only time I should _have_ to boot into another OS besides OSX would be intensive gaming, which I will be doing only occasionally at the most.  :D

DrCR

---

### Post by DrCR on 2007-09-25
Just saw this in passing while looking for something else:

> Important: If your computer boots directly into OSX do this:
Startup OSX
1. open teminal and type:
sudo -s
nano /Library/Preferences/SystemConfiguration/com.apple.Boot.plist
2.add
<key>Quiet Boot</key>
<string>No</string>
<key>Timeout</key>
<string>15</string>
[http://www.insanelymac.com/lofiversion/index.php/t11640.html](http://www.insanelymac.com/lofiversion/index.php/t11640.html), Mar 14 2006

Something worth trying out and on my to-do list. :)

- - - - -

Right now trying to figure out how to reinstall WinXP onto sda2 as my WinXP OEM install, which I installed with a temp COA, won't accept my MSDN key. The problem is booting up with my new WinXP CD, it hangs/blank screens after "testing system configuration" or whatever on initial boot up. Apparently something to do with XP not liking my hard drive layout (surprise). :(  [link](http://support.microsoft.com/kb/314503)

Going to try to clear the mbr via dd after I make a backup.
[COLOR="Green"]dd if=/dev/zero of=/dev/hda bs=446 count=1[/COLOR]
Anyone know if OSX has anything important on the mbr?

Also going to try hiding all partitions via Grub before booting from the WinXP CD.

DrCR

_________________
[SIZE="1"]A5N8X, 3500+ single-core Manchester, 2x512MB Corsair XMS, MSI 7600GT
S-12 430W, HR-05, Scythe Mime, VF900 modded with Scythe 80x25mm. Dual D12SL-12 Yate Loons
WD1200JB, WD3200JB, HD501LJ
Dual,independant WinXP installs via Grub hiding, VectorLinux 5.1.1SOHO
------
MacBook Pro Santa Rosa, 2.2GHz, WD Scorpio 250GB WD2500BEVS, Pending Tuxized Apple Logo Mod[/SIZE]

---

### Post by pxwpxw on 2007-09-26
**DrCR**

If you are a boot segment hacker, you can see whats there with hexdump, and save it with dd to restore if the expected happens. Last time I looked the Macosx partiton had 0 in the boot sector, but no guarantees. MBR differs.

---

### Post by DrCR on 2007-09-26
I cleared the mbr using the following:
[color=green][COLOR="olive"]dd if=/dev/zero of=/dev/sda bs=446 count=1[/COLOR][/color]
after making a backup of it, and a backup of the partition table for good measure (bs=512 for mbr + partition table). Upon reboot, holding option only gave two choices, the OSX install and the WinXP BootCD. Unfortunately the WinXP uninstaller still had the same problem so I restored the mbr.
[COLOR="Olive"]dd if=dev.sda.mbr.446.backup of=/dev/sda bs=446 count=1[/color]

Still have no clue how I would reinstall WinXP with out destroying the existing partition table. Maybe it would work if I cleared the parititon table, and created a new table for only sda1 (OSX) and sda2 (WinXP) with the *exact* same settings, installed WinXP, and then restored the original parititon table or simply appended the remaining partition table vaules or perhaps let [TestDisk](/www.sysresccd.org) recover them. 

Not sure if the WinXP BootCD simply doesn't like what it sees on sda1's boot sector. But it installed just fine when all I had on the hard drive was OSX on sda1.
[SIZE="1"]To posterity, [<this link>](http://www.josephhall.org/grub_install_hda1.html) may help on figuring out this stuff.
[/SIZE]

Fortunately though for the time being the MS rep in India was gracious and went ahead and activated my intended temporary install of WinXP OEM  that I also have on my PC since I have a MSDN COA that I'm not using and I "simply didn't feel like going to the hassle of reinstalling just to use the (incompatible with WinXP OEM media) MSDN COA". :) :biggrin:

Now I just got to setup a nice RMClock config and get a good driver for and figure out a way to crank down the rediciously hot 8600M GT. The MBP runs *way* too hot. :mad: 
Maybe there's a way I can undervolt the vid (underclocking if necessary). Perhaps there are a few modded bioses out there already...

DrCR

______________
[SIZE="1"]A5N8X, 3500+ single-core Manchester, 2x512MB Corsair XMS, MSI 7600GT
S-12 430W, HR-05, Scythe Mime, VF900 modded with Scythe 80x25mm. Dual D12SL-12 Yate Loons
WD1200JB, WD3200JB, HD501LJ
Dual,independant WinXP installs via Grub hiding, VectorLinux 5.1.1SOHO
------
MacBook Pro Santa Rosa, 2.2GHz, WD Scorpio 250GB WD2500BEVS, Pending Tuxized Apple Logo Mod[/SIZE]

---

### Post by DrCR on 2007-10-29
Parted Magic's hacked GParted now allows direct ceation of HFS+ file systems.

> Patrick Verner has announced the release of Parted Magic 1.9, a single-purpose Linux distribution designed for partitioning hard disks: "[COLOR="darkRed"]Parted Magic 1.9. Updated packages: Linux kernel 2.6.23, ntfsprogs 2.0.0, ntfs-3g 1.913, Conky 1.4.7, BusyBox 1.7.0, jfsutils 1.1.12, PartImage 0.6.6, Parted 1.8.8, FUSE 2.7.0, xfsprogs 2.9.3. I added all i386 keymaps from kbd. There is a label changing GUI for ReiserFS, NTFS, ext2, ext3, XFS, and JFS. A few people asked for PhotoRec and it was added. I did some hacking on GParted and you can create HFS+ file systems directly from GParted now. Added support to name the location of the Parted Magic Squashfs in the syslinux.cfg. Some other bug fixes and script changes as well.[/COLOR]" Read the release announcement and changelog for more details. Download: pmagic-1.9.iso (36.1MB).
[http://distrowatch.com/?newsid=04556](http://distrowatch.com/?newsid=04556)

Now us OSXers don't have to blow away the whole partition table just to format a partition to HFS (you just got to *love* diskutil [/sarcasm] lol). :)

DrCR


___________________

---

### Post by cyberdork33 on 2007-10-29
> **DrCR said:**
> Parted Magic's hacked GParted now allows direct ceation of HFS+ file systems.


[http://distrowatch.com/?newsid=04556](http://distrowatch.com/?newsid=04556)

Now us OSXers don't have to blow away the whole partition table just to format a partition to HFS (you just got to *love* diskutil [/sarcasm] lol). :)

DrCR


___________________

Actually, you don't have to with leopard's disk utility either. Note this still doesn't allow growing existing partitions.

---

### Post by DrCR on 2008-07-12
Sorry to revive an old thread, but I would like to keep this all in one place if possible.

Anyone tried using NiBiTor to undervolt their GPU? Sounds like a great way to tame the heat. [There are known issues with some of the 8500M batches](http://www.digitimes.com/news/a20080704PD210.html). Hopefully the 8600M isn't also part of this problem. My afore mentioned MBP 3,1 in this thread is now out of warranty, so now I'm really ready to tinker with the hardware in attempt to kept it from cooking itself whenever I do anything intensive. If I can't undervolt the gpu sufficiently, I may even look into adding extra heatpipes to the stock HFS setup.

I noticed the latest firmware update balks at "non-standard" HDD setups. Looks like firewire-attached EFI/GPT OSX installs are our only route from here on out.


DrCR

---

### Post by cyberdork33 on 2008-07-16
> **DrCR said:**
> Sorry to revive an old thread, but I would like to keep this all in one place if possible.

Anyone tried using NiBiTor to undervolt their GPU? Sounds like a great way to tame the heat. [There are known issues with some of the 8500M batches]("http://www.digitimes.com/news/a20080704PD210.html"). Hopefully the 8600M isn't also part of this problem. My afore mentioned MBP 3,1 in this thread is now out of warranty, so now I'm really ready to tinker with the hardware in attempt to kept it from cooking itself whenever I do anything intensive. If I can't undervolt the gpu sufficiently, I may even look into adding extra heatpipes to the stock HFS setup.

I noticed the latest firmware update balks at "non-standard" HDD setups. Looks like firewire-attached EFI/GPT OSX installs are our only route from here on out.


DrCR
This really has nothing to do with this thread. You should post new topics in the new Apple Users Forum.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by DrCR on 2008-07-18
Roger, wilco.

---

