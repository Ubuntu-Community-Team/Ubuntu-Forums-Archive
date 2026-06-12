---
title: "Reboot and Power off buttons missing"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by elnino on 2006-07-12
After the installation of xgl in ubuntu606, the these two buttons disappeared from the power menu! When I want to reboot or shut down the PC, I have to finish my session first, and then shut it down from the login menu! ](*,) 

how can I have these buttons back?

---

### Post by bruenig on 2006-07-12
this is not really an answer as much as it is a get around, but if you go into a terminal and enter
```
sudo shutdown -h now
```
You will shutdown.
Or if you do 
```
sudo shutdown -r now
```
to reboot.

---

