---
title: "(resolved) MacBook Pro fresh install black screen"
date: 2021-05-06
forum: Apple Hardware Users
---

### Post by brickers on 2021-05-06
[FONT=&amp]Hi there[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]I'm completely new to linux and am trying to install Ubuntu 21.04 on my 2015 MacBook Pro 11,4. I have gone through the install process a number of times and cannot get the installation to boot past the startup disk select screen - I just see a completely black screen. [/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]I have no trouble using the live disk at all - all drivers seem to be loading correctly there. I have Intel integrated graphics so do not expect to see some issues I've read around Nvidia cards, but have nonetheless used the live disk to edit the installed EFI bootloader to use the 'NOMODESET' flag with no effect.[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]I have tried a completely fresh install, wiping the hard drive completely, removing MacOS and creating a new EFI partition. I have also tried another wipe and then a fresh MacOS install followed by installing Ubuntu as a second OS - still see the same thing, so this says to me that my EFI bootloader is functioning correctly (MacOS starts with no trouble), but something with the Ubuntu config is failing.[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]I am going for an Ubuntu minimal install and have tried installing both with third party drivers and without - again no change.[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]I'm now at the limit of even knowing what to google to find new things to try - can someone help please?

EDIT: I started to try installing an alternative distro and found the Manjaro installer has an option to view and launch EFI bootloaders. It showed a list of about nine, the top one of which (labelled GRUBX64) booted me into my Ubuntu install, and the second of which (labelled SHIMX64) took me to the black screen. I didn't try any of the others given the laborious reboot sequence, but it seems like some config somewhere is pointing to the wrong bootloader..[/FONT]
[FONT=&amp]
[/FONT]
[FONT=&amp]Thanks[/FONT]
[FONT=&amp]Ferg[/FONT]

---

### Post by QIII on 2021-05-06
Moved to Apple Hardware Users for a more appropriate fit.

---

### Post by brickers on 2021-05-07
I managed to resolve this issue myself using efibootmgr to set the path to the right bootloader

---

