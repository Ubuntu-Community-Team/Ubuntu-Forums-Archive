---
title: "Problem on installing Gusty on thinkpad R61"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by ChihChiehChen on 2008-02-12
Hello everyone,

Yesterday I tried to use alternate desktop CD to install ubuntu 7.10 on my thinkpad R61-A25 but some problems bothered me:

1. When I booted my notebook I could at first see the word "Ubuntu", and I type my password;after a while, I could see nothing but the black screen. 

2.I saw the error message " PCI..."( I'm sorry for not remebering all the message" ), does it mean that I have some problem about using wireless network?

3. I use PPPOE , not DHCP, to connect with outerworld, how do I complete my network setting?

Can you give me any suggestions? Thanks a lot.

---

### Post by Gen2ly on 2008-02-12
This looks to be an x server problem is the screen isn't seen.   In the login screen, type in 

> cat /var/log/Xorg.0.log | grep EE

Also look, at the xsession errors.

> nano ~/.xsession-errrors

and see if it says anyting useful.

---

### Post by oedha on 2008-02-12
sudo dpkg-reconfigure -phigh xserver-xorg
to see your network :==> sudo lshw -short -class network
and what's the result of that ?

---

### Post by jan quark on 2008-02-12
adn make sure you have not downloaded the server edition :)

---

