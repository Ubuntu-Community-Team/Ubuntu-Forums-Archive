---
title: "Radeon X1300  - Enabling/Checking Hardward Acceleration"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by proxima estacion on 2007-01-24
Hi,

I'm trying to get 3d Desktop going (the main reason I switched from Windows). I have a X1300. I downloaded the package (3ddesktop) but it obviously doesn't work. 

Every forum I have seen says make sure you have hardware acceleration enabled. this is easy to check in windows but I cant find out how to check/enable  it in Ubuntu,


Any pointers or ideas?? 


Thanks

---

### Post by Shatrat on 2007-01-24
To check you can use the command glxinfo | grep rendering
If it says no (and it will) then you dont have direct rendering.
To fix it you need to install the appropriate drivers.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by proxima estacion on 2007-01-24
Thanks - worked first time!!

---

