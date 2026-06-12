---
title: "Triple Boot Issue"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Priddo on 2007-05-14
Hey guys,

On my laptop I have installed XP, followed by Ubuntu 7.04 and then Vista Ultimate.

After installing Ubuntu, I could select which OS I wanted to run, but after installing Vista I only have an option to run Vista or XP... (Surprising from Microsoft......). I was hoping someone could te me how to make it run the linux OS selector (I have no idea what its called) when booting, or maybe point me in the direction of a tutorial (I searched, but came up empty handed).

Thanks for any help, in advance :)

---

### Post by viciouslime on 2007-05-14
You might want to try this one:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29")

---

### Post by confused57 on 2007-05-14
You might be able to use the Vista bootloader to boot Ubuntu:
[http://ubuntuforums.org/showpost.php?p=2644308&postcount=7](http://ubuntuforums.org/showpost.php?p=2644308&postcount=7)

---

### Post by stuffour on 2007-05-14
Check out the following link. It might be of help;
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by Priddo on 2007-05-14
> **viciouslime said:**
> You might want to try this one:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29")

Trying this method I've got to the grub, with the partition mounted, but I can't work out my partitions numbers fro Grub.

Its /dev/sda3, and in Grub I've tried (hd0, 2) As I believe that is what it should be with no success...

I've only got 1 hard drive, so all of them should be hd0, I thought. I tried 0 - 10 after the coma, and even 1-4 after HD and nothing seems to be a drive... Do you know why that would be?:(

---

### Post by alienexplorers on 2007-05-14
Just boot your LiveCD

Bring up terminal and enter

> sudo grub

enter:

> find /boot/grub/stage1

You will get an output like (hd#,#)

enter:

> root (hd#,#)

enter:

> setup (hd0)

exit grub editor

reboot

---

### Post by Priddo on 2007-05-14
That has done the trick!

Thank you to all those who helped out! :)

---

