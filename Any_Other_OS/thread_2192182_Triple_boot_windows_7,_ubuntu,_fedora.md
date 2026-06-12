---
title: "Triple boot windows 7, ubuntu, fedora"
date: 2013-12-06
forum: Any Other OS
---

### Post by bheemamahesh on 2013-12-06
_**Installing triple boot with Windows, Kali Linux (Ubuntu) and nst18 (Fedora)**_


***Steps I followed:***

Firstly, I Installed windows 7 and Installed Kali linux (ubuntu) and grub loader is in /dev/sda.

Now I have unpartitioned space to install Fedora.

Some one please guide me how to install fedora also without any issues.


Thanks for your help :)

---

### Post by oldfred on 2013-12-06
Moved to other OS since not Ubuntu.

Never installed Fedora, but I believe it defaults to LVM with a separate /boot partition. Then its grub would be the grub boot loader installed into the MBR. Normally last installed operating system is the one in the MBR.
Some have suggested that the advantages of LVM are best when using an entire hard drive, so better to just use a standard ext4 partition not the default LVM.

If you use LVM with Fedora, you may have to install lvm2 driver in Ubuntu.

Which version of grub2 do you want to boot by default?

---

