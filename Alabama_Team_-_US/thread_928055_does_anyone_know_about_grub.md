---
title: "does anyone know about grub?"
date: 2008-09-23
forum: Alabama Team - US
---

### Post by insanelyderanged on 2008-09-23
ok i have tried everything i have found about this and i still can not get the grub splashimage to show up lol

i am using the latest ubuntu by the way and i am kind of stuck with the plain grub screen lol

if anyone knows anything about this please help? lol

---

### Post by Sub101 on 2008-09-23
This should help:

[http://ubuntuforums.org/showthread.php?t=240917](http://ubuntuforums.org/showthread.php?t=240917)

---

### Post by michaelramm on 2008-09-23
That is what I did a long time ago to get a custom splash screen. It worked perfectly for me.

Michael

---

### Post by insanelyderanged on 2008-09-23
ok this didn't actually work for me but i finally realized what i was doing wrong
while every tutorial has the (hd0,1) that didn't work for me instead i had to use 
splashimage ()/ubuntu/disks/boot/grub/splashimages/image1.xpm.gz
as the full line for it lol
so anyone who has the same problem might be able to use that
splashimage ()/ubuntu/disks
that in place of the (hd0,1) works but only if it shows that is the root

---

### Post by michaelramm on 2008-09-24
Glad to see that you were able to work out a fix for it!

Talk to you (hopefully) on Thursday night in IRC.

Michael

---

