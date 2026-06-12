---
title: "external HDD installed ubuntu. help!"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by short3000y on 2007-12-04
hi, i have installed Ubuntu onto a external HDD of mine and now i have the issue of having to have it plugged in when i boot because of Grub.:( is there any way of getting around this?:confused: or would i have to re-image my computer to make it work again. please help. i have alot of information on both my ubuntu drive and my windows drive that would make me very sad to erase.
Thank You
~Nate

---

### Post by LaRoza on 2007-12-04
> **short3000y said:**
> hi, i have installed Ubuntu onto a external HDD of mine and now i have the issue of having to have it plugged in when i boot because of Grub.:( is there any way of getting around this?:confused: or would i have to re-image my computer to make it work again. please help. i have alot of information on both my ubuntu drive and my windows drive that would make me very sad to erase.


Where did you install grub?

If you installed grub on the internal drive, and not the external, you can restore the Windows bootloader with the Super Grub Disk. See the link in my sig for that.

---

### Post by short3000y on 2007-12-04
thank you. the bootloader was my problem. but how do i use the Super Grub Disk? i burnt the ISO onto a cd. now what?

~Nate

---

### Post by short3000y on 2007-12-05
sorry for double posting, i got windows to boot properly, but how do i get ubuntu to boot through just the external, instead of needing to go trough the computer?

~Nate

---

### Post by LaRoza on 2007-12-05
What do you mean by "going through the computer"?

If you mean manually selecting it from BIOS, you can set your computer to boot from USB devices first. This way, if you plug it in (the external) it will boot.

---

### Post by short3000y on 2007-12-05
my problem is that linux wont boot now, its on the harddrive, but there is no loader on the external for it. do i need to reput grub on it?

---

### Post by short3000y on 2007-12-05
can anyone help?

---

### Post by PmDematagoda on 2007-12-05
Why don't you use SuperGRUB to install GRUB on the MBR? After that you probably can use both Windows and Ubuntu.

---

