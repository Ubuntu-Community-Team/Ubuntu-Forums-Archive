---
title: "Windows AFTER Ubuntu"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-07-01
i have installed windows on a seperate partition after using ubuntu, and windows seems to have wiped the GRUB boot loader...

:(:(:(

how do i get bak to ubuntu...

please help, and thanks in advance

---

### Post by Apple 101 on 2006-07-01
Boot into the Ubuntu Recovery mode using your CD/DVD.  Run the command: *grub-install /dev/sda* or whatever your drive is.  You can find out by running the command: *cat /etc/fstab* or *df*.

  For future reference, whenever you install Windows after Linux, save your Grub MBR, and then boot to it from the Windows boot loader.  I talked about this process in another thread...

---

### Post by tubunu on 2006-07-01
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub+mbr](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub+mbr)

---

### Post by shoot2kill on 2006-07-01
ok, thanks i will try

---

### Post by u.b.u.n.t.u on 2006-07-01
I always install XP first. Ubuntu makes a fast and good job of setting everything up correctly and the boot option. Ubuntu can handle XP well, but XP cannot handle Ubuntu well.

---

### Post by shoot2kill on 2006-07-01
HMMM, THE FIRST ANSWER DID NOT WORK BUT ANOTHER HOW-TO DID...

1. Pop in the Live CD, boot from it until you reach the desktop.

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).

3. Type "grub"

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

5. Type "setup (hd0)", ot whatever your harddisk nr is.

6. Quit grub by typing "quit".

7. Reboot. 


ONLY THING NOW, I CANT BOOT TO WINDOWS... NO OPTION IN GRUB MENU.. NO OPTIONS AT ALL...

sorry for caps lock, only just noticed

---

### Post by AndyCooll on 2006-07-01
You will need to manually add an entry into your /boot/grub/menu.lst. Something along the lines of:

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

I don't actually dual-boot with XP so maybe someone else will be able to confirm these details are correct.

:cool:

---

