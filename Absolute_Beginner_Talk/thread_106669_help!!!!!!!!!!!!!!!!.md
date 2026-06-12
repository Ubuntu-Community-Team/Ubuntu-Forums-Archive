---
title: "help!!!!!!!!!!!!!!!!"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by AlMaSoUdI on 2005-12-21
hi all , i have 2 OS in my labtop Win XP and ubuntu, so i've formated my XP and i reinstalle it . now when i boot up my pc i can't find my ubuntu only XP work after that i install the GURB from the ubuntu'CD but still same....
when i on my pc the XP work with out asking me which one i want use so what sould i do ???:confused: :confused: :confused: :confused: :confused:

---

### Post by darth_vector on 2005-12-21
in the pause after the BIOS setup and before windows starts loading hit the 'ESC' key. this should get you into the grub menu.

once you boot into ubuntu, open the file /boot/grub/menu.lst and replace the line

hiddenmenu

with

#hiddenmenu

this way you will be prompted each time the computer boots.

---

### Post by AlMaSoUdI on 2005-12-22
[QUOTE=darth_vector]in the pause after the BIOS setup and before windows starts loading hit the 'ESC' key. this should get you into the grub menu.

once you boot into ubuntu, open the file /boot/grub/menu.lst and replace the line

hiddenmenu

with

#hiddenmenu

this way you will be prompted each time the computer boots.[/QUOTE]
i did what you said but when i hit the 'esc' nothing happen the win XP loading!!!!
i try so manythings but still same!!!
so....

---

### Post by frodon on 2005-12-22
[QUOTE=AlMaSoUdI]hi all , i have 2 OS in my labtop Win XP and ubuntu, so i've formated my XP and i reinstalle it . now when i boot up my pc i can't find my ubuntu only XP work after that i install the GURB from the ubuntu'CD but still same....
when i on my pc the XP work with out asking me which one i want use so what sould i do ???:confused: :confused: :confused: :confused: :confused:[/QUOTE]Did you follow those instruction to re-install GRUB ? : [http://www.ubuntuforums.org/showthread.php?t=76652](http://www.ubuntuforums.org/showthread.php?t=76652)

---

