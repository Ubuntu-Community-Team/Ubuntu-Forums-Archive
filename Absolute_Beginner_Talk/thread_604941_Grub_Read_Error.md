---
title: "Grub Read Error"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Old Timer on 2007-11-06
I built a new computer just to run Ubuntu. Foxconn mother board with AMD Athlon 64 X2 3800+, 1 G memory, 40 GB hard drive. This is Linux only, not dual boot.

Installed 7.10 (64 bit), did not have any error messages. When I boot from the hard drive I get the message "Grub Read Error" as soon as it tries to load the operating system. Reinstalled with the same result. Then installed 7.10 (i386) - same error message. Then installed 6.10, that I have installed and running on another computer, and got the same error message.

Looked at the posting on this subjects and tried the following using terminal.

Ran "sudo grub" - "find /boot/grub/stage1"  to find X=0 ,Y=0 value - "root (hd0,0)" - "setup (hd0)" - message said that values were accepted - rebooted and got same error message.

Ran "getit /boot/grub/menu.lst" - There were no listing in the list.

Ran "sudo fdisk -l" - listed three partitions: /dev/hda1 - Linux, /dev/hda2 - Extended, and /dev/hda5 - Linux Swqap / Solaris>

Any ideas on solving this problem.

Thanks

---

### Post by logos34 on 2007-11-06
try 'Boot from first hard disk' menu option on the live CD.

Or get [Super Grub Disk]("http://supergrub.forjamari.linex.org/").

Try flashing your BIOS with latest update.


> Ran "getit /boot/grub/menu.lst" - There were no listing in the list.

it's 'gedit /boot/grub/menu.lst' and the root partition has to be mounted to access the file.  Grub is either not installed or no menu.lst was generated.

---

### Post by Pumalite on 2007-11-06
Do md5sum on your iso, burn at 4x, check for integrity before install. Reinstall if all prior OK.

---

### Post by cotcot on 2007-11-06
> **Old Timer said:**
> 
Ran "getit /boot/grub/menu.lst" - There were no listing in the list.


Thanks
Not sure what you mean with this. Is the file menu.lst empty ? So do you create the file with your instruction ?

Could try to put this in your menu.lst :
> default		0

timeout		10

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

where you need to adapt the kernel version as you find it in your boot directory (vmlinuz ...).

---

### Post by Old Timer on 2007-11-06
Thanks for quick responses.

Tried "boot from the hard disc" menu option on the live CD and get the same error.

When I run gedit for menu.lst the file is empty. I modified menu.lst as suggested by cotcot and still get the same error.

I looked at menu.lst on my computer running 6.10 and found that in addition to the program cotcot suggested that Ubuntu kernel statements add an additional line:
     root=UUID=0b75d67b-7234-451c-89d1-5fe7586bd071  ro quiet splash or quiet single
Any idea what this does and if necessary how do I determine what it should be for my computer?

Why on this computer is menu.lst defective? As the same thing occurs when I installed 6.10 from a disk that I previously used on another computer, it doesn't seem to be a defective CD.

I wonder what others files are corrupted.

Is there something about my hardware configuration or BIOS setting that could cause the problem?

I am not familiar with "Super Grub Disc" Does this modify menu.lst or just the boot loader? Is this worth a try? Or is their some method of repairing the problem from the Ubuntu Live CD?

Thanks for your help

---

### Post by cotcot on 2007-11-08
> **Old Timer said:**
> 
     root=UUID=0b75d67b-7234-451c-89d1-5fe7586bd071  ro quiet splash or quiet single


It is not an additional line. I replaced UUID=... from my menu.lst by the partition name it stands for. UUID=... is the identification of the partition. You can find the translation of it in /etc/fstab.

I now follow a previous poster that it is better to reinstall after checking your installation media. Eventually reinstall with the Alternate install CD.

Even if you could repair it what other failures are there that you have not seen yet.
I have not yet used the supergrub CD, so I cannot comment on that.

---

### Post by Old Timer on 2007-11-08
I have found that it is a problem with the hard drive. This was a new drive and it passed the manufacturers diagnostic test. I installed another drive, reinstalled Ubuntu 7.10, and I do not get the Grub read error message. Now I need to troubleshoot the hard drive to figure out what is going on.

Thanks to everyone for their help!

---

