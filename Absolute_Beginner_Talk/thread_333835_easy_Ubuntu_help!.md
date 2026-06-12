---
title: "easy Ubuntu help!"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by leonstars on 2007-01-08
ok i have easy ubuntu installed and i am wanting to know 
which nvidia driver should i install

i have a nvidia geforce 3 Ti  64 meg of ram 
 
                     any help please 
                         
                             thanks

---

### Post by riven0 on 2007-01-08
If I'm not mistaken, all you have to do is this:

> sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx

Since I don't have a nVidia card, though, I'm not completely certain...

---

### Post by justin_c18 on 2007-01-14
> **leonstars said:**
> ok i have easy ubuntu installed and i am wanting to know 
which nvidia driver should i install

i have a nvidia geforce 3 Ti  64 meg of ram 


If you have Dapper;
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29")

If you have Edgy;
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29")

Hopefully that helps,
Justin

---

