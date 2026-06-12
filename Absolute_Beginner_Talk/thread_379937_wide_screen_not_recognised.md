---
title: "wide screen not recognised"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by black drongo on 2007-03-09
hi 
i am new to ubuntu. to add to it i have very limited ( practically nil ) experience in linux, though i have heard a lot of it.i have downloaded and installed ubuntu 6.10  -64 bit. 

  problem is ubuntu is not recognising my widescreen display (ViewSonic, VG1930wm).also the maximum resolution it allows me to have is 1024x768. where as the native resolution of my lcd is 14440x900. i have an ASUS board with NVIDIA chipset.(GeForce 6150).i got some local help and he tried to install nvidia drivers-it comes as a package- but  it says source code for kernel is not available.
     can anybody help ? pls.

---

### Post by Famicommie on 2007-03-09
Try to follow the instructions here:

[http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9755.html)

---

### Post by pandu.rs on 2007-03-09
To install properiatery nvidia driver
Refer [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

After completeing the instructions there, run the following command
dpkg-reconfigure xserver-xorg

choose nvidia in the first screen and in the resolution screen choose the desired resolution. (for all other screens just press enter and accept defaults, unless you know about what u r doing)

---

### Post by black drongo on 2007-03-09
**[SIZE="3"]wow![/SIZE]**
 **[COLOR="Magenta"]Thank you  guys.. [/COLOR]**
it came fine

pandu, ur suggestions worked.
  
Though i was on the edge of my seat- hey i am a nubi, that blue screen of xorg scared me ########.- it was fun.
thanks again frnds
see ya again

---

