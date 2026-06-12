---
title: "oops - help needed"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by sluggo123 on 2006-07-20
I'm having a problem with booting.  I did this one to myself - I had a new working 6.06 installation and got myself into a state where the X interface would not start.  After several failed attempts to restore the xorg.conf file, I decided to reinstall and simply deleted the partitions.

Unfortunately, this disk also has a WinXP installation on it, and now the linux boot loader errors out.  I can boot the Ubuntu CD, but I can't boot Windows.

Is there any way to gracefully recover so that I can boot Windows and re-install Ubuntu?

---

### Post by nalmeth on 2006-07-20
When you reinstall Ubuntu it will reinstall the GRUB boot-loader, is this what you mean? Or do you need to boot XP first for some reason?

---

### Post by Klemik on 2006-07-20
If you deleted partitions I think nothing can help you (except some non-free software recovery) :/
What is grub error ?
Post your /etc/fstab and partitions if possible.

---

### Post by sluggo123 on 2006-07-20
> **nalmeth said:**
> When you reinstall Ubuntu it will reinstall the GRUB boot-loader, is this what you mean? Or do you need to boot XP first for some reason?
I don't need to boot XP first.  When I try to re-install Ubuntu, I create the new partitions, designate the root and swap partitions, then begin formatting the new partitions.  The format process then errors out with a reference to a problem on the XP boot partition.  There are no other details.  The error message has a "go bac / continue" option, but I haven't tried to "continue".

When I try to boot windows the GRUB loader message comes up, but nothing happens after that.

Is it possible to manually edit the GRUB loader files?  Would this do any good?

---

### Post by nalmeth on 2006-07-20
Try this:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by sluggo123 on 2006-07-20
> **Klemik said:**
> If you deleted partitions I think nothing can help you (except some non-free software recovery) :/
What is grub error ?
Post your /etc/fstab and partitions if possible.

Here's my /etc/fstab
---
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda9 swap swap defaults 0 0
---

The disk has 4 ntfs partitions and approximately 15GB of unpartitioned space (which I was using for Ubuntu).

I don't recall the GRUB error - in fact, there may not have been any error message.  Iirc, it just shows "GRUB (version number)" and then halts.  I'll check that again, though.

Many thanks for your help =)

---

### Post by Klemik on 2006-07-20
According to your fstab file you dont have partitions setup or they just dont exist. Run fdisk and create linux partitions (ext3 for linux and swap for swap). Or just boot from ubuntu CD and make them using the installer.

---

### Post by sluggo123 on 2006-07-20
Okies, things are looking better, but I'm still concerned.  I ran through the installation process, this time telling the partitioner to "use the biggest chunk of unallocated space" and do it's magic on it's own.  The result of that is a working GRUB, a bootable Ubuntu, and a bootable XP.

The problem I'm seeing is that the ntfs partitions (present in the "Computer" panel) are not viewable under Ubuntu.  Ubuntu tells me that the devices cannot be mounted.

I booted XP and did a manual chksdk on all the partitions and got no errors.  I ran Partition Magic and it showed an error, a mismatch between the CHS and LBA values for a particular partition.  PM said that it would be able to correct the error but I declined and aborted.

Here's my fstab:
---

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda9       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

Is there enough info here to tell me how to correct the problems I'm seeing?  Can I trust Partition Magic to play nice with the Ubuntu partitions if I let it do what it thinks is necessary?

---

### Post by nalmeth on 2006-07-20
Do you notice anything wrong with either XP or Ubuntu?

I wouldn't fix anything until you know it's broken.

Here's how to get that ntfs mounted (read-only) on Ubuntu:
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

