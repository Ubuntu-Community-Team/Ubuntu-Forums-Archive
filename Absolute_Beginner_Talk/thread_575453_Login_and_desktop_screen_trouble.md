---
title: "Login and desktop screen trouble"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Ammaro on 2007-10-14
Ok so I changed my resolution to 1280x800 and then logged out and then it made half my screen black and then it made about 5 copies of the login screen and made them like 1in across and like 2in tall and there where black horizontal lines going through them so I cant see anything on it.

Is there anyway to change my resolution back to 1024x768 in like recovery mode?

---

### Post by Ferri on 2007-10-14
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Should allow you to fix this.
You may also manually edit xorg.conf.
```
sudo nano /etc/X11/xorg.conf
```
But I think it's better to give a try to the first option.

---

### Post by i-tech on 2007-10-14
hi , 
try to reconfigure your xorg
```
sudo dpkg-reconfigure xserver-xorg

```hope it works

---

