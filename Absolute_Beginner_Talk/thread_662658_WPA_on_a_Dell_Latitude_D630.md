---
title: "WPA on a Dell Latitude D630"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by alecwh on 2008-01-09
Hello,

I have a Dell Latitude D630, running Ubuntu Gusty. Everything is working great, except for one (important) issue.

I can't get my laptop to get an IP from any WPA-encrypted network. My computer can recognize the network, and it *tries* to connect, but it can't. The problem has been consistent with two WPA locations. I have a few buddies with Vista and Mac PCs that can connect fine, so it's definitely a problem with my computer.

Can someone help me find, and solve this problem?

---

### Post by stump138 on 2008-01-09
first thing to try is turning off "roaming" mode. It seems to cause alot of grief for people.  The other thing to try if you can "see" the networks, but not connect is to try a static ip address and see if that works.

can you post the contents of
```
sudo iwconfig -l
```
please

---

### Post by Pevichaey5 on 2008-01-09
do you ever get the prompt for the wpa key required to get an ip address?

---

### Post by alecwh on 2008-01-09
```
alecwh@alecwh-laptop:~$ sudo iwconfig -l
-l        No such device

alecwh@alecwh-laptop:~$ 



```

I've tried both of your suggestions; I've turned roaming mode off, and, static IP addresses. Neither works. It doesn't ask for a password. I can take a video/picture when I get to the network, and post back if that's necessary.

P.S.: Sorry for the low response, my internet is killing me!

---

