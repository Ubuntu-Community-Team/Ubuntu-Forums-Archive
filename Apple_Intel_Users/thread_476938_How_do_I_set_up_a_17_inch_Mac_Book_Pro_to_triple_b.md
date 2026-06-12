---
title: "How do I set up a 17 inch Mac Book Pro to triple boot ?"
date: 2007-06-17
forum: Apple Intel Users
---

### Post by Terry Jones on 2007-06-17
I have read several post on the subject of triple booting and the following questions have not been answered by any of them. I want to install Ubuntu 6.06 Dapper Drake. I have used the live CD  a number of times on Macs and PCs. 
I have quad booted a Dell GX 270 with Windows 2000, Windows XP, Fedora Core 6, and Ubuntu 6.06. i Used grub as the 
stage 1 bootloader.

I have the following Mac.
MacBookPro 17 Inch.
Intel CoreDuo 2.16 Ghz Processor.
Mac OS X 10.4.9.
120 GB Harddrive.

For each aswer please include pictures, weblinks,and personal experence if possible.

1. When I partiton the Mac OS X partition.Will I have to reintall Mac OS X?

2. Can the partitioning be done using the Mac OS X startupdisk? The disk contains Mac OS X 10.4.6

3.When to install lilo?

4. How to install lilo for the first time? 

5. How to reinstall lilo after a kernal upgrade? 

6. The exact commands to prevent a kernal panic in Ubuntu?

7. The extract commands to sink GPT with Master Boot Record in the refit bootloader terminal?

8. When and the exact number of times to sink GPT with Master BootRecord?

9. When to reboot and the exact number of reboots needed?

10. Can Mac OS X be reinstall, upgraded, or remove without affacting the other oses?

11. Can Ubuntu Linux be reinstall, upgraded, or removed without affecting the others oses?

12. Can Windows XP be reinstall, upgraded, or removed without affecting the others oses?

13. What is the meaning of chroot?

14. What is a chooted jail?

15. What is a chooted terminal and how to tell if a terminal is chooted? 

16. How to tell if a terminal is not chooted?

---

### Post by ronocdh on 2007-06-19
First of all, I highly recommend you use Feisty instead of Dapper. Dapper's performance on the Mactels leaves a lot to be desired in terms of hardware recognition and functionality. (For instance, in Feisty the F-keys work to control volume and screen brightness! Neat.)

Partitioning is a pretty simple process in OS X and your OS X functionality will remain intact. You don't need to install LILO, as GRUB should suit you fine for most purposes (in combination with rEFIt, of course). All your operating systems will function entirely independent of one another, with the except off filesharing across partitions, if you bother to set this up.

As for your definition questions, start here: [http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)

---

### Post by Terry Jones on 2007-06-19
I tried to partition using Dapper drake and got an error message that said I had an invalid mount point when i tried to assign the / mount point to partition dev /sda 3.

Has any one else gotten this error if so how did you solve it? 

Also does Fiesty Fawn have a patched version of grub. Do you get a error doing the install of grub?

---

### Post by ronocdh on 2007-06-19
> **Terry Jones said:**
> I tried to partition using Dapper drake and got an error message that said I had an invalid mount point when i tried to assign the / mount point to partition dev /sda 3.

Has any one else gotten this error if so how did you solve it? 

Also does Fiesty Fawn have a patched version of grub. Do you get a error doing the install of grub?
No GRUB error in Feisty. Use Feisty.

---

