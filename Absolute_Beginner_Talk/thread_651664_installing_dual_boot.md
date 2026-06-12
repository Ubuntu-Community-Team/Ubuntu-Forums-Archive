---
title: "installing dual boot"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by totally_new on 2007-12-27
Want to install Kubuntu dual boot with Windows Vista. 

New machine.

Have to resize partitions.

2 320 GB drives. Windows is on sda1 with the HP recovery stuff on sda3. sdb1 is totaly free.

The installation program is clear as mud to rme.

When the partition step comes up, it display something for sdb1 and asks if want to to us the guided, whole disk or manual. The guided is set to use 50% of the partition.  I want 100% of sdb1 for Kubuntu. Leave sda3 and convert sda1 for 50 GB for Windows Vista and the rest Kubuntu.

I have found the partition program under the Kubuntu system menu and it looks like that would do the repartition job. Is it safe to use that partition program? I think it is qpart..... or something like that.

That program last lets me see hat I am resizing and doing as where with the installation program I'm running totally blind.

Can I use the qpart... program to resize and then run the installation?

---

### Post by Tango_Down on 2007-12-27
Umm, you really should not try to resize a partition that has an active installation running on it. If you have some empty partitions, you can resize or combine them using gparted from a live disk, for general instructions on dualbooting, here is a handy link. 
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by Moop on 2007-12-27
Why are you spreading your kubuntu install across two hard drives? 

The partitioner should work for what you want to do but a better idea would be to just use all of sdb1 to install kubuntu and after that is done you can free up some space on the other hard drive for linux if you want more room. 

Always back up your data before resizing partitions.

---

### Post by totally_new on 2007-12-28
> **Moop said:**
> Why are you spreading your kubuntu install across two hard drives? 

The partitioner should work for what you want to do but a better idea would be to just use all of sdb1 to install kubuntu and after that is done you can free up some space on the other hard drive for linux if you want more room. 

Always back up your data before resizing partitions.

I wasn't intending to "spread"  across 2 hard drives. I just wanted to repartition when I installed. 

So what you are saying is that I should just use the installation program to install on one hard disk, say sdb1 and then repartition sda after installation?

Okay, that hadn't occurred to me when I was trying to install and getting frustrated with trying to understand the partitioning part of the installation process. It wasn't clear what was happening. It was suggesting 50% of the disk and it wasn't clear if I changed that to , say, greater than 50%, if I was changing the greater portion for Unbuntu or if the greater part was left as free space under Windows. The sparsity of directions or explanation didn't help. A graphical depiction like qpartt.. (whatever the name is) would have helped tremendously. 

Can't you make qpart.. part of the installation partitioning process? That would help tremendously.

By the way - thank you for your help. I really do appreciate it. It helps me to understand what is happening.

By the way, I don't think I was trying to resize an active partition. I was running Kubuntu off the installation CD. So the Windows partition sda wasn't really the "active" partition was it?

---

