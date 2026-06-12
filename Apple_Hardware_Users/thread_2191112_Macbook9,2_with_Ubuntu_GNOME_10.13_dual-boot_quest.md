---
title: "Macbook9,2 with Ubuntu GNOME 10.13 dual-boot questions"
date: 2013-12-01
forum: Apple Hardware Users
---

### Post by solarcancerian on 2013-12-01
Hello fellow Ubuntu users!

I had a question regarding dual-booting an Ubuntu GNOME 10.13 installing with my Mountain Lion installation.

I had followed the instructions on [this page]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Detailed_How-To") (installing rEFit, Creating the ext4 and linux-swap partitions with GParted, etc.) But when I go to install it and manually configure the partitions, it has an error regarded the 'reserved BIOS boot partition' and how it is missed.

Should I create this partition to install it? I know Macs do not use a BIOS, they use EFI to boot.

Thanks so much for your help,
CJ

---

### Post by mr1shaggy on 2013-12-01
No, the only partitions you need to make are the ext4 and linux swap partitions. When it says that you didnt make a BIOS partition and that the system might not work properly just click continue. Itll work just fine. I have a Macbook pro 9,2 with Ubuntu 13.10 on it and it works just fine. You dont even really need the linux swap space either, all that Ubuntu will use that for is RAM. But if you have over 4gb of ram you should be fine, i have 8gb of ram and i dont have any problems

---

### Post by solarcancerian on 2013-12-01
> **mr1shaggy said:**
> No, the only partitions you need to make are the ext4 and linux swap partitions. When it says that you didnt make a BIOS partition and that the system might not work properly just click continue. Itll work just fine. I have a Macbook pro 9,2 with Ubuntu 13.10 on it and it works just fine. You dont even really need the linux swap space either, all that Ubuntu will use that for is RAM. But if you have over 4gb of ram you should be fine, i have 8gb of ram and i dont have any problems

Oh okay, thank you!

EDIT: Did you have any issues with syncing up the partition tables with rEFit?

---

