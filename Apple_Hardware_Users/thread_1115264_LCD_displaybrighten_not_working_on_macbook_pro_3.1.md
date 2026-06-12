---
title: "LCD display/brighten not working on macbook pro 3.1"
date: 2009-04-03
forum: Apple Hardware Users
---

### Post by Bobnox on 2009-04-03
Hello. I'm new to ubuntu, I've just installed it on a macbook pro 3.1, and for the most part it's working. I have a few issues though.

I cannot get the LCD brighten/display keys to work. I've followed this guide [https://help.ubuntu.com/community/MacBookPro3-1/Intrepid#Keyboard%20functions%20(Brightness,volume,...)]("https://help.ubuntu.com/community/MacBookPro3-1/Intrepid#Keyboard%20functions%20(Brightness,volume,...)")

applesmc, nvidia_bl and mbp_nvidia_bl modules are loaded. Can someone tell me if I'm missing something?

---

### Post by cyberdork33 on 2009-04-03
> **Bobnox said:**
> Hello. I'm new to ubuntu, I've just installed it on a macbook pro 3.1, and for the most part it's working. I have a few issues though.

I cannot get the LCD brighten/display keys to work. I've followed this guide [https://help.ubuntu.com/community/MacBookPro3-1/Intrepid#Keyboard%20functions%20(Brightness,volume,...)]("https://help.ubuntu.com/community/MacBookPro3-1/Intrepid#Keyboard%20functions%20%28Brightness,volume,...%29")

applesmc, nvidia_bl and mbp_nvidia_bl modules are loaded. Can someone tell me if I'm missing something?
do you have pommed or mouseemu installed? you should try removing them.

---

### Post by Bobnox on 2009-04-03
> **cyberdork33 said:**
> do you have pommed or mouseemu installed? you should try removing them.

Thanks. They're not installed. I removee them yesterday after some thread searching. Any other ideas?

---

### Post by m10 on 2012-02-29
you should only have nvidia_bl _OR_ mbp_nvidia_bl modules loaded. They conflict!

---

