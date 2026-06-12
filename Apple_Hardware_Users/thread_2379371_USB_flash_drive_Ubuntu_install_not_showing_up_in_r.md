---
title: "USB flash drive Ubuntu install not showing up in rEFInd on Mac?"
date: 2017-12-04
forum: Apple Hardware Users
---

### Post by danh123 on 2017-12-04
[LEFT][COLOR=#111111][FONT=Ubuntu]I installed Ubuntu on a USB flash drive. It looks like the installed finished properly (though it did get frozen at the "Please remove your install device" screen.)[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Now I try to boot from this install but rEFInd doesn't find it.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

How can I boot from it?

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]More information:[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]my mac is Macbook Pro Retina 13-inch Early 2013[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Ubuntu iso is ubuntu-16.04.3-desktop-amd64.iso[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

Everything works fine when I click try without install and I can boot the Ubuntu iso fine. But the drive with the installed version on it doesn't get detected.
[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2017-12-04
Moving to the Apple hardware sub-forum, so those that know Mac can help.

I do not know Mac, but believe it is the same as PC with UEFI. UEFI only boots external drives with /EFI/Boot/bootx64.efi. So you need an ESP - efi system partition on external drive with gpt partitioning. And then copy /EFI/ubuntu from internal drive twice.Once to /EFI/ubuntu and once to /EFI/boot. Then rename grubx64.efi to bootx64.efi. You need the /EFI/ubuntu as grub expects more files in /EFI/ubuntu.
I thought rEFInd, automatically created its file as /EFI/Boot/bootx64.efi, if using rEFInd.
Or if booting directly from internal drive, you can just boot Ubuntu.

 EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

