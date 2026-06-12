---
title: "Help!!!!....Can't log into Desktop!"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-18
Hi, I recentley tried to install Compiz but when I added it so it would start up as soon as Ubuntu login....It just goes into a screen that looks like when you have bad reception on a TV...(lol) hard to explain...So I was wondering if I can log in to the console and remove it from the start up menue

Thnaks

---

### Post by aysiu on 2006-07-18
Try pressing Control-Alt-F1, logging in and then ```
sudo aptitude remove compiz
sudo dpkg-reconfigure xserver-xorg
``` Then Control-Alt-F7 and Control-Alt-Backspace

---

