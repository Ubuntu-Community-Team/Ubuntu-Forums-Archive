---
title: "Grub/Refit not working after OSX 10.8 upgrade...."
date: 2012-10-04
forum: Apple Hardware Users
---

### Post by kjkeefe on 2012-10-04
Hello. I have a dual boot setup on my Mac Book Pro for Ubuntu 12.04 and OSX 10.8. I just recently upgraded to 10.8 from 10.7 and that seems to have caused the problem.

After some searching, it looks like when it boots into Ubuntu, it is trying the wrong partition for grub. When it tries to boot, it brings me to the grub rescue prompt and says:

error: unknown filesystem.
grub rescue>

When I use the set command I see this:

prefix=(hd0,gpt3)/boot/grub
root=hd0,gpt3

However, I think it should be using hd0,gpt4. I found a discussion online that seems to say the way to fix this is to boot into ubuntu by doing: 

set prefix=(hd0,4)/boot/grub
set root=(hd0,4)
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda4 ro
initrd /initrd.img
boot

This successfully booted me into ubuntu. Next, the discussion suggested running the following in a shell: 

sudo grub-install --force /dev/sda4
sudo update-grub

When I did this, it added a new entry in the refit boot menu (Boot to linux on partition 4). But when I select that item, it drops me to the grub rescue terminal again and the prefix and root are still pointing at hd0,gpt3. 

Can you give me any advice for how I can resolve this issue? Thanks very much. (It would also be nice if I could reset the refit menu to just have an OSX option and a Ubuntu option. But, this is very minor.)

Here is the output of the partition analyzer:

*** Report for internal hard disk ***

Current GPT partition table:
# Start LBA End LBA Type
1 40 409639 EFI System (FAT)
2 409640 458542887 Mac OS X HFS+
3 458542888 459812423 Mac OS X Boot
4 459812430 620279807 Basic Data
5 620279808 625141759 Linux Swap

Current MBR partition table:
# A Start LBA End LBA Type
1 1 409639 ee EFI Protective
2 409640 458542887 af Mac OS X HFS+
3 458542888 459812423 ab Mac OS X Boot
4 * 459812430 620279807 83 Linux

MBR contents:
Boot Code: GRUB

Partition at LBA 40:
Boot Code: None (Non-system disk message)
File System: FAT32
Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
Boot Code: None
File System: HFS Extended (HFS+)
Listed in GPT as partition 2, type Mac OS X HFS+
Listed in MBR as partition 2, type af Mac OS X HFS+

Partition at LBA 458542888:
Boot Code: None
File System: HFS Extended (HFS+)
Listed in GPT as partition 3, type Mac OS X Boot
Listed in MBR as partition 3, type ab Mac OS X Boot

Partition at LBA 459812430:
Boot Code: GRUB
File System: ext4
Listed in GPT as partition 4, type Basic Data
Listed in MBR as partition 4, type 83 Linux, active

Partition at LBA 620279808:
Boot Code: None
File System: Unknown
Listed in GPT as partition 5, type Linux Swap

---

### Post by bijur on 2013-01-30
I think I´ve found the solution.

Just type this when you boot again in your Ubuntu OS:

```
grub-mkimage -O x86_64-efi --prefix="{UEFI_SYS_PART}/efi/boot" -o grub.efi part_gpt hfsplus fat ext2 normal chain boot configfile linux

```

where ```
{UEFI_SYS_PART}
``` should be your (disk_number,partition_number) of your Ubuntu installation - in your case ```
(hd0,4)
```.

After that, put the grub.efi file inside the same folder where the grubx64.efi file were. You can replace it, after you verify that it works properly ;)

The thing is that the grubx64.efi file doesn´t read the grub.cfg file during the EFI startup procedure, and therefore it must be rebuilt with the grub-mkimage tool.

I hope it helped!

Cheers!
Daniel

---

