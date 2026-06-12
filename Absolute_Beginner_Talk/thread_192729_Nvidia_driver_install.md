---
title: "Nvidia driver install"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by DevilStinger on 2006-06-09
hello to everyone in this forum!

i'm new in using ubuntu and here's my first question :grin: 

how can i permanently shutdown the x server for installing the nvidia drivers from the nvidia hp?

thx& greez :)

---

### Post by J-Gaming on 2006-06-09
Check here:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by steve.horsley on 2006-06-09
Don't install drivers from the nvidia web site. Install the ones in the Ububtu repositories. It's easier. 

[http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28NVIDIA.29](http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by Klaidas on 2006-06-09
> how can i permanently shutdown the x server for installing the nvidia drivers from the nvidia hp?

Try ```
sudo /etc/init.d/gdm stop
``` :)

---

