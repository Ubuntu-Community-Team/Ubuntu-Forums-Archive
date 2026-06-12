---
title: "need GRUB advice!!!"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by inter-m on 2007-07-17
I just recently deleted XP and Im working with only Ubuntu on my laptop... My question is do I need to keep GRUB since Im flying solo now... Or should I delete it???:confused:

---

### Post by bernied on 2007-07-17
Do not delete grub. Grub is the bootloader that starts linux. Linux will not start without a bootloader.
If you want to make it neater, you can edit the file /boot/grub/menu.lst
```
sudo nano /boot/grub/menu.lst
```
You can uncomment the line that says '#hiddenmenu', just take awy the '#', this will stop the menu from coming up, instead you will get a single line telling you to hit Esc to access the menu.
You can change the amount of time that either the menu or the short message is displayed by changing the number of seconds on the 'timeout' line. Something like
```
hiddenmenu
timeout 2
```

---

### Post by inter-m on 2007-07-17
Thanx man thats exactly what I was looking for :)

---

