---
title: "Ok. Now I REALLY NEED HELP!!!!"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by bobnewmn on 2007-09-29
Ok...like I've said before, I want to bridge internet with my Xbox 360 using linux. How do I do this? How do I get a program that lets me do this, and if it is firestarter, please don't give me a manual. The one somebody gave me in my last thread was useless since it was a munual on the older version of FS.

---

### Post by bobnewmn on 2007-09-29
Please anybody?

---

### Post by Hossie on 2007-09-29
If NAT is enough for you, I use that:

```
#!/bin/sh
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
ifconfig eth1 up
sleep 2
ifconfig eth1 inet "192.168.199.1/24" 2>/dev/null
ifconfig eth1 inet "192.168.199.1/24" 2>/dev/null
```

Then you can plug the Xbox in eth1 and assign an address 192.168.199.x. Use .1 as gateway and your router as DNS.

Hope that helps.

&#8364;:: This is not for Ubuntu, though, use sudo or sudo su to execute it.

---

### Post by bobnewmn on 2007-09-30
Thanks! But the 2nd, 3rd, and 4th command do not work. I do execute them with sudo or sudo su. It says "Permission Denied". Also, do I set the DNS AND Gateway to that IP, or just one of them. And I am wireless, like I said. I am using wlan0 for wireless. How do I put the eth1 on my 360?

---

### Post by meborc on 2007-09-30
if it says permission denied, you need root permissions... that means use 'sudo' in front of the command

also, if i'm not mistaken... the code in the post is given to be a script... not to insert the lines manually... although it should work either way

---

### Post by bobnewmn on 2007-09-30
Ok. So this is what I do. I type in "sudo" in the terminal. I set my gateway adress on my xbox 360 to 192.168.199.1 My router is DNS. I run a test, the Network adapter is wired, but the IP still fails. I also have tried using sudo su to execute this.

---

### Post by bobnewmn on 2007-09-30
(just bumping this back up-don't want this thread to get buried)

---

