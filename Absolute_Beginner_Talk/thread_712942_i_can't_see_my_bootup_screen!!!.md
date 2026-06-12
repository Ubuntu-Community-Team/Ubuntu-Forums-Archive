---
title: "i can't see my bootup screen!!!"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by gnome.youbuntoo on 2008-03-02
[SIZE="3"]i can't see my bootup screen!!! I directly go to* Username* screen[/SIZE] I have a Pentium 4 with Intel 845G motherbard. Plz help.

---

### Post by forestpixie on 2008-03-02
once you've booted check this file - to see if hiddenmenu is enabled

cat /boot/grub/menu.lst

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

if it lloks like this put a # in front of hiddenmenu

---

