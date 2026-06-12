---
title: "bluetooth"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by 2j4ez on 2007-12-01
Hello all still learning ubuntu,
Ive been playing with ubuntu for about 3weeks now all has been fine ive got my self a bluetooth adaptor for it plugged it in and a bluetooth icon came up near the clock 

I set the device to "VISIABLE" however i cannot find my laptop in a scan! my nokia n70 only finds my apple mac and my apple mac only finds my nokia n70 not the laptop !!

Ive installed lots of software but its still not visiable 
If i right click and select browse for device i got a box witch is just blank

Does this mean my bluetooth adaptor is not compatable or is there some settings that ive missed

---

### Post by PmDematagoda on 2007-12-01
My N73 ME works properly with my CCK bluetooth dongle. Why don't you give [Blueman]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56") a try, it could solve your problem.

---

### Post by 2j4ez on 2007-12-01
going to try it now will let you no how i get on

---

### Post by 2j4ez on 2007-12-01
How do i install it? ive spent the last hour typing text in to a terminal/web browser nothing happening!

it says to install use SUDO MAKE INSTALL where do i run that ??

---

### Post by PmDematagoda on 2007-12-01
Do in a terminal:-

1)Navigate to where the downloaded file is

Assuming that blueman-0.3 is "package":-

2)```
tar xvzf package.tar.gz

```

3)```
cd package
```

4)```
./configure
```

5)```
make
```

6)```
sudo make install
```

---

