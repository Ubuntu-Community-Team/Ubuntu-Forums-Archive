---
title: "Grub Conf, GrubConf install help!"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by richyrichuk on 2007-05-12
hello!!! ok im not gonna lie to you i've been a windows boy all my life...and only now i am crossing over, i kno nothing about linux ubuntu at all, i have read through the forums a fair bit.

basically managed to install ubuntu on to a harddrive with windows on already, managed tht didnt screw up my pc, windows works fine, but i just want to change the boot order so it auto boots to windows.

now i have downloaded GrubConf, but in gods name how the hell do u install it?!?! were is the 'exe' file that u run it with, i cant see any bin files, i am just stuck, i dont kno poop about linux :( can some 1 point me in the rite direction. cheers


rich!!

---

### Post by wormser on 2007-05-12
You just need to edit the menu.lst.

```
sudo nano /boot/grub/menu.lst
```
 
Then enter in your user password.

Towards the top of the file you will see:  default     0.  That line says the first one on the list will be booted when the timer finished counting down.  Remember it starts counting at 0.  Go towards the bottom and you will see all the OS on the system.  If it is a dual boot then XP should be the 3rd one on the list.  Since we start at 0 then XP would be number 2.  Change the default to whatever XP is then reboot.

---

### Post by richyrichuk on 2007-05-12
> **wormser said:**
> You just need to edit the menu.lst.

```
sudo nano /boot/grub/menu.lst
```
 
Then enter in your user password.

Towards the top of the file you will see:  default     0.  That line says the first one on the list will be booted when the timer finished counting down.  Remember it starts counting at 0.  Go towards the bottom and you will see all the OS on the system.  If it is a dual boot then XP should be the 3rd one on the list.  Since we start at 0 then XP would be number 2.  Change the default to whatever XP is then reboot.


i have managed to open it in a terminal, how do i save it??? just it saves as menu.lstsave and save1..

cheers

rich

---

### Post by confused57 on 2007-05-13
See #2 in the page index of this link:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

If you use nano, to save you: ctrl+x,y,enter...the ^ means the ctrl key.

---

### Post by richyrichuk on 2007-05-13
[size="6"]kings!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!![/size]



F****g Ace!!!!

Sorry If No Swearing Here :$ But Im Happy :d

---

