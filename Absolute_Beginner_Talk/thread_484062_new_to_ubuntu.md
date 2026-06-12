---
title: "new to ubuntu"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by valchau on 2007-06-25
Hi, I just downloaded the Feisty Fawn ubuntu iso, burned it to a CD and installed in on my WinXP desktop computer. I am excited about using this distro becuase it appears to be user friendly. I also have the book Beginning ubuntu Linux by Keir Thomas (APress) to guide me. 

I had a very large WinXP partition but it was mostly empty, so in the installation process I told ubuntu to create two smaller partitions, one for /  (ext3), and one for the swap file. That was fine. I rebooted and I saw the grub boot menu. But I couldn't boot WinXP anymore. I was able to boot into ubuntu from this and was even able to boot into the Win Recovery partition. But no matter how many times I rebooted, I could not boot from Win XP again. So I finally used the Win recovery partition, hoping to recover WinXP. Couldn't recover it. 

So I again used the install ubuntu CD, installed ubuntu and it works fine. And I can SEE my WinXP NFTS partition, but I cannot boot from it. I looked at my grub boot file using ubuntu and it looks fine according to some forums where I looked to see what others had done...

And ubuntu's open office lets me see and edit the powerpoint and word docs on my USB drive (FAT). What can I do to boot from WinXP?!!!

Thanks!!!
[email]vchau@palomar.edu[/email]

---

### Post by cogadh on 2007-06-25
Boot with your Windows XP install CD and enter Recovery Console. When you get to the command prompt, type "fixmbr". This will wipe out GRUB and make Windows the default boot again. If Windows still won't boot, then you may have seriously damaged your Windows partition. Did you defragment your Windows partition before you allowed Ubuntu to repartition the drive? Also, when you created the Ubuntu partitions, where on the drive did you place them (at the beginning or end)?

---

### Post by BobCFC on 2007-06-25
Welcome!

Can you browse your XP files on your internal HD using Ubuntu  or did you wipe them?   Ubuntu usually mounts your windows drives for you so you can read files.

---

### Post by Skrynesaver on 2007-06-25
post a copy of your /boot/grub/menu.lst and your /etc/fstab.  This will enable people to give concrete advice for your system

---

### Post by valchau on 2007-06-25
When I get back home after work I can do that. Thank you!

Yes I can see my WinXP stuff thru ubuntu. What I am doing is opening the docs I need with OpenOffice, editing them and saving them to my USB drive (has FAT so I can read and write to it).

---

### Post by valchau on 2007-06-25
I don't think  I have a WinXP install CD; that is the problem. Otherwise I would have tried that already. I had to use the Win Recovery Partition. All the data seems present (was under my Documents), and even the Thunderbird email files are still present there. I can see everything is there. I have a fairly new PC so I didn't defrag the WinXP paritition. And it is hardly used except under my documents. I copied all that stuff from another WinXP PC recently onto this one. 
WinXP is still the first part of the hard drive. I checked that but can show you later after I get home.


Boot with your Windows XP install CD and enter Recovery Console. When you get to the command prompt, type "fixmbr". This will wipe out GRUB and make Windows the default boot again. If Windows still won't boot, then you may have seriously damaged your Windows partition. Did you defragment your Windows partition before you allowed Ubuntu to repartition the drive? Also, when you created the Ubuntu partition, where on the drive did you place them (at the beginning or end)?[/QUOTE]

---

### Post by nick_h on 2007-06-25
Since I assume you want dual-boot anyway it is probably best to paste your /boot/grub/menu.lst here first, as already suggested.  You can see your partition entries with the command sudo fdisk -l /dev/sda

---

### Post by LaRoza on 2007-06-25
If you want to boot Windows, you can restore the bootloader with the Super Grub Disk.

It will fix the MBR so Windows will boot, however, Ubuntu will not.

The Super Grub Disk does much more than that, but that is a very useful feature.

See my sig for the Super Grub Disk.

---

### Post by cam_tram on 2007-06-25
Is your Windows partition formatted as fat32 or ntfs?  Even with support for it, NTFS is still a little shaky on Ubuntu.  The partitioner might of messed something up, especially if the partition was fragmented.

If the partition is intact though, you could try manually editing Grub's menu.lst, make sure all your drive and partition numbers are correct (it starts at zero)

---

