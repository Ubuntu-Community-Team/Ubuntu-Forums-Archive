---
title: "Login Window Resolution? (Solved)"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by OmegaOne on 2005-11-24
i know this is probably a silly question, but i cannot seem to change the resolution on the login screen. it is currently using the highest that my monitor can handle, and this makes my monitor go a bit nuts. ive tried logging in as root and changing the resolution there, and i changed it as my main user, but neither seems to apply to the login screen.

little help please?

thanks

---

### Post by linbetwin on 2005-11-24
Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=94547&highlight=login+resolution](http://ubuntuforums.org/showthread.php?t=94547&highlight=login+resolution)

---

### Post by aysiu on 2005-11-24
Can your monitor handle 1024 x 768? If so, try this:

Open up a terminal (Applications > Accessories > Terminal) and type these commands in: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Then, scroll down to your relevant Ubuntu entry. Let's say, for example's sake, it looks like this ```
title           Ubuntu Linux
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda8 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
``` Tack on vga=791 so it looks like this instead ```
title           Ubuntu Linux
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda8 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
``` Then save (control-x), confirm save (y), and exit (Enter). Should work.

---

### Post by OmegaOne on 2005-11-24
[QUOTE=linbetwin]Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=94547&highlight=login+resolution](http://ubuntuforums.org/showthread.php?t=94547&highlight=login+resolution)[/QUOTE]

Thanks for that, it worked ^_^

i did a search before i posted (and tbh didnt know what i was really looking for) but this fixed it :D

now logging in at only 1280 by 1024 (instead of 1900 or something)

thanks

---

