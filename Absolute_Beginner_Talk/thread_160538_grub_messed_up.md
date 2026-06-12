---
title: "grub messed up"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by hellfried on 2006-04-15
i had to reinstall ubuntu 5.1 over the same parition where i had it on earlier. now my poor grub loader has 2 entries for every option. how do i edit this file and is it safe?

---

### Post by dcstar on 2006-04-15
[QUOTE=hellfried]i had to reinstall ubuntu 5.1 over the same parition where i had it on earlier. now my poor grub loader has 2 entries for every option. how do i edit this file and is it safe?[/QUOTE]
```
gksudo gedit /boot/grub/menu.lst
```
Yes, but be careful.

---

### Post by oscar on 2006-04-15
[edit]dcstar beat me to it[/edit]
 Perhaps make a backup somewhere to restore if you mess up.
It is possible that you acutally have 2 installations, your new one didn't overwrite your old one, and grub has detected these and made them bootable, worth checking. When looking at your menu.list check that they all refer to the same partition (hd0,1) or whatever it is.

I think there is an alternative to editing it by hand which is to run:
```
sudo update-grub
```
Which updates your menu.list to match your installed kernels

---

### Post by hellfried on 2006-04-15
sudo update-grub did not work for me. looks like i have to do it with gedit. anyways another weird thing is now i have 3 icons on my dekstop which i never had in the previous installation. they are for sda1, sda4 and sda5. sda1 is where my winxp is and sda4 is another partition that was formatted previously by winxp to ntfs. sda5 where my fat32 parition where i was sharing some files between ubuntu and winxp previously. when i click on sda1 and 4 it says i cannot open them.why then do i have them on the deskktop! how do i get rid of them?

---

### Post by oscar on 2006-04-15
You have them on your desktop because ubuntu automatically found and mounted them, thinking you might want to use them it put links to them on your desktop. It is possible to mount the ntfs partitions as read and writeable but is experimental. See [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481) for more details. If you dont want them I think you can just edit your /etc/fstab and remove the lines starting with /dev/sda1 and /dev/sda4. When you restart they should be gone.

---

