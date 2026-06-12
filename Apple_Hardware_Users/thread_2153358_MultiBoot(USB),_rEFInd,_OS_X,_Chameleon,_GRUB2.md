---
title: "MultiBoot(USB), rEFInd, OS X, Chameleon, GRUB2"
date: 2013-06-10
forum: Apple Hardware Users
---

### Post by Magnusb1 on 2013-06-10
Hello,  I want to use MultiBootUSB to install multiple Linux distros to an external harddrive(including Raring Ringtail). I have found this thread (link 2) which turns up with a functioning configuration of GRUB2 to chainload OS X with Chameleon. I have an Apple Macintosh, and I discovered in the last minute that Chameleon will corrupt my bootloader. Dodged a bullet there :) I have earlier tried to boot into 12.04 and 13.04 with rEFInd after following guides how to edit the configure file. In the end it would not load the kernel files. Installing GRUB2 earlier broke my windows bootloader, the last step in this guide(link 3) is supposed to fix that. The MultiBootUSB should configure GRUB2 for my Linux installations. Is there any chainloader I can use to boot OS X in GRUB2? Do you have any other suggestions on how I can rig this thing? :)

Links:
MultiBootUSB([https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk))
([http://www.insanelymac.com/forum/topic/189079-grub2-as-the-only-boot-loader-its-possible/](http://www.insanelymac.com/forum/topic/189079-grub2-as-the-only-boot-loader-its-possible/))
([http://solitudo.net/blah/posts/Triple_booting_Ubuntu_Mac_OS_X_and_Windows_7_installed_on_a_single_shared_disk/](http://solitudo.net/blah/posts/Triple_booting_Ubuntu_Mac_OS_X_and_Windows_7_installed_on_a_single_shared_disk/))

---

### Post by sandyd on 2013-06-10
Moved to apple users

---

