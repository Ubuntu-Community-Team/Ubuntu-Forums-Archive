---
title: "Just installed Dapper - computer does not start"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by anttti on 2006-06-04
Hello everyone,

Here's my situation: I have two hard drives, 120Gb and 160Gb. On the 120 I have two installations of WinXP (naturally in different partitions), and three other NTFS partitions. The 160Gb one is divided into four parts, of which one was supposed to dedicate to Ubuntu.

So I downloaded Dapper, burned it to disk and booted from it. I started the installation process, and on the partition phase of the installation I chose to manually configure the partitions. I replaced one of the four parts of the 160Gb disk with ex3 (?) formatted partition for Ubuntu. That part was extended partition, which contained two partitions, one for swap and one for /. After installation I booted the computer, and was greeted by GRUB level 1.5 error 21.

So I used the WinXP installation disk and ran fixmbr to gain control of the machine again. I decided to give it another try, this time with a different strategy. I deleted the newly-created linux partition with 'gparted', and chose to install Ubuntu to "largest unused space" with the installation wizard.

Upon restart, the result was still the same -- error 21. I checked GRUB manual on that error:
"21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system."

Can anyone give any advice how to handle this situation? Is it possible to install Ubuntu on a machine with two installations of WinXP?

Thanks in advance,

-antti

---

### Post by karthik085 on 2006-06-04
[QUOTE=anttti]Hello everyone,

Here's my situation: I have two hard drives, 120Gb and 160Gb. On the 120 I have two installations of WinXP (naturally in different partitions), and three other NTFS partitions. The 160Gb one is divided into four parts, of which one was supposed to dedicate to Ubuntu.

So I downloaded Dapper, burned it to disk and booted from it. I started the installation process, and on the partition phase of the installation I chose to manually configure the partitions. I replaced one of the four parts of the 160Gb disk with ex3 (?) formatted partition for Ubuntu. That part was extended partition, which contained two partitions, one for swap and one for /. After installation I booted the computer, and was greeted by GRUB level 1.5 error 21.

So I used the WinXP installation disk and ran fixmbr to gain control of the machine again. I decided to give it another try, this time with a different strategy. I deleted the newly-created linux partition with 'gparted', and chose to install Ubuntu to "largest unused space" with the installation wizard.

Upon restart, the result was still the same -- error 21. I checked GRUB manual on that error:
"21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system."

Can anyone give any advice how to handle this situation? Is it possible to install Ubuntu on a machine with two installations of WinXP?

Thanks in advance,

-antti[/QUOTE]
Will these help:
[http://forums.techguy.org/unix-linux/466273-dual-booting-windows-xp-ubuntu-2.html](http://forums.techguy.org/unix-linux/466273-dual-booting-windows-xp-ubuntu-2.html)

[http://forums.devshed.com/linux-help-33/grub-error--windows-xp-and-fc-5t-348503.html](http://forums.devshed.com/linux-help-33/grub-error--windows-xp-and-fc-5t-348503.html)

More results:
[http://www.google.com/search?hl=en&lr=&q=GRUB+level+1.5+error+21&btnG=Search](http://www.google.com/search?hl=en&lr=&q=GRUB+level+1.5+error+21&btnG=Search)

---

### Post by anttti on 2006-06-04
[QUOTE=karthik085]Will these help:
[http://forums.techguy.org/unix-linux/466273-dual-booting-windows-xp-ubuntu-2.html](http://forums.techguy.org/unix-linux/466273-dual-booting-windows-xp-ubuntu-2.html)

[http://forums.devshed.com/linux-help-33/grub-error--windows-xp-and-fc-5t-348503.html](http://forums.devshed.com/linux-help-33/grub-error--windows-xp-and-fc-5t-348503.html)
[/QUOTE]

Oh my, they did indeed!

The problem was solved by fiddling with BIOS, my 2nd harddrive wasn't turned 'on' automatically for some reason. Thank you, thank you, thank you!! :D

---

