---
title: "Boot into Widows first"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Glaurungg on 2007-11-06
Hi 

I have ubuntu and windows on seperate HDs how do I get my computer to boot into Widows first (auto)

I am not ready to make the big change yet.

Thanks Bill

---

### Post by vree13 on 2007-11-06
Hello. I understand that hesitancy to make the big switch.

Assuming that you are using grub to boot, you'll need to edit your menu.lst file. This is generally located in /boot/grub/menu.lst

Start by making a backup copy of your current menu.lst.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

You can edit the menu.lst as root with whatever text editor you prefer. I like gedit. So, to edit this file, you can do this:
```
gksudo /boot/grub/menu.lst
```

Now, you'll likely see something like this toward the end:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```
Cut this out (or comment it out and copy it if you're paranoid) and place it before this line
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

```
Do not place it after that line, or you'll have problems when you do kernel updates. You can also change the timeout period in this file. For more info, you can search the forums or Google for "menu.lst" and you'll likely find lots more info on tweaking it. 

Good luck!

---

