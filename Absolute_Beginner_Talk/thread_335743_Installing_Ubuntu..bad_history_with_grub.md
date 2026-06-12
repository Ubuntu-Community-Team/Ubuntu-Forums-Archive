---
title: "Installing Ubuntu..bad history with grub"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by ledzeppelin265 on 2007-01-10
I recently tried to install redhat, and the grub bootloader messed up my computer pretty bad, i was installing it onto a slave drive and after that *nothing* would boot, not even my windows drive.

so i ended up formatting both drives because i had no other way to fix it.  ](*,) 

im now considering ubuntu, i was given a disk about a year ago and figured id try it out. 
i was wondering whether taking out my windows drive when i install ubuntu onto my slave drive would prevent me from being able to dual boot. 

i have a dell dimension 3000 if that matters

thanks

---

### Post by pissedoffdude on 2007-01-10
> **ledzeppelin265 said:**
> I recently tried to install redhat, and the grub bootloader messed up my computer pretty bad, i was installing it onto a slave drive and after that *nothing* would boot, not even my windows drive.

so i ended up formatting both drives because i had no other way to fix it.  ](*,) 

im now considering ubuntu, i was given a disk about a year ago and figured id try it out. 
i was wondering whether taking out my windows drive when i install ubuntu onto my slave drive would prevent me from being able to dual boot. 

i have a dell dimension 3000 if that matters

thanks

If you take out your windows drive it will not be detected by the installer and therefore not add windows to the grub menu automatically.  Although you can just manually edit the grub menu list and easily add windows to it.  To add windows manually to your grub menu do: ```
gksudo gedit /boot/grub/menu.lst
``` then you add these lines: ```
title Windows XP 
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
```

---

### Post by ledzeppelin265 on 2007-01-10
thanks, ill try that or just leave the drive in and do it, im just wary because i dont wanna have to format again

---

