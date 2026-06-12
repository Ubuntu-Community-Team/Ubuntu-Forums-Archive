---
title: "Error Code 0x80070057 Trying To Format Partition Ubuntu"
date: 2012-01-12
forum: Any Other OS
---

### Post by Lukeyslife on 2012-01-12
So when trying to reinstall windows vista i run the installation then i get to the point where it asks me where do i want to install it what partition so i press format on my main partition which has ubuntu on it but i get this error code [SIZE=1]0x80070057, i also did check disk and it didnt say anything was wrong

Thanks Much Help Will Be Appreciated
Luke,
[/SIZE]

---

### Post by oldos2er on 2012-01-12
Moved to Other OS/Distro Talk.

---

### Post by mips on 2012-01-12
Boot up with your ubuntu livecd and run gparted. erase all your partitions on the drive and try the vista cd again afterwards.

---

### Post by Lukeyslife on 2012-01-12
> **mips said:**
> Boot up with your ubuntu livecd and run gparted. erase all your partitions on the drive and try the vista cd again afterwards.

sorry to waste your time but when i run the disc should it come up with some grub menu thing saying Linux Generic 3.0.0 and other linux versions etc. then  run gparted because when i do this it just loads up my normal ubuntu is that meant to happen
if thats what i do i open gparted and right click the partition sda1 with a key next to it but the delete and format are greyed out

---

### Post by mips on 2012-01-12
> **Lukeyslife said:**
> sorry to waste your time but when i run the disc should it come up with some grub menu thing saying Linux Generic 3.0.0 and other linux versions etc. then  run gparted because when i do this it just loads up my normal ubuntu is that meant to happen
if thats what i do i open gparted and right click the partition sda1 with a key next to it but the delete and format are greyed out

You're not booting off the cd you are booting off your HDD. make sure the cd-rom is selected as the boot device in bios.

---

