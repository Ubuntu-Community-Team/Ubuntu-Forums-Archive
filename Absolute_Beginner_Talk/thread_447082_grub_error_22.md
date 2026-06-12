---
title: "grub error 22"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by dylpicklesdad on 2007-05-17
hello everyone! it has been awhile since i have had any questions and all of you were very kind in helping this newbie. now i have a BIG problem. after much messing around with edgy i decided to give up for now and changed my partitions back to original with a gparted cd and when that was done and restart happened all i get is an message from the grub boot loader that states error 22 and freezes right there. had to hard shut down computer and load a live disk and send this message. please help me fix this without reloading windows.  thank you all for your time
dylpicklesdad

---

### Post by ccesare on 2007-05-17
What do you mean by "changed your partitions?"

If you changed your partition table, I would assume that you most likely formatted the partitions too. This means that the kernel image that GRUB points to in order to boot is no longer there. You'll need to reinstall linux to overwrite the GRUB now sitting in your MBR.

Google "grub error 22." This is a very common issue and lots of information is already out there.

---

### Post by dylpicklesdad on 2007-05-17
thank you for the reply, yes that is exactly what i did(i think) anyway i used gparted live to delete the partitions that ubuntu was on and resized and reformatted then when i rebooted all i recieved was the error 22 from the grub boot loader, sorry to say my goal was to uninstall ubuntu but i am going to give my laptop to my son and he does not want a daul boot w/ubuntu, so i need to find out how to uninstall from a dual boot. i have fiesty back in right now because i gave away my edgy disc so a link for a tutourial would be great   thank you

---

