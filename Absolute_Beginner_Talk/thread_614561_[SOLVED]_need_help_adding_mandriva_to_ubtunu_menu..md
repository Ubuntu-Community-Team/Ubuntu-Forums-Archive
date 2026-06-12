---
title: "[SOLVED] need help adding mandriva to ubtunu menu.lst"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-16
i just installed mandriva 2008 and cant figure out what i should put in the menu,lst. i installed the / on sda5. i tried this entry but it gave me a error when i tried to boot:

title 		Mandriva 2008
root (		hd0,4)
kernel		/boot/vmlinuz-2.6.11-8mdk root=/dev/hda6 resume=/dev/hda1
initrd		/boot/initrd-2.6.11-8mdk.img 

please help me to figure out what should be put here. i have the mandriva / mounted in ubuntu now.

thanks!

ps
i got the kernel and initrd lines from a menu.lst.example file in the /boot/grub on the mandriva / partition

---

### Post by natehatewindows on 2007-11-16
also i did try (hd0,5) and other numbers but it didnt work.

---

### Post by natehatewindows on 2007-11-16
please help me. :)

---

### Post by louieb on 2007-11-16
Just use the configfile option and load mandriva's grub menu. Quick and easy.
[Nuts on Grub]("http://louboldt.com/ilinuxgrub.htm")

---

### Post by natehatewindows on 2007-11-17
alright for anyone who cares....

i did it a little different. Everytime i used the grub configuration option in mandriva install the install failed. so i simply let mandriva take over the mbr (and did not add ubuntu to mandriva's menu.lst). after the mandriva install compleated i rebooted with a super grub disk and restore gusty's grub, then rebooted into gusty. Then i mounted my mandriva / and looked at the entry in the /boot/grub/menu.lst and put it into the gusty menu.lst and rebooted into a working grub screen with gusty and mandriva. i have a toshiba p105 so i also addes acpi_osi=!Linux to the "kernel" line of the mandriva entry in gusty's menu.lst so i could have sound.

thanks for the help. :)

---

### Post by meindian523 on 2007-11-17
if your problem's solved please mark the thread as solved.....

Thread Tools-->Mark As Solved.

---

