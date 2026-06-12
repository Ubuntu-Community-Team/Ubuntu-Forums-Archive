---
title: "Internet"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by banjo13 on 2007-12-09
Have installed latest ubuntu, but can't get on the internet. Ethernet from computer, to linksys wireless router, then router to internet socket. how do i get it sorted.

---

### Post by meborc on 2007-12-09
hi,

is the router set up already? should you be able to receive dynamic IP (dhcp)... if so, try```
sudo dhclient
```in the terminal...

you can check for your internet interfaces config by ```
sudo ifconfig
```if the first command does not result in connection, report back with the output in the terminal

---

### Post by banjo13 on 2007-12-09
it works using apple notebook

---

### Post by meborc on 2007-12-09
do you need to insert some username and password for internet connection? (ADSL)

or is it plug-n-surf?

did you try "sudo dhclient" in the terminal?

---

