---
title: "Grub EFI will not make/use a grub.cfg"
date: 2010-04-22
forum: Apple Hardware Users
---

### Post by Ravernomina on 2010-04-22
I was able to make a grub.efi boot loader finally. But in the end it did not make or generate a grub.cfg, so every time i boot using this loader I get the grub bash shell and nothing else. I tried copying the on from my harddrive to the EFI folder on my flash drive but still nothing. 

What i did was compile the loader from source using the directions [here]("http://grub.enbug.org/TestingOnMacbook"), then formated a 4 GB flash drive to gpt, and a fat32 File system. Then moved all of the grub items to /efi/grub. Once done i then rebooted, booted to a rEFIt cd and then used it to boot to the USB (the folder is not blessed yet). Then once i got to the loader screen its just a EFI screen, no boot choice Nothing... just a recovery bash. What am i doing wrong... did i do a step wrong, did i compile wrong? What?! could some on PLEASE tell me how to get the EFI grub to make/use a grub.cfg file! PLEASE PLEASE PLEASE PLEASE PLEASE!!!! Thanks!

---

### Post by Ravernomina on 2010-04-22
Bumping

---

### Post by Ravernomina on 2010-04-22
Bump

---

### Post by Ravernomina on 2010-04-22
Bump

---

### Post by alexmurray on 2010-04-22
Perhaps try reading and asking the in usual EFI thread - [http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

