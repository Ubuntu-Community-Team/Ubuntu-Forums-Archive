---
title: "Multi-boot OS/X, Ubuntu 9.10, WinXP and Grub2"
date: 2009-11-17
forum: Apple Hardware Users
---

### Post by yhetheridge on 2009-11-17
I have been using my macBook Pro with all three of the about without issue until now.  I use rEFIt for booting the laptop.  No issues. Frankly, I don't know what happened unless the problem occurred with my latest use of "Update Manager".  I did notice an upgrade was applied whereby "grub-pc" replaced "grub-efi", however a subsequent reboot did not show any issues.  Actually, I noticed that GRUB showed my OS/X partition along with my 9.10 and WinXP partitions as boot options.  BTW: selecting the OS/X partition via GRUB did not work.

I can still boot to OS/X via rEFIt.

I use Grub to manage booting to Linux and Win.  Here's the rub.  Now when I select Linux or Win via rEFIt booting starts as expected but indefinitely hangs with "GRUB" displayed in the upper left hand corner of the screen.

I have booted via a live 9.10 CD, mounted the Linux partition, inspected the /boot and /boot/grub directories.  It looks fine to me. I suppose that there could be an issue with the /boot/grub/boot.img??

Does anyone have a suggestion as to my next step.  I should not need to reload 9.10.  That's a Windows solution.  Surely there's a next step that I'm just overlooking.

Thanks,

yhe

---

### Post by linuxopjemac on 2009-11-17
you could sync the partitions from rEFIt with the partition tool

---

### Post by yhetheridge on 2009-11-17
Thanks.  I noticed that the GPT Type on the Linux partition showed as Apple HFS/HFS+ Partition just as is the case for the OS/X partition.  That sounds wrong.  I did not do the rEFIt sync.  So I thought of using Palimpsest on the 9.10 LiveCD to change it to Linux (0x83), but that's not a choice for an EFI machine.  Suggestions?

---

