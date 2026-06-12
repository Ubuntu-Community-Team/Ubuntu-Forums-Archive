---
title: "Help..."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by J@Y13 on 2007-02-04
This is my first time trying out Linux, and I just installed Ubuntu on my computer. After I log in, I see a beige background, and a white box that is obviously messed up (like a graphics problem) I have read many posts and I can find nothing that will fix it. If anyone know how to fix it, please help.


Computer specs:

ABIT AT8 32X MOBO
GEFORCE 7800GT
2GB CORSAIR MEMORY
WD 250GB HD
AMD ATHLON  64 X2  4400 PROCESSOR

---

### Post by shareMenaPeace on 2007-02-04
Hi, do you use the 32 bit or 64 bit ubuntu iso?

---

### Post by J@Y13 on 2007-02-04
I am using the 6.10-alternate-amd64 iso....I first tried the desktop-i386 version and the same thing happened.

---

### Post by shareMenaPeace on 2007-02-04
No error message during install or boot?

---

### Post by J@Y13 on 2007-02-04
nope.....I thought all was well until i log in....then I cannot do anything

---

### Post by shareMenaPeace on 2007-02-04
Can you login with failsafe session (from login)?

---

### Post by J@Y13 on 2007-02-04
when i start my pc, i get a menu to start ubuntu, ubuntu (recovery), or windows...I am using the same hd. I haven't seen failsafe....

---

### Post by shareMenaPeace on 2007-02-04
When you enter the login screen, it lets you choose failsafe under session, try it.

---

### Post by J@Y13 on 2007-02-04
I tried it and the graphics are still messed up(where I can do nothing) .....I also tried failsafe terminal...but couldnot make out the text in the box....any other ideas? 


ps -I'm such a noob

---

### Post by shareMenaPeace on 2007-02-04
Try burning the Ubuntu Live CD again with slowest burn speed.

And check these searches
[http://www.ubuntuforums.org/search.php?searchid=13946731](http://www.ubuntuforums.org/search.php?searchid=13946731)

[http://ubuntuforums.org/showthread.php?p=2050923](http://ubuntuforums.org/showthread.php?p=2050923)

---

### Post by deadgobby on 2007-02-04
You have a AMD and using 32bit. So we'll have to do this OK.
Installation/32bitonAMD64

Often when installing Ubuntu i386 on an AMD64 board you will have to hit F6 and enter the following paramaters

irqpoll pci=noacpi noapic nolapic acpi=off

to get The Ubuntu i386 Alternate or LiveCD to Boot correctly. 
[https://help.ubuntu.com/community/Installation/32bitonAMD64](https://help.ubuntu.com/community/Installation/32bitonAMD64)
 All so the Vid card may be the problem too. But lets try the above first. Sound good??
Gobby

---

### Post by J@Y13 on 2007-02-04
Yeah the sound is fine...


Thanks
Since it is already installed I should press e (to edit) before i load right.....or can i press F6 at the login screen.

---

