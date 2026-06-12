---
title: "vista upgrade killed Grub"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Phone33 on 2007-11-23
i had a dual boot XP/Ubuntu PC then i upgraded my PC from XP to vista. after the upgrade my grub still shows XP as my other choice however i only have vista and when i chose the XP option it fails to boot. i cna get vista to doot if i go into my boot sequence and make the widows hard drive a highter priority than the Ubuntu. Any idea on how i can make my grub live again?

---

### Post by TeaSwigger on 2007-11-23
Hello :) If the Vista install didn't over-write the ubuntu partition, then no worries. This helps to explain how you can reinstall your GRUB:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by meierfra on 2007-11-23
Let me first see whether I understand the situation correctly:

1) If you boot regulary, you get the Grub-menu. Choosing ubuntu works fine, but choosing  XP fails?

2) When you change the boot order, you boot  directly into  vista but you do not get an option to boot into XP and you do not get to the grub-menu ?


Is XP on the same hard drive as ubuntu? On the same drive as Vista? Or do you have three hard drives?

Post the output 

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

(both "l" are lower case L, not the number one)

---

