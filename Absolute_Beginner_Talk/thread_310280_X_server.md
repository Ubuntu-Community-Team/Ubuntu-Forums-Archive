---
title: "X server"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by ricardo.ssouza on 2006-11-30
I`m having a problem with the start of the X server.
Everytime I try to boot Ubuntu a message comes saying that the start of the X server failed, and starts Ubuntu like a DOS, I don`t know what to do! Can anybody help me?

---

### Post by LLRNR on 2006-11-30
Try```
startx
```If it doesn't work, ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by 23meg on 2006-12-01
What's your video hardware?

---

### Post by ricardo.ssouza on 2006-12-01
My video hardware is a GForce 7300 GT 256MB.

---

### Post by LLRNR on 2006-12-01
If you use Dapper try [this](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29), if you use Edgy try [this](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29). Anyway, that was for your graphic card's drivers. Did you get your GUI back ?

LLRNR

---

### Post by ricardo.ssouza on 2006-12-01
No I still don`t have GUI. 
When I try "starx", occurs a fatal server error: no screens found

---

### Post by LLRNR on 2006-12-01
Ok, but did you try ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by ricardo.ssouza on 2006-12-01
I tried that, and then tried to restart x again, and the same error keeps happening.

---

