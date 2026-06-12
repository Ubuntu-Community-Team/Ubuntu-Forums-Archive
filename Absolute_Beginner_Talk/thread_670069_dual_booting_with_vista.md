---
title: "dual booting with vista"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by gutsy goober on 2008-01-17
Hi.  I am a complete newb who has not yet even attempted an install, rather I've read (and read, and read) about installing linux/ubuntu on my laptop which currently runs windows vista (thus, the fervid desire for a new OS).  I think I am ready to make a dual-boot setup using EasyBCD, which seems to me to be the safest since it allows windows to maintain control of booting and keeps the original MBR.  Is anyone familiar with this sort of a dual-boot setup?  This page: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)   seems to imply that ubuntu will not mess with the windows booting, while others suggest that ubuntu may rewrite the MBR.  Do I need to do anything special during the installation to keep the MBR intact?

Thanks for any help.

---

### Post by kpkeerthi on 2008-01-17
I've had that kind of setup with Vista sometime back. Vista Bootloader -> GRUB - > ArchLinux
Just make sure you install grub to the partion where /boot is mounted (/dev/hda1, for instance) and not the MBR (/dev/hda). Your MBR should be intact.

---

### Post by kaan on 2008-01-17
I dual booted windows vista and ubuntu using a very standard install and grub with no problems whatsoever. It shouldn't be a problem at all. Just make sure that you keep windows as the first Partition. Also vista has a partition manager, so you can resize your partitions in vista, if you are squeemish about using gparted.

---

### Post by Sef on 2008-01-17
> I dual booted windows vista and ubuntu using a very standard install and grub with no problems whatsoever. It shouldn't be a problem at all. Just make sure that you keep windows as the first Partition. Also vista has a partition manager, so you can resize your partitions in vista, if you are squeemish about using gparted.

It is recommended to shrink the Vista partition with its own partitioner and not another partitioner.

---

### Post by kaan on 2008-01-17
> **Sef said:**
> It is recommended to shrink the Vista partition with its own partitioner and not another partitioner.

I too have read this. Apparently vista keeps a record of the partition size somewhere and decides it's broken because gparted didn't change that value. It can be fixed with the vista installation cd. It makes more sense to use vistas own partitioner though than go through the hastle.

To answer the original users question:

There is nothing wrong with overwriting the MBR as there is no other way to dual boot. I don't see why you would use EBCD over grub. It actually looks way more complicated then a regular install.

---

### Post by azad on 2008-01-17
In order to have more than one OS, your MBR must be modified. 

Clean up a partition in Vista and install Ubuntu. Select "Use the largest continuous space" during installation. Or you could do manual partitioning if you want.

You can always restore your MBR later. Its no big deal.

---

### Post by erginemr on 2008-01-17
> **kaan said:**
> I dual booted windows vista and ubuntu using a very standard install and grub with no problems whatsoever. It shouldn't be a problem at all. Just make sure that you keep windows as the first Partition. Also vista has a partition manager, so you can resize your partitions in vista, if you are squeemish about using gparted.

But the OP should be extra careful not to overwrite to your Vista partition. It is very easy to be duped by the Ubuntu installer letting it decide on how to partition the hard drives, wiping Windows altogether, resulting in the end with a Linux only system. And there are quite a few sad stories in the forum on this subject.

Once you get past the partitioning part, the rest of the installation is piece of cake.

One last bit of advice to the OP: Before the actual installation, make sure that all your major and peripheral hardware are recognized in Ubuntu Live CD.

---

### Post by spolta on 2008-01-17
Dual booting with Vista is simple on a single harddrive. Just use the Vista disk manager and shrink your Vista partition, make a new partition, then reformat it to ext2 or ext3 using the Ubuntu installer. Then, choose that new partition for your root and you should be all set. Just make sure you have a large enough partition, and make sure not to overwrite your Vista installation.

---

### Post by dstew on 2008-01-17
> In order to have more than one OS, your MBR must be modified.Not necessarily. The only thing the boot loader in the MBR does is load the full booter program. If you have an MBR that calls grub in a single-boot system, you do not have to modify the MBR to get grub to dual boot. You only have to modify the grub booter configuration file, /boot/grub/menu.lst. The same thing goes for other multi-boot capable systems, such as Vista and EBCD.

---

### Post by phidia on 2008-01-17
There's also another pretty painless way to do this. Enter your laptops bios and select usb drive as the 2nd start up device. (You will need to have an external usb drive obviously) you can then install ubuntu or another distro to the usb drive also choose the external usb drive to install grub to. (use the alternate iso)
I've recently done this and nothing had to be changed on the laptop at all. When the usb drive isn't plugged in it boots to vista-when the usb drive is plugged I get the grub menu. Note: you will have to edit /boot/grub/menu.lst because, at least for ubuntu the installer sees the boot order as internal drive=sda external=sdb but when the usb drive is plugged in it boots as sda so for my set up I just changed the menu.lst entry from (hd1,0) to (hd0,0) and grub finds and boots ubuntu without a hitch.

---

### Post by gutsy goober on 2008-01-17
Thanks for all the replies.

I guess I just have to go and do the install .. it sounds like I just have to put grub in the right spot.  I think.  If something goes wrong, I guess I can just wipe vista completely (since I haven't gotten around to acquiring the installation CDs yet  :P)

Again, thanks.

---

