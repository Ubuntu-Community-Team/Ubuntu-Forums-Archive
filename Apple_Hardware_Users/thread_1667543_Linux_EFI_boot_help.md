---
title: "Linux EFI boot help"
date: 2011-01-15
forum: Apple Hardware Users
---

### Post by Hatsune Miku on 2011-01-15
Hello everyone! Again i have questions for you >D! I'm trying to get my mac to boot using the EFI boot loader with grub. I have compiled and made a binary for a x64 EFI boot, and it successfully works! Now here is the problem, I have NO IDEA how to make a grub.cfg for it to use to boot. I'm plaining on doing a full Linux install i just need this to be ready to boot the OS when it is installed. Can anyone make me one/tell me how to make one? Or tell me what i need to do after i install ubuntu. Anyone got any input?

Macbook 5,4
Intel core 2 duo
NVIDIA 9400m Graphics
4 GB DDR3 RAM
Ubuntu 10.10 amd64
x64bit Apple EFI

---

### Post by hawkmage on 2011-01-15
I have a MacBook Pro 2,1 that I installed Ubuntu 10.10 as the only OS on the system.  I did not have to do anything special.

---

### Post by metatechbe on 2011-01-16
Hello,

The explanations here should be a good start :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

New URL : [http://help.ubuntu.com/community/UEFIBooting](http://help.ubuntu.com/community/UEFIBooting)

metatech

---

### Post by Hatsune Miku on 2011-01-17
> **hawkmage said:**
> I have a MacBook Pro 2,1 that I installed Ubuntu 10.10 as the only OS on the system.  I did not have to do anything special.

> **metatechbe said:**
> Hello,

The explanations here should be a good start :
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

metatech



I know you do not need to, but i would like to use the EFI boot native to my Mac. I hate using the Emulated BIOS as it slows boot down, along with manipulating the computer.


I used that to get the basic setup, I'm stuck at how im supposed to install the OS After I made the boot loader. Also on how to generate a grub.cfg for EFI-grub and not Grub-PC

---

### Post by metatechbe on 2011-01-17
> **Hatsune Miku said:**
> I know you do not need to, but i would like to use the EFI boot native to my Mac. I hate using the Emulated BIOS as it slows boot down, along with manipulating the computer.


I used that to get the basic setup, I'm stuck at how im supposed to install the OS After I made the boot loader. Also on how to generate a grub.cfg for EFI-grub and not Grub-PC

Please read the link I posted earlier : 
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
It is specific about EFI.

metatech

---

### Post by Hatsune Miku on 2011-01-18
> **metatechbe said:**
> Please read the link I posted earlier : 
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
It is specific about EFI.

metatech

I did, and im saying there is nothing there on what im asking. I need to know how to generate the right grub.cfg file for the computer. It is supposed to be auto generated, and the file to not be edited or created by someone.

---

### Post by srs5694 on 2011-01-18
AFAIK, whether you boot via EFI or BIOS, the update-grub command generates a new /boot/grub/grub.cfg file.

What precisely do you mean by:

> I have compiled and made a binary for a x64 EFI boot, and it successfully works!

What binary are you talking about? A GRUB 2 .efi file? A Linux kernel? An Ubuntu install disc that boots under EFI?

FWIW, I'm preparing a Web page on the topic of booting Linux in EFI mode on Macs. It's not quite ready yet, though. I'll post an announcement in this forum when it's done (probably within a day or two).

---

### Post by Hatsune Miku on 2011-01-18
> **srs5694 said:**
> AFAIK, whether you boot via EFI or BIOS, the update-grub command generates a new /boot/grub/grub.cfg file.

What precisely do you mean by:



What binary are you talking about? A GRUB 2 .efi file? A Linux kernel? An Ubuntu install disc that boots under EFI?

FWIW, I'm preparing a Web page on the topic of booting Linux in EFI mode on Macs. It's not quite ready yet, though. I'll post an announcement in this forum when it's done (probably within a day or two).


A grub.efi binary file.

---

### Post by Hatsune Miku on 2011-01-18
> **srs5694 said:**
> AFAIK, whether you boot via EFI or BIOS, the update-grub command generates a new /boot/grub/grub.cfg file.

What precisely do you mean by:



What binary are you talking about? A GRUB 2 .efi file? A Linux kernel? An Ubuntu install disc that boots under EFI?

FWIW, I'm preparing a Web page on the topic of booting Linux in EFI mode on Macs. It's not quite ready yet, though. I'll post an announcement in this forum when it's done (probably within a day or two).


A grub.efi binary file.

---

### Post by srs5694 on 2011-01-19
> **Hatsune Miku said:**
> A grub.efi binary file.

I'd be interested in knowing the command you used to create this. (I've done it, too, but mine has some minor problems; if your method works better, I'd like to know what it is.) Thanks.

---

### Post by srs5694 on 2011-01-19
I've got my Web page up describing my procedure for EFI-booting Linux on a Mac:

[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

I hope it's useful to you!

---

