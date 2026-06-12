---
title: "Install Help"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Ice2097 on 2006-12-19
I just installed Ubuntu (x64) 6.10 on an external hd on my computer. I unplugged the 2 sata drives inside my box before installing to make sure nothing got messed up on them (they have xp and vista installed, and i'm paranoid). The install worked fine, I rebooted from the external HD, installed some updates, it said to reboot, so i turned the computer off and replugged in my 2 sata drives. Now when i try to boot grub comes up fine, but when it goes to run Ubuntu it just stops during the startup procedure. The last thing on the list is:
[   70.652275] sd 2:0:0:0: Attached scsi disk sdc
then there is just a flashing cursor that I can type into.
what should I do?
Thanks.

---

### Post by balloons on 2006-12-19
first thing i would do is unplug the scsi drives again. If ubuntu boots, then we can narrow it down from there. (Of course after it boots you can try shut down and restart with them plugged in again)

---

### Post by Ice2097 on 2006-12-19
ok, i unplugged the sata drives, rebooted, it worked fine. plugged them back in, and it didnt start again.
so its definitely the sata drives... I just dont know why adding drives would cause linux not to start

---

### Post by Sef on 2006-12-19
Unplug one at a time.  Find out if it is both drives or just one.

---

### Post by macogw on 2006-12-19
It's probably because the external drive is below the SATA drives in your BIOS.  If you want the external drive to boot first, change it in your BIOS.

---

### Post by Ice2097 on 2006-12-19
ok, when either drive is plugged in it won't start (still stops at the ubuntu loading screen)
and changing the drive order doesn't help (im using the bios bootloader to boot from the external drive)

---

### Post by Ice2097 on 2006-12-20
Well, it turns out when I said paranoid before, I meant absolutely correct. ](*,) 
 I tried reinstalling Ubuntu with the sata drives plugged in. It installed fine, but also installed grub on my windows drive. Now it can't launch any operating system unless the external drive is plugged in (if it's unplugged it starts to load grub then gives an error).
How do I fix this (move grub onto the external drive and put the windows bootloader back on my internal drive)?

---

### Post by macogw on 2006-12-20
Do you have a Windows rescue cd or install disk or restore cd?

---

### Post by Ice2097 on 2006-12-20
I have the vista install disk (i'm using the vista bootloader to load xp and vista)

---

