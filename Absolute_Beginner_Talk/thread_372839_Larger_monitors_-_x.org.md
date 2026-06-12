---
title: "Larger monitors - x.org"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2007-02-28
Hello All

I'm currently using a no-name 17" LCD panel at 1280 by 1024 and Xubuntu 6.06.1 ('dapper'  LTS) recognised it fine with no issues (P4 IBM Netvista, Nivdia Vanta16 half height graphics card, VGA out).

I'd like to use a 1600 by 1200 20 inch LCD e.g 

[http://www.microwarehouse.co.uk/catalogue/item/ACMON183](http://www.microwarehouse.co.uk/catalogue/item/ACMON183)

Will this work OK? Do I need to manually edit the x server configuration?

Cheers

---

### Post by john.nicholls on 2007-02-28
It is quite likely that the new monitor will be detected and the necessary changes made automatically. If not, you will not have to alter the file manually. Just enter 
```
sudo dpkg-reconfigure xserver-xorg
``` in a terminal and if you are unsure about any question, accept the default.

---

