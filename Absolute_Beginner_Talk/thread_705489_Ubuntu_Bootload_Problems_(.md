---
title: "Ubuntu Bootload Problems :("
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by doomsdaydave11 on 2008-02-23
Ok, I booted to Ubuntu Studio 7.10 64-bit last night. The bootloader was fine, everything was there. Then, this morning when I come up to switch back to Windows (I converted some video that took all night), it was gone. I know Windows is still there, because I can see it from Linux, but in the GRUB bootloader it doesn't show it. Is there any way I can repair this bootloader to boot both Windows XP and Linux once again?

---

### Post by mikewhatever on 2008-02-23
Post the outputs of the following commands from terminal:
sudo fdisk -l
cat /boot/grub/menu.lst
cat /boot/grub/device.map
Hope there is a terminal in Ubuntu Studio.

---

### Post by (((X))) on 2008-02-23
Post your /boot/grub/menu.lst file. Give menu.lst .txt extencion to upload..

---

### Post by doomsdaydave11 on 2008-02-23
here is a copy of my menu.lst. This sucks. I want to play a game! It's my Saturday off!

(hd0)   /dev/hdb
(hd1)   /dev/sda

---

### Post by (((X))) on 2008-02-23
Ok
You have no winows in your list, you know that..
add those lines  after ubuntu entries:

title                    Windows
root                    (hd0,1)
savedefault     
makeactive
chainloader       +1

You will be ok if it is oem windows

---

### Post by doomsdaydave11 on 2008-02-23
OK, thank you. I'll add them, reboot, and see what happens :)

---

### Post by doomsdaydave11 on 2008-02-23
Thank you for your assistance. I in Windows posting this right now :). The code you gave me needed some minor adjustments, but it works great.

---

### Post by (((X))) on 2008-02-23
Good:)

---

