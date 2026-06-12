---
title: "Quick Dialup Question"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Hellofriends on 2007-07-04
Hi
If I boot from the Live CD is there anyway I can check to see if Ubuntu is detecting my modem?
I have an internal hardware PCI US robotics and an external serial modem, I can  use either but they are necessary for me to use the internet. Thanks.

---

### Post by moore.bryan on 2007-07-04
*i'd suggest checking [linmodems.org]("http://www.linmodems.org/"); i had the hardest time trying to set mine up, so ditched dial-up for broadband.*

---

### Post by Hellofriends on 2007-07-04
thanks for the reply. I've checked around that site and I'm not really sure if my modem is supported or not. I guess I'll try and get gnome-ppp on a disk and install ubuntu and hope it works :(

---

### Post by moore.bryan on 2007-07-04
*what, exactly, are your modems?*

---

### Post by cebobbitt on 2007-07-04
Hi there, I also use dial-up and the way I got it to work was, I used a serial port modem(hardware modem). Mine is on ttyS0 and you can use either the networking tool that comes with Gnome or gnome-ppp. Both work well, but I mostly use gkrellm to start them up and monitor my time online. Gkrellm has a timer and a ppp status monitor. My modem is a Modem Blaster by Creative that I got at Best Buy for 60 bucks, and it has worked flawlessly. I hope this helps, good day

---

### Post by Hellofriends on 2007-07-04
> **moore.bryan said:**
> *what, exactly, are your modems?*

US robotics pci, I know it is a hardware modem, not sure about anything else.(I've had it for years.)

Serial modem..has no brand name on it, it says: model: FB WS-5614ES2A on the bottom however.

[QUOTE=cebobbitt]Hi there, I also use dial-up and the way I got it to work was, I used a serial port modem(hardware modem). Mine is on ttyS0 and you can use either the networking tool that comes with Gnome or gnome-ppp. Both work well, but I mostly use gkrellm to start them up and monitor my time online. Gkrellm has a timer and a ppp status monitor. My modem is a Modem Blaster by Creative that I got at Best Buy for 60 bucks, and it has worked flawlessly. I hope this helps, good day[/QUOTE]
This is good to know, thank you. I havn't heard of anyone using dialup on Fiesty Fawn 7.04. Very reassuring.

---

### Post by Bartender on 2007-07-04
Also, you don't need to get the Linux PC online to get gnome-ppp installed.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

### Post by Hellofriends on 2007-07-04
> **Bartender said:**
> Also, you don't need to get the Linux PC online to get gnome-ppp installed.
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

Thanks. I've downloaded Gnome-ppp and gkrellm to a flashcard. Hopefully it'll at least see my serial modem!

---

### Post by Bachstelze on 2007-07-04
> **Hellofriends said:**
> thanks for the reply. I've checked around that site and I'm not really sure if my modem is supported or not. I guess I'll try and get gnome-ppp on a disk and install ubuntu and hope it works :(

[http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)

---

