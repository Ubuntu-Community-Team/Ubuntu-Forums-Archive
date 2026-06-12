---
title: "Whoa! Where's my Windows?!"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-27
I was prompted to download some packages by the update manager. When I rebooted my GRUB only showed the Linux OS's, not my Windows OS. I also had Reboot and Shutdown options there and they've dissappeared to!

I know I need to edit my /boot/grub/menu.lst file and add something but I'm not sure what I need to add. Please Help!

---

### Post by mostwanted on 2006-05-27
If you have Windows installed as in the number one partition of the first harddisk the position would be hd1(0,0) and then you'd only need someone else with Windows installed to give you the correct section of their grub file so you can append that. I have no idea where the grub file is in SUSE 10.1 so I can't help you.

**Someone else please assist this user.**

---

### Post by catlett on 2006-05-27
If you can get in Ubuntu then enter ```
sudo gedit /boot/grub/menu.lst
```
Hit enter a couple of times to get some space between the last entry and this. 
```
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
This entry will work if windows is on the first partition of the first hard drive. It will be there if windows was on first and you installed linux later.
I don't know about the reboot and shutdown entries. You could probably google for grub commands or grub menu entries and see what comes up.

---

### Post by tartarian on 2006-05-28
Thankyou, now have my windows back.

If anyone was interested I got the Reboot / Shutdown by adding:
> 
title Shutdown
halt

title Restart
reboot


to my boot/grub/menu.lst file

Thankyou!

---

### Post by catlett on 2006-05-28
Thanks I didn't know that. We're one for one:D

---

