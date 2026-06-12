---
title: "Boot loader stoped showing"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Truck449 on 2007-09-24
Im a true noob and after a friend of mine installed ubuntu on my computer n created a boot loader i recently updated ubuntu and the computer now boots directly to ubuntu. While i use to be able to choose the operating system from the boot loader
any ideas?
thank you

---

### Post by alienexplorers on 2007-09-24
You may need to edit menu.lst to reset the /boot/grub/menu.lst as shown below.

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu


---

### Post by Truck449 on 2007-09-24
tried that already used the script on my freinds computer n edited menu.lst and also edited the boot.ini file  it had no effect

---

### Post by Truck449 on 2007-09-24
i located a file called lilo that i assume was downloaded in the update that reset the system to boot linux by default
 dont know if this helps

any advice is greatly appreciated

---

### Post by alienexplorers on 2007-09-24
lilo like grub is a boot loader.  You can use either of them.

---

### Post by Truck449 on 2007-09-24
is there a way to switch from lilo back to grub because lilo will not boot windows

---

### Post by alienexplorers on 2007-09-24
You will need to boot your windows disk into recovery mode.  Type in fixmbr.  Then exit and reboot.
Put your live-cd in the drive and reboot into the ubuntu OS.  Bring up terminal and type sudo grub. Then type:
> find /boot/grub/stage1
You will get an output like (hd0,0)
Type in:
> root (hd0,0)
setup (hd0)
exit and reboot.

---

### Post by Truck449 on 2007-09-24
i dont currently have my live cd, while booting i held down shift in order to access lilos default boot loader and when i tried to boot windows it just gave me a disk error message. do you have to manually set up the files for booting windows through lilo

---

### Post by alienexplorers on 2007-09-24
You might have to, though I am not sure.  I know in grub you sometimes have to edit it's config file.  Maybe lilo has something like that.

---

