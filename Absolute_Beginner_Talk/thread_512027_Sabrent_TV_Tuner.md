---
title: "Sabrent TV Tuner"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Acglaphotis on 2007-07-28
Is it possible to get it working? I've searched a lot but i didn't found anything. The chipset is "Trident TV Master 5600". Kdetv doesnt show anything, neither does tvtime. 

Any help would be greatly appreciated.

Thanks.

edit [This is the tuner]("http://www.sabrent.com/pics/TV-USB20-1.jpg").

---

### Post by xc3RnbFO8P on 2007-07-28
I found this : [http://www.linuxtv.org/v4lwiki/index.php/TM6000]("http://www.linuxtv.org/v4lwiki/index.php/TM6000")

---

### Post by Acglaphotis on 2007-07-28
Thanks ill try it.

---

### Post by Acglaphotis on 2007-08-02
It doesn't work. Any more ideas?

---

### Post by Acglaphotis on 2007-08-02
*bump*

---

### Post by meitnerium on 2007-08-12
You have to use saa7134 module. I do a lot of try, I<m sure for the card number, and for the tuner, it s the best result for both radio and tv :

modprobe saa7134 card=42 tuner=47.

All work weel for me, with mythtv and xawtv, using gentoo distribution. 

Some interesting web page :

[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

