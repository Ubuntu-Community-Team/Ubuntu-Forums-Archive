---
title: "Installation Freezing on Vaio VGN-S580"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by enko on 2006-08-12
Just wondering if any of you have had any experiences installing any linux distro on a Vaio S-580. I've seen several people saying they had linux on their Vaio S-Whatever, yet every install I've tried has resulted in this same issue:

During the repartitioning process the installation freezes permanently. On Ubuntu, after booting from the LiveCD and running the gui installer the installation always freezes (no mouse response or drive access whatsoever) at 15% of "Installing System" during the "Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0) (sda)..." procedure. Suse 10 and Suse 10.1 Enterprise Desktop installations (network or cd install) also freeze during the partitioning process. The disks work fine on my desktop PC. I've heard that something to do with pcmcia/acpi can freeze the installation, but I've tried adding acpi=off and pnpacpi=off to the boot options without result.

Suse Enterprise Desktop installation freezes at "100% - Formatting partition /dev/sda2 (10.0gb) with reiserfs" using the 'Installation - ACPI Disabled' and normal install option.

My system is as follows:
Sony Vaio VGN-S580
Pentium M 1.73ghz
1.5gb ram
80gb hard drive
originally loaded with Win XP Home
cd/dvd-r

Any insight you could give would be most helpful.

Thanks

---

### Post by p_garyali on 2006-08-26
I have a Vaio FS730 and I was getting similar problem while installating Dapper. Once I select "Manaual Partition", it does not show anything [No partitions to select from], just the continue button is shown. 

If I press continue anyway, the installer crashes!

The same installation works on my Desktop!

---

### Post by coffeecat on 2006-08-26
I don't know whether this was the same issue that affected my Sony Vaio VGN-FS215B, but here goes anyway. I had successfully repartitioned with Acronis in Windows (Acronis can create Linux partitions) and had installed SuSE 10.0 and then 10.1 OK. Then I wanted to install Ubuntu, but the installer (live CD) came up with an error somewhere after the select partitions bit. So I tried installing Mepis - no go. Then Fedora 5 - again no go. It was then that I found that Gparted in the Ubuntu live CD was showing the whole HD as unallocated in spite of the fact that the installer recognised the partitions I had set up. I suspect it was something to do with the hidden recovery partition and/or something odd in the partition table. And I guess that this is what was causing the install failure

I imaged Windows with Acronis, backed up SuSE, set a disklabel with Gparted (which Gparted said was missing) and reformatted the whole HD. I restored Windows (to hda2 - it refused to go anywhere else :?) restored SuSE, and then succesfully installed Ubuntu and Fedora. I now have a quad-booting machine, but I use Ubuntu most of the time.

But of course! :wink:

---

