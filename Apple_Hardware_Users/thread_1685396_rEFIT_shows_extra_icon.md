---
title: "rEFIT shows extra icon"
date: 2011-02-10
forum: Apple Hardware Users
---

### Post by Wunala Dreaming on 2011-02-10
Hello everyone! I had my MacBook configured with a triple boot (Windows 7, Mac OSX and Ubuntu 10.04). Everything was working perfectly until I decided to upgrade to Ubuntu 10.10 and screwed everything up haha. 

I formated the Ubuntu partition and installed 10.10 on it, but I made the mistake of not selecting the correct place for the boot loader. I went the non confusing way and decided to format the Ubuntu and Windows 7 partition to start all over again.

The problem si this, for some reason rEFIT shows a Linux partition when there isn't any, I just have my HD partitioned like this:

[IMG]http://img607.imageshack.us/img607/3912/particiones.th.png[/IMG]

This is what rEFIT shows:

_[IMG]http://img404.imageshack.us/img404/1271/refit.th.jpg[/IMG]_

The partitions are empty, I haven't installed any OS yet.

Do you know how can I delete that extra Linux icon? Thanks!

---

### Post by bdentremont on 2011-02-14
This may be too simplistic to deal with your problem, but my experience with rEFIt is that is that it offers to boot any available media based on the OS associated with its file system type, even if the content of the partition is not bootable.  For example, if I connect an external drive with a completely empty NTFS partition, rEFIt will offer to boot Windows.

---

### Post by coolbeans777 on 2011-02-20
Well don't trust me on this because I'm not a rEFIt guru or anything, but I get two icons when I install grub onto a linux partition rather than the entire hard drive.  However, because you have a triple-boot goin, I don't know if installing grub on the entire drive would interfere.

---

### Post by dubmartian on 2011-02-21
seems like refit handles usb partitions differently than internal...by fs rather than pt's? ..but im also no refit expert. that said, i have grub installed on sda3 to boot ubuntu on sda6. if i then install grub on sda6, an extra linux icon appears. before i researched how to get rid of it, i restored a blackup image to sda6 with clonezilla and the extra icon was gone after rebooting. i can only assume it had something to do with clonezilla not restoring partition tables by default when restoring an image. so refit then doesnt find it in the gpt?

---

### Post by Tu1J4kXk8NUhMz on 2011-02-22
> **bdentremont said:**
> This may be too simplistic to deal with your problem, but my experience with rEFIt is that is that it offers to boot any available media based on the OS associated with its file system type, even if the content of the partition is not bootable.  For example, if I connect an external drive with a completely empty NTFS partition, rEFIt will offer to boot Windows.

You've actually stumbled on a gparted bug. The reason NTFS shows up as bootable (with or without any OS installed) is because gparted (and most partition software, from my understanding) marks any and all NTFS partitions with a MSFTRES flag. There are ways to clear this, though it's never bothered me enough to try any.

> **Wunala Dreaming said:**
> Hello everyone! I had my MacBook configured with a triple boot (Windows 7, Mac OSX and Ubuntu 10.04). Everything was working perfectly until I decided to upgrade to Ubuntu 10.10 and screwed everything up haha. 

I formated the Ubuntu partition and installed 10.10 on it, but I made the mistake of not selecting the correct place for the boot loader. I went the non confusing way and decided to format the Ubuntu and Windows 7 partition to start all over again.

The problem si this, for some reason rEFIT shows a Linux partition when there isn't any, I just have my HD partitioned like this:

[IMG]http://img607.imageshack.us/img607/3912/particiones.th.png[/IMG]

This is what rEFIT shows:

_[IMG]http://img404.imageshack.us/img404/1271/refit.th.jpg[/IMG]_

The partitions are empty, I haven't installed any OS yet.

Do you know how can I delete that extra Linux icon? Thanks!

I had the same issue. Here's my thread...
[http://ubuntuforums.org/showthread.php?t=960993](http://ubuntuforums.org/showthread.php?t=960993)

But here's where you'll probably find the answer...
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

> **dubmartian said:**
> seems like refit handles usb partitions differently than internal...by fs rather than pt's? ..but im also no refit expert. that said, i have grub installed on sda3 to boot ubuntu on sda6. if i then install grub on sda6, an extra linux icon appears. before i researched how to get rid of it, i restored a blackup image to sda6 with clonezilla and the extra icon was gone after rebooting. i can only assume it had something to do with clonezilla not restoring partition tables by default when restoring an image. so refit then doesnt find it in the gpt?

Refit actually just handles external and internal hard drives the same as Mac OS X does. Refit is really just concerned about finding bootable media. I think that it looks for GRUB (or it's like), in the case of Linux.

---

### Post by srs5694 on 2011-02-22
> **teamjh14 said:**
> You've actually stumbled on a gparted bug. The reason NTFS shows up as bootable (with or without any OS installed) is because gparted (and most partition software, from my understanding) marks any and all NTFS partitions with a MSFTRES flag. There are ways to clear this, though it's never bothered me enough to try any.

This is a pretty old bug; it's been fixed in recent versions of libparted, although I don't recall the exact version numbers. I know I just tested with GParted 0.5.2/libparted 2.3, and it was fine. If you've got a disk with a mis-marked partition, it's easily corrected with GPT fdisk (gdisk); use the "t" main menu option to change the partition type code to 0700, then use "w" to save the changes.

---

