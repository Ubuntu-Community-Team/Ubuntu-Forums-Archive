---
title: "[SOLVED] No internet conection. Please help!"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-08
Just installed Ubuntustudio 7.10 but cant get it to connect to Internet. I've tried everything.

I'm using a wired connection so it's supposed to be automatically configured.

I've checked and rechecked everything and the only difference between Windows XP and Ubuntu is the broadcast gateway which in Windows is 192.168.1.1 and in Ubuntu is 192.168.1.255

I'm trying to look for a way to change the broadcast gateway but there seems to be none.

The help file asks me to check the DNS servers and gives an address which I have to ping (something like 82.1.211.85....... or something like that) and then look for some value and check if it's 100%. In my case it's 0%!

However, if I try a ping at ubuntu.com I do get an answer.

What's wrong?

I have already checked Wake-on-lan on Windows.

---

### Post by wormser on 2007-12-08
From what you are stating it looks like the gateway is the issue.  It is strange that it is giving you a different gateway.  You can set a static ip and put in the correct gateway.  I have not checked out Ubuntustudio yet but these directions should help.

Left click on the network icon near the clock> Manual Configuration> Wired Connection> Properties button> uncheck Enable roaming mode> Configuration: Static and put in the same subnet mask and gateway you get when booting into windows.  The ip address you should probably change the last number to be out of the dhcp range.

---

### Post by agerfe on 2007-12-08
Problem is there is no network icon! Ubuntustudio has no clock icon either! Is there any other way of accessing it?

I've tried Network in System>Administration>Network. Is this the same app?

Anyway,  there is no way to change the gateway! :confused:

Wjy is is necessary to be out of the dhcp? :confused:

---

### Post by wormser on 2007-12-08
> **agerfe said:**
> Problem is there is no network icon! Ubuntustudio has no clock icon either! Is there any other way of accessing it?

I've tried Network in System>Administration>Network. Is this the same app?

Anyway,  there is no way to change the gateway! :confused:

Wjy is is necessary to be out of the dhcp? :confused:

Yes, it is the same app in Ubuntu.  It is not necessary to be out of dhcp.  You could try getting dhcp to give you another ip.

```
sudo dhclient
```

If that is still not working then check out this [blog]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html") for configuring network connections.

---

### Post by agerfe on 2007-12-08
Unfortunately I can't try that right now. Ubuntu has developed a major problem. It's amazingly slow! :confused:

I have another thread posted about this: [http://ubuntuforums.org/showthread.php?t=634749]("http://ubuntuforums.org/showthread.php?t=634749")

Still can't figure out what's wrong. Everything was ok a few hours ago. Now opening an app such as Network can take as long as 5 min.

Have to figure out this first before I can begin to work on the connection problem.

---

### Post by agerfe on 2007-12-09
At last!
I did a little research and found a way to disable ipv6 on Firefox.
If anyone has the same issue and reads this thread this is what worked for me:

1.Open Firefox and type > about:configin the address bar.
2. Where it says Filter type > ipv6
3. Change > network.dns.disableIPV6 to true by double clicking where it says false
4. Quit Firefox and launch it again.The problem should be fixed.

Thanks to everyone who answered my post for taking some time in trying to help me. :)

---

