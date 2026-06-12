---
title: "boot loader error"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by w_onkar on 2007-05-08
I have a dell inspiron 1405 laptop on which i have windows xp installed. I did not want to mess up my laptop OS and make the warranty void, so i installed ubuntu on an 40 GB external usb hard disk. while installing, i chose not to install any boot loader (to protect mbr of my laptop hard drive), so when i disconnect the usb disk, it can boot in winxp as if it never had linux. When I connect the usb drive and boot from the drive, I used to get the minimal command prompt where I could issue the kernel command (with the path to vmlinuz and root=/'dev/sdb1), the initrd command (with the path to initrd image) and boot command and it would boot properly (and also start Xserver).
However once I tried to boot it from usb drive and it did not give me the minimal command prompt. All I could see on the screen is "GRUB" with no way of issuing any commands.
I tried to run the installation cd in rescue mode and tried to execute bash with my usb drive as root (/dev/sdb1).
The filesystem on my usb drive is in tact however I dont get the minimal command prompt where I could issue the boot command. 
What should I be doing to fix the problem?

Thanks

---

### Post by Spinelli on 2007-05-09
> **w_onkar said:**
> I have a dell inspiron 1405 laptop on which i have windows xp installed. I did not want to mess up my laptop OS and make the warranty void, so i installed ubuntu on an 40 GB external usb hard disk. while installing, i chose not to install any boot loader (to protect mbr of my laptop hard drive), so when i disconnect the usb disk, it can boot in winxp as if it never had linux. When I connect the usb drive and boot from the drive, I used to get the minimal command prompt where I could issue the kernel command (with the path to vmlinuz and root=/'dev/sdb1), the initrd command (with the path to initrd image) and boot command and it would boot properly (and also start Xserver).
However once I tried to boot it from usb drive and it did not give me the minimal command prompt. All I could see on the screen is "GRUB" with no way of issuing any commands.
I tried to run the installation cd in rescue mode and tried to execute bash with my usb drive as root (/dev/sdb1).
The filesystem on my usb drive is in tact however I dont get the minimal command prompt where I could issue the boot command. 
What should I be doing to fix the problem?

Thanks

Does GRUB give any errors? Here's a guess. Type a 'c' at the GRUB screen to go to the command line.

---

