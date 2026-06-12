---
title: "Bootloader distros missing"
date: 2011-10-27
forum: Any Other OS
---

### Post by rmcellig on 2011-10-27
I have 8 partitions on my hard drive. So far I have 5 distros installed each in their own partition. My bootloader used to display all the distros I had installed. After installing PCLinuxOS, the bootloader which looks really nice, only displays PCLinux and none of the other distros. How can I fix this so that all my distros are listed in the bootloader menu?

---

### Post by drs305 on 2011-10-27
> **rmcellig said:**
> I have 8 partitions on my hard drive. So far I have 5 distros installed each in their own partition. My bootloader used to display all the distros I had installed. After installing PCLinuxOS, the bootloader which looks really nice, only displays PCLinux and none of the other distros. How can I fix this so that all my distros are listed in the bootloader menu?

What bootloader does PCLinuxOS use?  If it's not Grub 2, I would recommend booting into your Ubuntu OS or any OS which uses Grub 2 and run the following command. It will return control of the boot to Grub, and probably find your other OS's. If your BIOS doesn't boot sda first, change the command.
```

sudo grub-install /dev/sd**a**
sudo update-grub
```

If you can't boot any other OS, boot the Ubuntu LiveCD for the version you have installed. Mount the Ubuntu partition and then install grub. I'll use sda5 in the example. Don't use the partition number in the second command.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

*After* you reboot into Ubuntu, run:
```
sudo update-grub 
```
Hopefully it will find all, or at least most, of your other OS's.

---

### Post by rmcellig on 2011-10-27
Thanks! That worked. I really like the bootloader that comes with pclinuxos. Is it possible for me to use this bootloader instead of grub2?

---

### Post by drs305 on 2011-10-27
> **rmcellig said:**
> Thanks! That worked. I really like the bootloader that comes with pclinuxos. Is it possible for me to use this bootloader instead of grub2?

I'm not familiar what bootloader it uses. If you tell us what it is I'm sure there are forumites who would have at least some familiarity with it. If it's Grub legacy our collective memories are slowly fading but the documentation is still out there on the Web.

---

### Post by rmcellig on 2011-10-28
The bootloader looks very clean and contains just the names so that it doesn't look as cryptic as grub2. if there is a way to clean up grub2 so that you can adjust the font size and just list the distros that are installed that would be great.

---

### Post by drs305 on 2011-10-28
> **rmcellig said:**
> The bootloader looks very clean and contains just the names so that it doesn't look as cryptic as grub2. if there is a way to clean up grub2 so that you can adjust the font size and just list the distros that are installed that would be great.

The Grub Customizer app lets you make a lot of tweaks to the menu, including a pretty easy way to rename each of the titles. 

The font size I'm sure can also be controlled by Grub Customizer. If you had to do it manually:
[LIST]
[*]At the Grub menu press 'c' to drop to the Grub prompt.
[*]Type 'vbeinfo' to see what resolutions are available and write one down. The higher the resolution the smaller the menu text.
[*]Press ESC and boot.
[*]Open the Grub configuration file for editing: "gksu gedit /etc/default/grub'
[*]Change "#GRUB_GFXMODE=640x480" to "GRUB_GFXMODE=<new value>". Omit the # symbol. 
[*]Save and 'sudo update-grub"
[/LIST]

Grub 2 has a lot of great features. Maybe you will become a convert...

Click the 'Customizer' link in my signature line to take you to a thread about GC.

---

### Post by rmcellig on 2011-10-28
Thanks so much drs305!!

---

