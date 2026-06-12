---
title: "Issues installing 12.04 on Asus K55N Help!!!"
date: 2012-09-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by theDD on 2012-09-13
First in my first tried I scrub up my windows installation and then I removed all partition and started all over again. This time I did install W7 ultimate with no problem with the only issue that if try to install it from a usb stick you better use the usb2 port. Ok know i tried to install ubuntu and It doesn't reconize my windows partition and show everything free. In my bios the EFI is on and also de AHCI for the sata drivers. But know i just want to know if there any way to install it without messing my W7 installation. Also i wonder why is so hard to make bootable cd to work with this machine. Thanks in advanced!!!

PD. IF I turn off the AHCI then windows won't boot.

---

### Post by theDD on 2012-09-17
[B]This fix my not detecting windows 7 and be able finally to install ubuntu

Re: Partitions not detected by gparted[/B] 			
 			 			 		   		 		 		garvinrick4's  suggestion is unlikely to help. It sounds like the drive has leftover  GPT data on it, which is confusing GParted. The easiest way to deal with  this is to use my [GPT fdisk (aka gdisk)]("http://www.rodsbooks.com/gdisk/") program, which you can can use via [PartedMagic]("http://partedmagic.com") or [System Rescue CD.]("http://www.sysresccd.org")

To fix your problem, follow these steps:


[LIST=1]
[*]Boot the emergency disk and open a text-mode shell.
[*]Type "gdisk /dev/sda" (change "/dev/sda" to whatever is appropriate  to access your hard disk, if necessary). The program is likely to  complain that it's found both MBR and GPT data, and will ask which to  use. It doesn't matter which you tell it to use.
[*]At the "Command" prompt, type "x" to enter the experts' menu.
[*]At the "Expert command" prompt, type "z" to "zap" (destroy) the GPT data.
[*]Type "y" in response to the confirmation about destroying the GPT.
[*]Type "n" in response to the query about blanking the MBR. **Caution: If you answer "y" here, you'll destroy your Windows partition(s)!**
[/LIST]


The program will now exit. I recommend you test that this worked by  using GParted. If GParted can now see your Windows partition(s), the  Ubuntu installer should do so, too.

---

### Post by mniemann on 2012-09-27
theDD... you made my day.

After spending most of the day installing Windows 7, I attempted to install Ubuntu 12.04 (x86). Unfortunately I did not receive the choice to "install beside Windows" that I normally get. Yesterday I searched with the wrong keywords to find this thread. Today I did.

I followed your expert instructions, and voila, my new 12.04 install attempt was successful.

BTW, my motherboard is an MSI... and I thought the problem was the result of the AHCI setting, which sent me in the wrong direction.

Thank you! Thank you! Thank you!

---

### Post by arfett on 2012-12-28
How are you able to boot from USB?

I am using the USB 2.0 port and can't boot from a stick made with YUMI from pendrivelinux.

I have BIOS 217 and when I select my USB drive detected as "[UEFI: Imation Atom PMAP]" as the first boot device and all others disabled it just takes me into the BIOS on every boot.

---

### Post by geogur on 2012-12-31
i boot from usb by using f8 key then select ubuntu and boot to my usb ubuntu 12.10 .

---

### Post by kazuya on 2013-01-03
Is there a simple step by step guide for a new owner of this laptop for installing a linux OS via dual boot on this laptop?
We need guide for from bios level to install level
Some folks say cange firmware from UEFI option to Legacy Boot for example, but fail to mention how to do so.
 
I wish there was a youtube video or screenshot guide for doing this.
When or If I figure out the solution, I would upload it here and everywhere.
 
At the moment, has anyone successfully done a dualboot or OS replacement with linux on this hardware? Is it possible to use an older BIO than 217 that has the legacy boot option?
 
Here is some other link I found stating this issue:
[http://mjg59.dreamwidth.org/20187.html](http://mjg59.dreamwidth.org/20187.html)
 
Thanks.
 
Some links with solution:
[http://ubuntuforums.org/showthread.php?t=2092966&page=3](http://ubuntuforums.org/showthread.php?t=2092966&page=3)

---

