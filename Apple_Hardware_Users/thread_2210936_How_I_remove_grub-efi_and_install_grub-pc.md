---
title: "How I remove grub-efi and install grub-pc"
date: 2014-03-13
forum: Apple Hardware Users
---

### Post by alexfig221 on 2014-03-13
I'm unable to boot into Ubuntu. It always gets stuck on a blank purple screen. I've tried many different solutions, but nothing has worked. After some research I've come to the conclusion that I need Ubuntu to boot in BIOS mode. It seems this solution worked for someone [else]("http://ubuntuforums.org/showthread.php?t=2052933"), but I'm not exactly sure how to do it. I'm assuming I need to boot into a Live CD or USB which I have, but I don't know what to do after that. Can anyone point in the right direction?

---

### Post by matt_symes on 2014-03-13
Hi

What have you tried so far ?

Do you have the same hardware as the poster in the thread you linked to ?

Kind regards

---

### Post by alexfig221 on 2014-03-13
[Here]("http://askubuntu.com/questions/433535/is-there-a-way-to-force-ubuntu-to-install-in-bios-mode/433659?noredirect=1#433659") are some more details. I have a MacBook  Pro model 5,3 with an nVidia 9600m and 9400m so I have to add this command to disable the 9600m or else I just get a blank black screen rather than a blank purple screen.
```
outb 0x728 1 # Switch select
outb 0x710 2 # Switch display
outb 0x740 2 # Switch DDC
outb 0x750 0 # Power down discrete graphics
```

I've also tried using nomodeset, acpi=off, and nouveau.noaccel=1 and nothing worked. The other reason I think I need it to boot in BIOS mode is because in some of the guides I've read on triple booting on MacBooks, they installed Ubuntu in BIOS mode. I think the reason mine didn't is because I used a USB instead of a CD, and MacBooks(at least this model) have trouble booting USBs in BIOS mode. I had a similar problem trying to get it to read my Windows 8 USB. I think some people [here]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015211") had a similar problem where they wanted it to install in BIOS mode, but got EFI.

---

### Post by oldfred on 2014-03-13
I do not know MAC.
Whether you use flash drive or not should not mater.
If in BIOS mode you will need a bios_grub partition with gpt partitioning which Macs also use.
Not sure how Macs work with BIOS booting as with Windows it needs MBR partitions inside the gpt partitions or hybrid MBR/gpt which is not recommended.
       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)


 [URL="https://help.ubuntu.com/community/MacBookPro"]https://help.ubuntu.com/community/MacBookPro
[/URL]
 Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

Edit another thread[URL="https://help.ubuntu.com/community/MacBookPro"]
[http://ubuntuforums.org/showthread.php?t=2210818](http://ubuntuforums.org/showthread.php?t=2210818)
[/URL]

    [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

### Post by alexfig221 on 2014-03-14
So installing grub-pc worked. I just followed the guide [here]("https://help.ubuntu.com/community/Grub2/Installing#Purging_.26_Reinstalling_GRUB_2") and finally got it to boot. Thanks to everyone who offered help.

---

