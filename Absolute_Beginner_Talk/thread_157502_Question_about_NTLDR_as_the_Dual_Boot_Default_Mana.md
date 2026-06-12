---
title: "Question about NTLDR as the Dual Boot Default Management"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Wong3 on 2006-04-09
As we may quite frequently reinstall windows OS,so when we finish the install step,the dual boot problem just directly comes up.We have to build get Grub and then follows.....

It's quite tearing down.

Hey man,can we just take an easy way out?

So my question is can we use the windows NTLDR as the default boot manager by adding the Ubuntu's boot option in boot.ini?

---

### Post by Wong3 on 2006-04-10
Please help,I'm right now on the edge of reinstalling the Windows XP.

---

### Post by steve.horsley on 2006-04-10
If you already have a working GRUB dual-boot, you can take a copy of that bootloader from the bootsector and replace it later. You can take a copy of the entire bootsector with the command:
**sudo dd if=/dev/hda of=/boot/BOOTSECTOR bs=512 count=1**
You may have to change /dev/hda to whatever your hard disk is (possibly /dev/sda).
You can copy the bootloader code only with :
bootloader from the bootsector and replace it later. You can take a copy of the entire bootsector with the command:
**sudo dd if=/dev/hda of=/boot/BOOTLOADER bs=466 count=1**
This copies the bootloader code but not the partition table at the end of the sector.

You can replace either with the command:
**sudo dd if=/boot/BOOTSECTOR of=/dev/hda**
replacing BOOTSECTOR with BOOTLOADER and hda with your hard disk name as required. 

Of course, you can only run the replacement commands while you are in Linux, but you can do these from the rescue mode of the installer disk.

---

