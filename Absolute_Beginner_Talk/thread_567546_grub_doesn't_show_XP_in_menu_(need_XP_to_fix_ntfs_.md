---
title: "grub doesn't show XP in menu (need XP to fix ntfs partitoin)"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by jay123035 on 2007-10-04
please help. i have been trying to get a dual boot of Ubuntu and xp up for the last four days. 

my current and hopefully last issue is two issues in one. when resizing a ntfs partition on my external hard drive i messed up the file system. from what i have found i need to boot into windows and run 'chkdsk if' then reboot twice. that said the grub menu at start up shows 4 Linux kernels (two "normal" and two recovery) and a meta...something86. non of witch is xp.

my first try at Ubuntu was feisty and its/that grub showed xp with no issues. currently im trying Dapper Drake

after some googling i tried to run

jay@henry:~$ /boot/grub/menu.lst

but got

bash: /boot/grub/menu.lst: Permission denied

if i could get the menu open, one site recommended adding this at the bottom

title		Windows 95
root		(hd0,1)
makeactive
chainloader	+1


at this point i don't really care to much about a working dual boot. i just NEED to save the partition on the external HD and thats the only option i have found.

---

### Post by ericartman on 2007-10-04
Not sure if this will help but everytime I toasted my grub I used SuperGrub to fix it. It allows you to boot into your windows or Linux systems. There are other choices out there but SuperGrub always worked for me.

Cart

---

### Post by CaptainInsaneO on 2007-10-04
The command to open your menu.lst is this:

```
sudo gedit /boot/grub/menu.lst
```

---

