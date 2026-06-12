---
title: "Help~~ Macbook Pro 4,1 no backlight control"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by ahdar on 2008-05-28
LCD backlight, keyboard illumination and ambion light sensor don't work under ubuntu 8.04. 
Neither system power manager nor pommed could handle it. (pommed did work for sound though...)

---

### Post by _alex_ on 2008-05-28
You need to use the Fn key fix as detailed here:

[https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

However, even then keyboard illumination will not currently wrok AFAIK.

---

### Post by ahdar on 2008-05-28
The Fn key had been fixed. So pommed worked for sound control (F8/F10-12)... But F1/F2 still got no responses :(

---

### Post by _alex_ on 2008-05-28
Are you running pommed 1.16+? To check, execute "pommed -v" at the shell. If not, you need to add the mactel support ppa to your source list, see:
[https://launchpad.net/~mactel-support/+archive](https://launchpad.net/~mactel-support/+archive)

---

### Post by ahdar on 2008-05-28
fixed it! Thanks a lot!! 
turns out 1.16 hasn't got to the repository
hope a solution to keyboard/sensor comes up soon~

---

