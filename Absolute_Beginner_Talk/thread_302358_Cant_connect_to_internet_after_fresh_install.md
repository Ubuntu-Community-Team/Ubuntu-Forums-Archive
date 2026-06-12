---
title: "Cant connect to internet after fresh install"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-18
I made a fresh install of ubuntu edgy, but i cant connect to internet. I use the ethernet connection, no wireless.
I had to type in some of the the output for "ifconfig" and "iwconfig" since i had no connection to post my text file.

ifconfig:

etho     link encape: ethernet hwaddr 00:30:48:60:ba
         inet addr: 192.168.1.101 bcost:192.168.1.255 mask 255etc
         inet6 addr: fe08::230 etc....
         UP Broadband running multihost MTU:1500 metric 1

lo       link encape: local loopback
         inet addr:127:0.0.1 Mask 255.0.0.0
         inet6 addr: ::1128 scape host etc ...
         UP loopback running MTU:16436 metric:1



Iwconfig

lo      no wireless extentions
eth0    no wireless extentions
sit0    no wireless extentions

---

### Post by kiyometane on 2006-11-18
I was getting connections before i upgraded from ubuntu6.06lts to 6.10

---

### Post by bernied on 2006-11-18
You may need to add your router as default gateway. Do you know the IP address of your router? If it were 192.168.1.1 then you could try:

route add default gw 192.168.1.1

---

### Post by kiyometane on 2006-11-18
How do i do that?

---

### Post by bernied on 2006-11-18
You need a terminal. See this excellent piece by aysiu:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

And welcome to linux.

Also, follow this thread:
[http://www.ubuntuforums.org/showthread.php?t=302232](http://www.ubuntuforums.org/showthread.php?t=302232)

---

### Post by kiyometane on 2006-11-18
I get "operation not permited" erron when trying to enter the command.

---

### Post by bernied on 2006-11-18
Ok, sorry about that, you need to be the 'root' user. To get root permissions, use the 'sudo' command, so:
sudo route add default gw 192.168.1.1

You will be asked for your password.

---

### Post by kiyometane on 2006-11-18
I get "file exist" when i type the command under sudo
But it does not solve my connectivity issues

---

### Post by kiyometane on 2006-11-18
For some reasons the internet is working now and i dont know how that happened.
hopefully it wont happen again

---

### Post by bernied on 2006-11-18
I hope so too

---

