---
title: "Can i Install Windows XP on Ubuntu(not dual-boot, wanna remove ubuntu) with OEM disk?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by aberrantxd on 2008-02-04
I had windows xp. i then installed ubuntu fiesty. Sadly i am not satisfied with ubuntu and would like to switch back to Windows. I was wondering, can i use an oem disk to install windows xp again? or do i have to buy the 200$ retail version.

---

### Post by wiseguyxp on 2008-02-04
if it is the OEM that came with the computer, then it should be fine

---

### Post by aberrantxd on 2008-02-04
what if it isn't( oem i got off ebay?)

---

### Post by pieisgood4589 on 2008-02-04
Any Window$ re-installation disk will do.

---

### Post by aberrantxd on 2008-02-04
are you sure because i used an xp pro reinstallation disk and it did not work. If i didn't partition the hard drive(used whole hard drive for ubuntu) would i still be able to use an oem? I dont think Windows xp is on my pc anymore.

---

### Post by oedha on 2008-02-04
have you try to install it ?
the problem will be : you will ask to confirm about the code....

question : why dont you make it dual boot at that time ?

---

### Post by dwanders on 2008-02-04
You should boot off the Windows Disk, and follow the steps to install it. (If you have a CD key for the disk you have - if you don't have a key, go buy and new version of XP with a key and install it - that is the CON of Windows, there is no free ride on that ship). 

You may run into a small problem where the MBR is still hosed after the reinstall of XP, this is fixed by booting from the Windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.

Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restart the computer.

If you don't follow anything I have said above, then you are about to enter the real world of computing very quickly that most users just don't get to experience enough.

:guitar:

---

### Post by mdpalow on 2008-02-04
Why Fiesty?

Should have installed 7.10...

---

