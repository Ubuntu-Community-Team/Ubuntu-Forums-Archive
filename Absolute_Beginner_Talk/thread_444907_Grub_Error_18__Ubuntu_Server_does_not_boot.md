---
title: "Grub Error 18 / Ubuntu Server does not boot"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by muttefur on 2007-05-15
Hi...

I've got an IBM Aptiva whose specs are as follows...

Pentium MMX 200 MHz.
64M System Ram
Ethernet PCI Card
20G Hard Drive (BIOS recognizes only 8G but Linux recognizes the whole disk...)

About a month ago, I installed ubuntu fesity using the alternate CD. But I want to install only server packages...
Everything worked fine until I wanted to reinstall it. With the alternate CD or server CD, after if finishes installation, GRUB halts and shows me an error 18 message. 

This is the 10th time I try to install and boot ubuntu...please help....

Now, when I successfully installed ubuntu server GRUB loads and halts on the STARTING UP... message and anything happens.

Thank you very much for your help in advance...

---

### Post by x64Jimbo on 2007-05-15
boot the live cd, low level format the whole disk with the following command:
sudo dd if=/dev/zero of=/dev/hda
and then try reinstalling. I have the feeling there was just something messed up in your hard disk somewhere that wasn't getting fixed when you reinstalled.

---

### Post by muttefur on 2007-05-15
Hi...thanks for the answer. I did that yesterday (it took 1 and a half hours) with another software. Then I installed ubuntu alternate and gave me an error 18. I then thought to install an overlay (like a driver to allow the disk as being recognized with the whole 20G) but after it finishes installation, the overlay is replaced by grub.

I will do a low level format today....do you have any other sw in mind to low level format it? Is there any difference to fill the drive with zeros than low level formatting?

Thanx...

---

### Post by muttefur on 2007-05-15
Ok...did the low level formatting....now installed Ubuntu Server Feisty and just hangs in the "Starting Up"...Seems like my CPU doesn't like the linux-server kernel...does anybody knows why???

Thanx again..

---

### Post by alienexplorers on 2007-05-15
Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.

---

### Post by muttefur on 2007-05-16
Thanks for the help...it worked with Alternate CD. It just boots...!!!

However, I installed the server, it does not boot. No Grub errors there... it just hangs after the "Starting Up..." message. I don't wanna think my CPU does not like the linux-server kernel. It only boots with linux-generic kernels...

Does anybody has and idea about it?

---

