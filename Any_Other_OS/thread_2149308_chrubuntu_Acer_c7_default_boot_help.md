---
title: "chrubuntu Acer c7 default boot help"
date: 2013-05-28
forum: Any Other OS
---

### Post by Adamthirlwell on 2013-05-28
hi guys. recently bought a Acer c7 and installed chrubuntu onto it today. all went fine but having difficulty booting into chrubuntu. when i t boots into chrome I open the terminal and log in as chronos then type `sudo cgpt add -i 6 -P 5 -S 1 /dev/sda` then exit then reboot but it just boots into chrome again. please help

---

### Post by oldrocker99 on 2013-05-28
Hmmm...your command is correct, with spaces where they belong. It certainly worked for me....

---

### Post by mensajess on 2013-07-15
after a couple months of use, now i'm having the same problem. boots chromeos, enter the command, reboot, chromeos. does anyone have a solution?

---

### Post by demuxer on 2013-08-01
You must press CONTROL+D to boot into ChrUbuntu automatically (as default if you used the 'cgpt' command)

perhaps, the grub menu cant work there, and you must be carefull to not press SPACEBAR in that screen, cause will turn on the OS RECOVERY to stop (disabling Chrubuntu loader)

---

