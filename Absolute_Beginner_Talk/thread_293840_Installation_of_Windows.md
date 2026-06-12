---
title: "Installation of Windows"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by skip910 on 2006-11-05
I need to reinstall Windows XP, but from my understanding, if I install Windows while I already Ubuntu 6.10 installed, Windows installs it's boot loader over Ubuntu's boot loader (grub). So, after I install XP, will I need to reinstall grub? How do I get to doing this? Or will XP boot loader let me be able to choose from Ubuntu & Windows?

Thanks in advance for any help that is provided.

---

### Post by Kateikyoushi on 2006-11-05
You could add linux to your NTloader but not recommended.

Follow these steps to restore grub after the install. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by skip910 on 2006-11-06
Well, I installed Windows XP and reinstalled Grub and everything went fine except one thing: my Windows partition isn't mounted while in Ubuntu. Before, there was a folder called "hda1" on my Desktop, but it isn't there anymore.

Suggestions?

Here is the contents to my fstab file:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4d717296-bef1-45ff-b6ca-42dad687383e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=EA58511F5850EBB7 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=4e539395-0d27-423a-8b54-693b252e0f5e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

