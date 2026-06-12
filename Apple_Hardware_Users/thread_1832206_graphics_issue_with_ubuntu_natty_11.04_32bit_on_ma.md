---
title: "graphics issue with ubuntu natty 11.04 32bit on macbook pro 8,2"
date: 2011-08-24
forum: Apple Hardware Users
---

### Post by srikumar.b on 2011-08-24
Hi,
I installed Ubuntu 32 bit natty on my new macbook pro 2011 model.
It has AMD Radeon HD 6750M graphics card.

As soon as installation complete, everthing worked fine but it prompted me to install and activate the graphics card for better performance. After i install the driver & reboot, i am observing the below issues
1) Choppy screens/menus and refreshes 
2) Cursor is very choppy
3) lagging /delay on displaying characters on the screen while typing
4) Cursor position changes to different location 

I am getting this issue all the time after i installed the prompted driver.

lspci output shows:

lspci |grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series]
01:00.1 Audio device: ATI Technologies Inc Device aa90

Kindly help me to fix this issue

---

### Post by srikumar.b on 2011-08-24
Kindly help me here..I am really blocked and my computer is unusable with this issue...I tried installing Natty 3 times and still getting the same issue....

---

### Post by srikumar.b on 2011-08-25
I figured out the issue....
When i use "Ubuntu classic with No effects" while logging in, lot of graphics issues are observed but when i change it to "Ubuntu classic", everything worked fine....

I hope this will help for someone who see similar issue when they fall in the same trouble.

---

