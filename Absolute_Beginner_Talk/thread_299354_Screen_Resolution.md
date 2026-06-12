---
title: "Screen Resolution"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Mohit on 2006-11-14
Hi

While running in WindowsXP,
I can change the screen resolution
but while working in Linux, 
The screen resolution is fixed to (640*480) 
How can i change this resolution,
Linux doesnot allow to change through, System>Prefrences>Screen resolution.

Please help
Mohit

---

### Post by Bachstelze on 2006-11-14
[Here](https://help.ubuntu.com/community/FixVideoResolutionHowto) you go :)

---

### Post by Mohit on 2006-11-14
Hello

Can u sort this problem

Mohit

---

### Post by LsrLine on 2006-11-14
Accessories > Terminal
type this: sudo dpkg-reconfigure xserver-xorg
Run through the wizard, and you'll eventualy reach a screen resolution screen.  Select the right resolution by hitting the space bar on it... finish the wizard and then reboot your computer.

---

### Post by Mohit on 2006-11-14
I already did that but this not working
then wat to do.

mohit

---

### Post by hashimoto on 2006-11-14
Run the wizard again and make sure that you enter correct refresh frequencies (horizontal and vertical). This is essential to get all supported resolutions. You get that information from you monitor's manual. 

Also, make sure that you select all the resolutions that your monitor supports.

---

### Post by Mohit on 2006-11-14
Its taking Default
not allowing me to change the resolution or frq
it is set at (640*480)
wat to do
Mohit

---

### Post by stevey2005 on 2006-11-14
I had the same problem. I found out that the monitor does not support any high resolutions that wat the OS set as the default (648 by 480)

---

