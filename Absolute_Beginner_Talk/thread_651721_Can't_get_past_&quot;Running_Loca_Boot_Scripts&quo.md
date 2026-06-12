---
title: "Can't get past &quot;Running Loca Boot Scripts&quot;"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by rbsis on 2007-12-27
Hello, I installed Ubuntu 7.10 on a Dual Core 2.2 ghz, 1 gig of RAM, ATI ASUS X1550 Series.
I installed via the text installer, but when ever I boot up it sticks there and flickers. 
Any ideas why? I run XP just fine.


-Ryan

---

### Post by PmDematagoda on 2007-12-27
You should configure the X-Server when you use the Alternate CD to install Ubuntu. When you reach the stage where the boot-up stops, which in your case is "Running Local Boot Scripts", press Ctrl+Alt+F1 to bring you to a tty. When you have logged in, execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After that is done, do:-
```
sudo /etc/init.d/gdm start
```

---

### Post by rbsis on 2007-12-27
Thanks, I will try that :)

---

### Post by rbsis on 2007-12-27
I tried that and some how I got in, but then I couldn't enable the ATI in the restricted drivers.
I got "xorg-driver-fglrx is not enabled"
When I restarted it did the same problem again...

---

