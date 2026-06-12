---
title: "Tripple boot OSX / Jaunty / Karmic"
date: 2010-02-25
forum: Apple Hardware Users
---

### Post by SwedishWings on 2010-02-25
I have tried a few times to install Karmic, in addition to to OSX and Jaunty on my macbook pro 5,1.

The OSX and Jaunty works like charm, however, i can't boot the Karmic partition - the screen just goes black and nothing more happens. 

My partition table:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       32020   256995830   af  Unknown
/dev/sda3   *       32021       33609    12762695+  83  Linux
/dev/sda4           33610       38809    41768855   83  Linux

```

sda2: OSX
sda3: Karmic
sda4: Jaunty

I've tried to reinstall grub2 on /dev/sda3 via the LiveCD, but when i run "grub-install /dev/sda3" it warns about that it's a bad idea, and suggest "/dev/sda" which i think is a bad idea as that would kill my OSX partition (i assume). I'm not sure how to proceed from this point.

Any ideas?

Thanks,
Mike

---

### Post by linuxopjemac on 2010-02-25
reinstalling GRUB2 should not be a problem on /dev/sda. It won't ruin your OSX partition. cannot you force it on /dev/sda3 ? maybe with a "f" or so ?

---

### Post by SwedishWings on 2010-02-25
> **linuxopjemac said:**
> reinstalling GRUB2 should not be a problem on /dev/sda. It won't ruin your OSX partition. cannot you force it on /dev/sda3 ? maybe with a "f" or so ?

Thanks for your reply!

When reading [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) it states:

[INDENT]... Also, on the last dialog of the installer, just before it actually starts installing, be sure to click the “Advanced” button and choose to install grub to /dev/sda3.[/INDENT]
Is this incorrect or miss leading?

Are you sure there is no chance of destroying the OSX installation when installing grub on /dev/sda ?

Many thanks!

/Mike

---

### Post by linuxopjemac on 2010-02-25
You might want to try this:


> How To Install GRUB to a Partition Boot Sector
grub-setup --force /dev/sda2
- this example installs /boot/grub/boot.img  to the boot sector of /dev/sda2
(The GRUB from the operating system you're working in will be installed to /dev/sda2).
NOTE: GRUB 1.96 didn't seem to like having it's IPL installed to a partition boot sector, it complained and required the use of --force to get it to work.

see [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html")

I really don't think it harms, I have never done it myself but other people did it and it worked. I even helped someone else with the same command.

---

### Post by linuxopjemac on 2010-02-25
In all cases I advise to make a clone of your hard disk before doing these things. I normally use Clonezilla for this.

---

### Post by Vishal Agarwal on 2010-02-25
It looks like, that you are missing swap partition. As per my know how that is a must to install the Linux system.
But you cannot create more then 4 primary partitions in one single HDD. SO you will need to create one extended partitions, where you will do swap and root partitions and then try to install Ubuntu. and It should work.
**[COLOR=Blue]Be careful, creating partitions will destroy your earlier data. Do all at your own risk.[/COLOR]**

---

### Post by SwedishWings on 2010-02-25
> **Vishal Agarwal said:**
> It looks like, that you are missing swap partition. As per my know how that is a must to install the Linux system.
But you cannot create more then 4 primary partitions in one single HDD. SO you will need to create one extended partitions, where you will do swap and root partitions and then try to install Ubuntu. and It should work.
**[COLOR=Blue]Be careful, creating partitions will destroy your earlier data. Do all at your own risk.[/COLOR]**

Thanks for your reply!

I'm kind of confused of what is going on here. According to fdisk i have 4 partitions. But if i look in gparted i see 5 partitions. I guess some must be located in an extended partition, but I can't tell which. See the attached screen dump from gparted.

Thanks,
Mike

---

### Post by Vishal Agarwal on 2010-02-25
As per the attached photo, it looks like that you can delete sda4 and sda5, and then recreate one  extended partition, where you will create the logical drives for swap and root partition.
As it looks like that 5 primary partition are there, so doing one extanded pertitions with as suggested logical drives, should work.

**[COLOR=Blue]Again I am repeating  for Data security. You should not loose your data, while playing with the partition table.[/COLOR]**

---

### Post by SwedishWings on 2010-02-25
> **Vishal Agarwal said:**
> As per the attached photo, it looks like that you can delete sda4 and sda5, and then recreate one  extended partition, where you will create the logical drives for swap and root partition.
As it looks like that 5 primary partition are there, so doing one extanded pertitions with as suggested logical drives, should work.

**[COLOR=Blue]Again I am repeating  for Data security. You should not loose your data, while playing with the partition table.[/COLOR]**

I can't blow my Jaunty on partition 4, as that is the one I currently use for development.

My idea was to try out Karmic on partition 3, before upgrading the Jaunty to Karmic on partition 4.

As far as i know, there can only be 4 primary partitions, so two of them has to reside in an extended partition - or am i totally lost here?

---

### Post by SwedishWings on 2010-02-25
> **linuxopjemac said:**
> How To Install GRUB to a Partition Boot Sector
grub-setup --force /dev/sda2
- this example installs /boot/grub/boot.img to the boot sector of /dev/sda2
(The GRUB from the operating system you're working in will be installed to /dev/sda2).
NOTE: GRUB 1.96 didn't seem to like having it's IPL installed to a partition boot sector, it complained and required the use of --force to get it to work. 

Thanks!

I just tried this, but get the same warnings and no improvement otherwise.

I'm thinking of doing what you suggested earlier - i.e. install grub on /dev/sda. Can someone else confirm that this will NOT blow OS X ability to boot?

I really have no time to restore everything from scratch...

/Mike

---

### Post by linuxopjemac on 2010-03-01
[http://ubuntuforums.org/showthread.php?t=1418885](http://ubuntuforums.org/showthread.php?t=1418885)

---

### Post by SwedishWings on 2010-03-01
> **linuxopjemac said:**
> [http://ubuntuforums.org/showthread.php?t=1418885](http://ubuntuforums.org/showthread.php?t=1418885)

I followed your earlier advice and installed grub2 on /dev/sda, and it works like charm. I now have a working triple boot.

Many thanks for your help!

However, I'm still puzzled by the fact that "fdisk -l" and gparted shows different partition table layouts (i.e. no swap partition at fdisk). When running either Jaunty or Karmic, they both find the swap partition and uses it. Also, Disk tool in OS X sees it, so i assume that fdisk fails to report that partition. Strange...

I have still to try grub-efi, that would be nice in order to use the 9400 GPU, rather than 9600 that makes my MacbBook run very hot (i ended up writing my own fan control daemon to keep it reasonable cold in the tropical climate here in Philippines). Have read quite a bit about it, but think i'll wait until grub-efi is easier to install and more tested.

Regards,
Mike

---

