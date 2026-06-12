---
title: "Ubuntu on multi-partitioned system"
date: 2009-09-28
forum: Apple Hardware Users
---

### Post by MacUsers on 2009-09-28
Hi there,
It seems like I'm in trouble with no. of partitions + installing Ubuntu (9.04) on MBP (4,1)  and I just see only a few of us to mention having more than one partitions, so I thought I better ask.

I referenced this page:  [http://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](http://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) to install Ubuntu - where it says to put MBR in boot loader (grub) in /dev/sda3. I assumed, that was for the people those who have/had only a single drive for OS X (or those who have used Bootcamp to partition). I have 4 partitions (excluding EFI) for OS X and another two for Ubuntu.

```
maci:~ ss$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *250.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS OSX                     28.9 GB    disk0s2
   3:                  Apple_HFS Programs                21.0 GB    disk0s3
   4:                  Apple_HFS DataVault               75.0 GB    disk0s4
   5:                  Apple_HFS Projects                99.9 GB    disk0s5
   6:       Microsoft Basic Data                         22.9 GB    disk0s6
   7:                 Linux Swap                         1.0 GB     disk0s7
```So, I installed boot loader to /dev/sda6 and everything went fine during the installation. After that, I booted off the rEFIt disk (not actually have installed) to sync to partition table but it says there isn't any thing to sync. If I select the Linux icon in rEFIt ans enter, it freezes on the grey Tux logo; on only one occasion it went pass that stage and then freezes on a "blinking dash" screen.

If I press and hold "alt/option" key during the boot, I don't see any other option, other than OS X to choose. Any one knows what am I missing or what went wrong?

Thanks in advance for your help. Any thing tip[s]/ suggestion[s] would be higly appreciated. Cheers!!!

---

### Post by MacUsers on 2009-09-28
Does any one have an answer for me please? Just can't figure out why it can't be booted. Cheers!!!

---

