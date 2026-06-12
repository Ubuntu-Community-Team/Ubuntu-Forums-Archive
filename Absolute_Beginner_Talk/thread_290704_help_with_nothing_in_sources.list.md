---
title: "help with nothing in sources.list"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by robyholmes on 2006-11-01
hi i am new to linux but have played with it a bit. i have just installed the new Ubuntu on my PC with windows. it installed ok but when i come to install Nvidia drivers berta drivers using your how to-beryl (i think) the first thing it ask is to enable repos? so i go to terminal and type in sudo nano /ect/apt/sources.list and there is nothing in it? nothing! :(  so i can't complete this step?

it keeps crashing too, just lockes up and can't click on out? :confused:  the mouse still can be moved? :-k 

i hope u can help. i just getting help off a friend so please explain and give codes. that is if you can help. :) 

thanks a lot

---

### Post by aysiu on 2006-11-01
Try ```
/etc/apt/sources.list
``` instead of ```
/ect/apt/sources.list
```

---

### Post by raqball on 2006-11-01
> **robyholmes said:**
> hi i am new to linux but have played with it a bit. i have just installed the new Ubuntu on my PC with windows. it installed ok but when i come to install Nvidia drivers berta drivers using your how to-beryl (i think) the first thing it ask is to enable repos? so i go to terminal and type in sudo nano /ect/apt/sources.list and there is nothing in it? nothing! :(  so i can't complete this step?

it keeps crashing too, just lockes up and can't click on out? :confused:  the mouse still can be moved? :-k 

i hope u can help. i just getting help off a friend so please explain and give codes. that is if you can help. :) 

thanks a lot

Edit: see above :)

---

### Post by igknighted on 2006-11-01
Also, if you are new try
```
gksudo gedit /etc/apt/sources.lst
```
the terminal text editors can be trick until you get the hang of it

---

### Post by robyholmes on 2006-11-01
yer sorry that is wat i typed in. it comes up with the box and short cuts at bottom but nothing in the middle. no writing just couser?

---

### Post by Beaucephus on 2006-11-01
I think he means you got the file path wrong.  Nano will show a blank file if you misspell the name.

---

### Post by robyholmes on 2006-11-01
ok thanks doesn't slove the problem of locking up all the time?

---

### Post by aysiu on 2006-11-01
> **robyholmes said:**
> ok thanks doesn't slove the problem of locking up all the time?
Try not using Beryl, which I think is Alpha software (possibly Beta).

---

### Post by Beaucephus on 2006-11-01
I think he is experiencing the sources.list problem during the installation of beryl.

If your having stability issues before installing beryl you need to sort those out first.  Eyecandy is a lesser priority.

---

