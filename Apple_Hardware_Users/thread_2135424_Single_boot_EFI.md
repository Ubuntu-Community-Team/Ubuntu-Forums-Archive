---
title: "Single boot EFI?"
date: 2013-04-14
forum: Apple Hardware Users
---

### Post by AllRadioisDead on 2013-04-14
Hi everyone,

I have a mid 2012 macbook air that I'd like to install Ubuntu on. I would look to boot through EFI and not the legacy bios, and I would like it to be a single boot installation (ie no Refit or dual booting).

I've been looking all over the internet and I haven't really found a solution, does anyone have a similar setup that can shed some light on this?

Thanks!

---

### Post by ajgreeny on 2013-04-14
You have to boot the CD or USB you are using to install in UEFI mode from the boot menu that will appear usually when you press a specific key, which key depends on your BIOS.

Having got the CD/USB booted into live mode, I suggest you use gparted to create a new partition table using GPT not ms-dos, then make a 200MB EFI partition at the start of the disk, then a new partition for root (/) of about 20GB, and the rest for /home, minus a swap of whatever size you want or need.  You can forget about swap being twice the size of your ram, and either use 2-4GB, or if you want to hibernate make it the same size as your ram.

For GPT partition tables there are no extended and logical partitions; all are primary.

See: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for lots more detail, which I think will be similar for your Mac installtion.

---

### Post by AllRadioisDead on 2013-04-14
Thanks for the reply. Just for clarification, should I be using the AMD64Mac ISO, or the regular AMD64 ISO?

---

### Post by whiteonline on 2013-04-14
From what I've read, the (U)EFI boot option was removed from the "Mac" image for compatibility; you'll want to go with the AMD64 ISO.

---

### Post by oldfred on 2013-04-14
I do not know Macs, but have these links:

 Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by AllRadioisDead on 2013-04-15
Thanks a lot everyone. Looks like I have a bit of reading to do before I attempt this.

---

### Post by GhettoMrBob on 2013-04-20
A simple way to single boot any Linux distro is to bless the partition after install (to avoid waiting at the white boot screen for ages). To do this, boot to an OS X install disk or USB and start up a terminal window and use this command (replace /dev/disk0s1 with the appropriate location of your install):

sudo bless --device /dev/disk0s1 --setBoot --legacy --verbose

Afterwards, there will a short wait at the white screen when booting and then it will boot to grub.

---

