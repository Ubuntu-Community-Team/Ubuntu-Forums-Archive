---
title: "ABIT AB9 core 2 duo installation"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by caratuco on 2007-06-12
If you are having trouble installing (k)ubuntu Feisty on a Abit AB9 board with a core 2 duo and a Sata Drive here is how I did it. 
  Actually, I have Vista installed on an IDE on the system as well, so in my case when I configured my BIOS the second line on advanced setup let me decide the boot priority for the IDE and Sata drives that I have. I set the IDE as primary and the SATA as secondary. If you set the SATA as primary when you execute grub it will send you back to the Abit boot screen and you will be stuck in a continuous loop and not be able to boot Windows (some will like this feature, if not wait a while it will happen). I have not tested a dual boot on this system with only one SATA or IDE drive so I don't know if grub will send you back to the beginning and disable Windows.
  Anyway, boot into the live install disk. Choose Start or install. I found with my many tries that sometimes it would error with "job control shut down", and sometimes not. If it does try again or press f6 add a space and"all_generic_ide" (without the quotes) and enter. After you are in the live disk, install the system. Once again, with my system I choose to install on the SATA.
  After installation, reboot the system with the live disk in the drive but choose (on the bottom) "boot from first drive".
- When grub comes up do not press enter, instead press (e) for edit,
- another grub screen will appear,
- choose the option just down from "(hd0,0)", press (e) again,
- add a space and "all_generic_ide" (no quotes),
- press enter and you will return to the previous screen,
- on the second line you chose (/boot/kernel....) press (b) for boot and your hard drive should boot into (k)ubuntu. 

- Next open Konquerer>home go up until you find the boot folder,
- open it where you will find grub,
- open grub and you will see menu.lst., 
- right click and scroll down to actions and click "edit as root",
- scroll down to near the end where you will see the same entries as on the grub boot menu,
- on the second line just below (hd0,0)at the end of /boot/kernel.... add a space and "all_generic_ide noapic nolapic" (again no quotes),
- double check your work as you are editing as root,
- click file and save,
- shutdown and the system should reboot as normal.

With my configuration I have to use the boot disk and boot from "first drive option" or the system will boot into Windows as grub is not installed on the IDE and thinks the SATA is the first drive. However, this works for me as my wife knows less than I do about Linux and uses live messenger. On the other hand, if someone knows a way to boot grub off the IDE with the configuration I have please let me know.
Hope this works for you!

---

