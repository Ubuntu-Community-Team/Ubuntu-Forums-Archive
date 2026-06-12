---
title: "grub is always part of the boot up?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by paxton on 2007-01-07
Hello, I'm new. :D 

I am installing the latest Ubuntu on my laptop. I had winxp on there, but now I want to dedicate my 80gb to just Ubuntu and no windows.

So I go through the installation of Ubuntu. When I got to the partition part, I select for it to erase the entire disk. It then installs and when it restarts... I see a Grub thing for 5 seconds or so.

Is the grub menu going to be always there? I'm only running Ubuntu, no dual boot or anything. 

When I go into the grub menu it shows the current kernel, a recovery one and then a memtest86 selection. Isn't there a F8 type option like for WinXP, where you are offered different ways to boot when you hit F8? I'd like Ubuntu to boot straight into the splash without going to grub. If I want to do a recovery thing in Ubuntu isn't there a F8 type thing, which at that point I'd be offered a way to select a different boot?

I don't know... did I even install it properly? ](*,)

---

### Post by The Joe on 2007-01-07
GRUB will stay yes, but it won't open automatically. It will stay there so you can select Recovery Mode and Memory Test, it's actually rather helpful.

Amendment: It will automatically go to Ubuntu.

---

### Post by meng on 2007-01-07
You can reduce the length of the "timeout" before grub boots the default option. You can also make grub hidden by default (I think you press ESC to bring it up at boot if you need a recovery option.

Edit the /boot/grub/menu.lst, the lines are called:
timeout
and
hiddenmenu

---

### Post by teaker1s on 2007-01-07
boot loader instead of windows master boot record, it's your friend;)

---

### Post by geek_Man on 2007-01-07
You can make it go right into Ubuntu if you want. Post your menu.lst file, so I can have a look. And welcome to Ubuntu!

EDIT: Jeez, I'm always too slow...

---

### Post by paxton on 2007-01-07
Thanks for the help, clarification and welcome! \\:D/

---

### Post by meng on 2007-01-07
To post your menu.lst, 
cat /boot/grub/menu.lst

---

### Post by The Joe on 2007-01-07
Ah yeah to edit the GRUB menu go to terminal and type ```
gksudo gedit /boot/grub/menu.lst
``` Be careful what you do with it though.

---

