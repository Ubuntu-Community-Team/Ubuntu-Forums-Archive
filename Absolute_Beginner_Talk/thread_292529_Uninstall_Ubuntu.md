---
title: "Uninstall Ubuntu"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by kc0eak on 2006-11-03
Hello,

I need to take Ubuntu off the hard drive on my laptop and get the boot loader back to the NT boot loader instead of the GRUB loader that I'm currently using.  I was told by someone that in order to do this I need to boot into the recovery console and run both fixmbr and fixboot.  Can someone give me a step by step instructions as to how to do this, and also how to get the partition turned back over to Windows.

Thanks

---

### Post by user1397 on 2006-11-03
> **kc0eak said:**
> Hello,

I need to take Ubuntu off the hard drive on my laptop and get the boot loader back to the NT boot loader instead of the GRUB loader that I'm currently using.  I was told by someone that in order to do this I need to boot into the recovery console and run both fixmbr and fixboot.  Can someone give me a step by step instructions as to how to do this, and also how to get the partition turned back over to Windows.

Thanksdo you own a windows install disc?

---

### Post by kc0eak on 2006-11-03
Yes, I do have a Windows install disk.  It's the original Windows XP disk that came with the computer.

---

### Post by seshomaru samma on 2006-11-04
Do you have a dual boot and want to delete Ubuntu?

as far as i remember , you need to boot from the XP CD , it loads some drivers and then asks you if you want to insttal windows or repair windows
you choose repair and then it will ask you for the admin password
(EDIT: it's called the "recovery Console" , you need to press R when the XP CD boots...)
it will ask you for the partition number , usually the answer is "1"
you then get a terminal where you put the command :
```
fixmbr
```
it will ask you something like :"do you really want to do it" and you say "yes" and that's it
next time you boot it will go directly into windows
if you want to erase the ubuntu partition , you need something like 'partition magic' . you can get a 'qt parted' live CD which you can get as a  part of the 'system-rescue-cd ([http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) ) , boot from it and format the linux partition as FAT32 , you will be able to use from Windows afterwards.

---

### Post by user1397 on 2006-11-04
well if you're gonna do what he suggested, then you might as well pop in the live cd to erase ubuntu with gparted partition editor, and then do the fixmbr to get your windows boot loader back.

---

### Post by Ambimom on 2006-11-04
I recently had to go through the uninstall after the upgrade to Edgy went horribly wrong.  

As explained above, you use your Windows XP disk to boot.  When you turn on your machine look for the boot screen command.  Mine is F2.  You tap that and change the boot sequence so that it will boot to the CD. [http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

Your linux partition will not be visible until you reclaim it and reformat it to NTFS.  I used Partition Magic to reclaim it and reformat as NTFS, but partimage will do the same thing, I believe. Once it is NTFS again, you'll be able to use it.

---

### Post by user1397 on 2006-11-07
> **Ambimom said:**
> I recently had to go through the uninstall after the upgrade to Edgy went horribly wrong.  

As explained above, you use your Windows XP disk to boot.  When you turn on your machine look for the boot screen command.  Mine is F2.  You tap that and change the boot sequence so that it will boot to the CD. [http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

Your linux partition will not be visible until you reclaim it and reformat it to NTFS.  I used Partition Magic to reclaim it and reformat as NTFS, but partimage will do the same thing, I believe. Once it is NTFS again, you'll be able to use it.but Partition Magic costs 70$, see for yourself: [http://www.powerquest.com/home_homeoffice/products/overview.jsp?pcid=sp&pvid=pm80](http://www.powerquest.com/home_homeoffice/products/overview.jsp?pcid=sp&pvid=pm80)

that's why i suggested to use a live ubuntu cd (which is free) to get rid of the ubuntu partition.

i can guide you with that if you want.

---

### Post by jpeddicord on 2006-11-07
GParted on the live CD provides everything you need. Partition Magic does that and a little extra, but for $70.

Make your choice. :rolleyes:

---

### Post by nilved on 2007-05-17
I don't think so, at least. You would still need to get the Windows bootloader back.

---

