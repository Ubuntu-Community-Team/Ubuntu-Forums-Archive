---
title: "Browse hard drive from live cd?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by SirShaggy on 2006-08-05
I would like to browse my hard drive from the live CD. I was tri booting, messed up my Fedora Core 5 and decided to reinstall it. Well, I wiped out my original grub in the process. I forgot to uncheck the install grub to MBR box before installing Fedora. I know how to edit the grub file in Ubuntu and Fedora. I just want to somehow see my old /boot/grub/menu.lst to see what kernel I was using in Ubuntu. I just updated Ubuntu last night, I saw there was a new kernel since my last update a month and a half ago. I didn't write it down!!!](*,) 

Anyway, back on track here, How can I access my hard drive folders from the live cd? I searches the forum for this, nothing I am looking for. I tried to browse over to the Ubuntu partition from Fedora, I couldn't gain access. I am not good with Fedora at all!

I know Hda6 and Hda7 are Ubuntu, one is /home and the other is /root. Not sure which is which?!?! I am sure once I can access the hard drive / partition / files, I can make this work. Any ideas?

---

### Post by JerMe on 2006-08-05
You'll need to mount the fedora partition (**man mount** for instructions) to a mount point, then you'll be good to go.  An **fdisk -l** will list the drives and partitions on your computer.  Once you mount it, issue a **cat (*YOUR_FEDORA_ROOT*)/boot/grub/menu.lst** to see what says.

---

