---
title: "Can not brows"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Joy on 2006-01-01
Hi Everybody,
I am new to Linux and computer.Using Winow 98 but does not know hardware setup and configuration. I have installed Ubuntu version 5.10 from CD.I can ping my router but can not brows on Firefox.I have ADSL modem connection.
Please guide me.
Joy.

---

### Post by Masteroc on 2006-01-01
post your output of the command 

'ifconfig' without quote marks

---

### Post by cwaldbieser on 2006-01-01
[QUOTE=Joy]Hi Everybody,
I am new to Linux and computer.Using Winow 98 but does not know hardware setup and configuration. I have installed Ubuntu version 5.10 from CD.I can ping my router but can not brows on Firefox.I have ADSL modem connection.
Please guide me.
Joy.[/QUOTE]
You might want to try some of the later steps in this troubleshooter.  It sounds like you already have basic connectivity.  You probably need to set up DSN or disable IPv6.

[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")

---

### Post by Joy on 2006-01-03
Hello,

I have just installed ubuntu 5.10,. The problem i am facing is, i am able to ping sites from the terminal, and i get a reply. 
but when i start the default browser, ie, firefox, i am not able to connect.

My machine ip is 192.168.1.10, which is obtained by dhcp from my adsl router.

My machine can also resolve the dns queries, while pinging.

I also tried apt-get install firefox, but it said firefox is already installed and has a newest version

Is it possible, that there are some issues with iptables in my machine ? if so, how do i disable or modify the iptables, just to check.

Thanks

---

### Post by Joy on 2006-01-03
Hello,

I just got the problem solved as under : the solution is with the following link.

[http://www.ubuntuforums.org/showthread.php?t=111758](http://www.ubuntuforums.org/showthread.php?t=111758)

---

