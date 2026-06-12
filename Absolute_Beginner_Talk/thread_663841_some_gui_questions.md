---
title: "some gui questions"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by jeisma on 2008-01-10
hi! 

on xubuntu 7.10, i wanted to get rid of the bootscreen so i modified the menu.lst

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root           (hd0,0)
kernel         /boot/vmlinuz-2.6.22-14-generic root=UUID=7485dcc2-f16d-4cbf-8ff1-6d171a194c33 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title            Ubuntu 7.10, memtest86+
root           (hd0,0)
kernel        /boot/memtest86+.bin

however the boot screen still appears.

also i dont want to use the gui login screen. i want to login in the console and maybe run startx(?) if i want gui.

lastly, how do you remove the icons in the desktop? i just want a clean plain desktop.


thanks a lot!

---

### Post by taurus on 2008-01-10
1.  Edit /boot/grub/menu.lst and remove the **quiet splash** (and the end of an entry for kernel) and the **quiet** (two lines below the kernel entry).

2.  Probably need to remove the gdm.
```
sudo apt-get remove gdm
```

3.  Try right-clicking with a mouse and delete them.

---

### Post by NilsE on 2008-01-10
1) If you change the following 2 lines it may help.  Make sure they read

timeout		1  (the 1 is one second that the starting up message shows, not the list of kernels.)

hiddenmenu   (this one says hide menu list of kernels unless esc it hit)

2) As far as just going to the command prompt I believe if you change this following line to the entry number for the recovery mode kernel entry it should get you what you want.  The first title entry is 0 the second is 1 etc. It is probably the second entry in the list at the bottom so it would be 1.

default		0

3) To remove the icons on the desktop go into the Configuration Manager and look for /apps/nautilus/desktop and check off the one you don't want.

---

### Post by deanjm1963 on 2008-01-10
what you did was correct, it's just that grub was not updated.

to get grub to stop displaying the boot screen you need to enter in a terminal

sudo update-grub

reboot and your boot screen should be gone

---

### Post by nowshining on 2008-01-10
First save anything now, then close out all application immediately - :)

by the way in system - administration - services

enter ur pw

uncheck GDM

u'll be automatically taken to a CLI, u can try out how to GDM in the tips and tricks and howtwo section of my site in my sig. :)

As for removing all icons from the desktop 

/apps/nautilus/preferences/show_desktop and un-check it

---

