---
title: "Need help completely uninstalling phoenixOS from dual boot."
date: 2019-06-30
forum: Any Other OS
---

### Post by gamerwael on 2019-06-30
Hi i have recently installed phoenixos on my ubuntu laptop by following this method [https://www.youtube.com/watch?v=YPQUH2E1E0k](https://www.youtube.com/watch?v=YPQUH2E1E0k). Now i really want to uninstall it and reclaim that space. I cant find any tutorials on this. please help.

---

### Post by oldfred on 2019-06-30
UEFI or BIOS system & installs?
What brand/model system?

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by gamerwael on 2019-07-02
I dont think my boot is broken. I can still use Ubuntu. I dont think i need boot repair. Sorry if i misunderstood what you are trying to say. Im not an expert on ubuntu...

---

### Post by oldfred on 2019-07-02
The Boot-Repair report will show your configuration. And then we can see what left over phoenixOS files you still have.

---

### Post by gamerwael on 2019-07-04
When i did recommended repair I got this:
FlexNet detected. Please backup your data before this operation. Do you want to continue?
I selected no because i didnt want to backup my entire laptop as it would take time.
Do u think i should fix it?

After that i got this:
An error occurred during the repair.


Please write on a paper the following URL:
[http://paste.ubuntu.com/p/Rwj6FtJkBx/](http://paste.ubuntu.com/p/Rwj6FtJkBx/)




In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] 


You can now reboot your computer.




The boot files of [The OS now in use - Ubuntu 16.04.6 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Thanks for the reply.

---

### Post by oldfred on 2019-07-04
I want to see report not run the fix.

But if you have not backed up computer that should be the very first thing you do, no matter how long it takes.

You are only showing one drive with just Ubuntu in one partition and one swap partition.

Flexnet is left over then from your previous Windows BIOS install and some proprietary software you installed. Flexnet manages the hidden serial numbers or passwords for many Windows applications.
They also use the sectors after the MBR for there info. But grub also writes additional boot code, core.img into that same space just after MBR. Years ago, they conflicted, now grub writes around flexnet's data. But you do not need that data anymore anyway.

With new UEFI systems that use gpt partitioning Windows creates a System reserved for flexnet type data. And if grub is installed in the old BIOS mode to a newer gpt drive, grub has to have a bios_grub partition. These take place of the space after the MBR in gpt partitioned systems.

---

