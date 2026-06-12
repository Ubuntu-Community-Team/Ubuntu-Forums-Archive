---
title: "Booting Up (Grub) Problem"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Drezard on 2006-08-13
Hello, Im wondering with Grub can i make it so that it boots up windows as the top option? Not Ubuntu. I use ubuntu rarely (since i am going through the cycle of dropping windows and picking up ubuntu). Or is there a way to take off the timer that makes u have to choose within 9 seconds?

- Cheers, Daniel

---

### Post by Drezard on 2006-08-13
Please Help!.

Cheers, Daneil

---

### Post by foolsh on 2006-08-13
```
sudo gedit /boot/grub/menu.lst
```
then cut and paste the windows options above the ubuntu ones and save
the next time you boot windows will be the default os

---

### Post by Drezard on 2006-08-13
Please explain better im a newbie soz.

- Cheers, Daniel

---

### Post by confused57 on 2006-08-13
See this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Ignore the part about dualbooting with 2 hard drives, but pay attention to the commands needed to edit your menu.lst file and how to copy(highlight your Windows entry) and where to paste(middle click where you want it to go) your Windows entry.

---

### Post by foolsh on 2006-08-13
sure no problem
ok 
open a terminal session and type this command
```
sudo gedit /boot/grub/menu.lst
```
now scroll down to the bottom and find this section
```
title Windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)
```
note that your may look a little different
now click and select  everything in the section for windows click edit then cut from the menu at the top 
then find the first section that looks similar to this
```
title		Ubuntu, kernel 2.6.15-26-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash elevator=cfq
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot
```

click above this section and click edit/paste from the menu at the top

you might want to delete the line that says 
```
title other operating systems
```
then save the file
and that should be it reboot to have window load automatically

---

### Post by Drezard on 2006-08-13
I have a problem. Number 1. Is terminal that thing in Applications > Acessories? and Number 2. If it i typed that code straight in and it opened something that was totally blank. It opened something in text edit that was totally blank.

Please help me (Can u upload a file with that grub.lst thing and a place where i have to copy it or explaination on how to fix it?)

- Cheers, Daniel

---

### Post by foolsh on 2006-08-13
yes that is the terminal
opps that was my fault it should be
```
sudo gedit /boot/grub/menu.lst
```
the menu.lst file is specific to your computer they are configuration files

---

### Post by Drezard on 2006-08-13
Hey Thanks so much. I dont think you Linux pros get enough credit.

- Cheers, Daniel

---

