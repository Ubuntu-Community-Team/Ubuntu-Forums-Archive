---
title: "Grub boot list is cluttered"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Maupertus on 2006-01-21
I know I've read something about this, but I can't find the post, so excuse me and refer me to the correct thread if I'm double posting.

My 'problem' is as followed. I had a small problem with network config that made it impossible for X to boot up and caused a smack of similar problems. As it was my own mistake and knew how to rectify it in the install procedure, I just re-installed (I mean it only takes a quarter of an hour so why not).

Problem: Now the bootlist in grub has 8 items, of which are a couple previous version boots and such, while I only need 4 (boot Ubuntu, Recovery, Memtest and XP) 

So is there a way to 'clean' the list?

---

### Post by codejunkie on 2006-01-21
[QUOTE=Maupertus]I know I've read something about this, but I can't find the post, so excuse me and refer me to the correct thread if I'm double posting.

My 'problem' is as followed. I had a small problem with network config that made it impossible for X to boot up and caused a smack of similar problems. As it was my own mistake and knew how to rectify it in the install procedure, I just re-installed (I mean it only takes a quarter of an hour so why not).

Problem: Now the bootlist in grub has 8 items, of which are a couple previous version boots and such, while I only need 4 (boot Ubuntu, Recovery, Memtest and XP) 

So is there a way to 'clean' the list?[/QUOTE]
run ```
sudo gedit /boot/grub/menu.lst
``` and comment out with # or remove the unwanted entrys it's best to comment them out incase remove the wrong one though you could also remove the kernels/linux-image packages in synaptic that your not using they can build up after a while hope this helps.

---

### Post by blair on 2006-01-21
As implied by codejunkie's excellent response, what you see in the GRUB menu when your PC boots up is controlled by what is contained in the menu.lst file which resides in the /boot/grub folder. When you don't like what you see when the grub menu is shown, the menu.lst file is the file you edit. 

If you scroll down to the end of the doc you will see groups of lines that look something like this:

title Ubuntu 2.4.10-6
root (hd0,0)
kernel /vmlinuz-2.4.18-5.47 ro root=/dev/sda2
initrd /initrd-2.4.18-5.47.img

For every "title" tag, you will see one entry in the GRUB menu. You should comment out each line (with a # as the first character) each associated with the entry, e.g. to make the above disappear in your grub menu change it like this: 

#title Ubuntu 2.4.10-6
#root (hd0,0)
#kernel /vmlinuz-2.4.18-5.47 ro root=/dev/sda2
#initrd /initrd-2.4.18-5.47.img

when you are done, you probably only need a single entry for Ubuntu, and perhaps your Windows OS if running a dual boot system. Note also that you can put whatever you want in the title tag. For example, if you don't like "Ubuntu 2.4.10-6", just edit the title tag value to "Ubuntu" or "Linux" or "Ubuntu 5.10", etc. 

you should always make a backup of your menu.lst file before you mess with it so you can restore your original file if needed, e.g.:

cp /boot/grub/menu.lst /boot/grub/menu.lst.original


Note that if you ever do a system software update and a new linux kernel image is pushed to you it will add new entries to your grub menu and you will suddenly see entries there that you didn't see before. When this occurs, simply go back into menu.lst and comment out the older references to the original kernel so all you will see is the newly installed kernel. Your grub menu will then look normal again.

---

### Post by JAwuku on 2006-01-21
An automated way I found is to open up Synaptic, and then just uninstall the old linux kernel images you no longer use (e.g. if you had the old package ***linux-image-2.6.12-10-386***, and you already had upgraded to ***linux-image-2.6.12-10-686***, you can uninstall the 386 kernel).

This automatically updates your Grub configuration file. The next time you boot, all the old kernels you uninstalled would not be shown.

This saves from manually editing any files.

---

### Post by jonathanm on 2006-01-21
i hav got rid of the memtest option, i have ran it before but what use is it?

---

### Post by ubuntuuser on 2006-01-21
I would recommend that you keep old kernel versions some time (I usually keep them ca. six months) so that you can always go back and use an older kernel if you encounter problems with the newer ones. After some time you can still use apt to remove old kernels.

---

### Post by Maupertus on 2006-01-24
Thanks guys, I used the text editing way, just to peek under the hood.

Worked like a charm.

---

