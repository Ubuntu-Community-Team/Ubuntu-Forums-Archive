---
title: "More Wireless Issues DV6636NR"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Syuivil on 2008-02-26
I am following Dark_Stags Guide to install,

Video Card works fine

Installed ndiswrapper
I extracted the wireless drivers to my desktop in a folder called wifi,

I then open terminal and <<CD /home/XXXXX/Desktop/wifi>>
then <<sudo ndiswrapper -i bcmwl5.inf>>
Says it is already installed
Then <<sudo Ndiswrapper -m>>

Blacklist and Modules editing has already been done

I restart and no luck...

What am I doing wrong? Any help appreciated

(This is my first install)

---

### Post by jan quark on 2008-02-26
what is your wlan card 

please run
```
lspci
```

if it is a broadcom, the ndiswrapper method did not work me either

try this instead
[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

---

