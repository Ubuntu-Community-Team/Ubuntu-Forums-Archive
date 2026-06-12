---
title: "Removing the Ubuntu Start Up Logo?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by chrispche on 2007-11-14
How do you remove the startup Ubuntu screen. So that I can see what services are starting up and then shutting down when I shut down. I want this to be permanent.

Thanks.

---

### Post by Hallvor on 2007-11-14
```
sudo gedit /boot/grub/menu.lst 
```

Then change "splash" to "nosplash" and remove "quiet". I`m not in front of my regular computer, but that should do it. 

Reboot...

---

### Post by Partyboi2 on 2007-11-14
```
gksudo gedit/boot/grub/menu.lst
```scroll down till to you find
> title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=965b3166-7681-4899-bb14-34e36370c8a0 
initrd        /boot/initrd.img-2.6.22-14-generic ro quiet splash
then remove ad no to splash and remove quiet
Save and reboot
:)

---

### Post by geirha on 2007-11-14
Actually, a better way is to browse down to the line in menu.lst that looks like
```
# defoptions=quiet splash
```
and change it to
```
# defoptions=
```
Then run ```
sudo update-grub
``` to have that change done on all the ubuntu entries. If you edit the ubuntu entries manually, the splash screen will return on the next kernel upgrade.

---

### Post by chrispche on 2007-11-14
Thanks all sorted.

---

