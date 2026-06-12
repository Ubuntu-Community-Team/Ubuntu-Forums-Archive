---
title: "Disable Firewall"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by d4rk on 2006-08-14
Does Ubuntu run with firewall if else is not ben set ?
If so, how do I turn off the firewall ?
Is the need for a firewall bigger when using Linux, or smaller compared with Window$ ?

Thx for answers!

---

### Post by earobinson on 2006-08-14
as I understand it ubuntu installs without a firewall, need for a firewall really depends, if you use a router to conect to the internet chances are that has a built in firewall.

---

### Post by d4rk on 2006-08-14
Then I believe my routher has FW, since Azureus keeps asking about it.
The problem is that Azureus opens a notification box that tells me that my FW is blocking something. The problem is that the notification box is a pure bug, when I press the Hide button, nothing happens :(

---

### Post by earobinson on 2006-08-14
could you post the msg, also try gnome-btdownload and see if you get an error

---

### Post by davebgimp on 2006-08-14
> **d4rk said:**
> Then I believe my routher has FW, since Azureus keeps asking about it.
The problem is that Azureus opens a notification box that tells me that my FW is blocking something. The problem is that the notification box is a pure bug, when I press the Hide button, nothing happens :(

You need to port-forward the ports that Azureus uses on your router. 

For the stuck error messages. In Azureus, go to **Help>About**. With that up, you should now be able to click those error messages and make them disappear.

---

### Post by d4rk on 2006-08-14
> **davebgimp said:**
> You need to port-forward the ports that Azureus uses on your router. 

For the stuck error messages. In Azureus, go to **Help>About**. With that up, you should now be able to click those error messages and make them disappear.


Ok, thx I'll try that !
The ports are already open, so I don't believe that's a problem.

---

### Post by earobinson on 2006-08-14
do other bt programs work?

---

### Post by PriceChild on 2006-08-14
As i understand it, the linux kernel itself is basically a firewall.

Firestarter is basically a gui for changing the "iptables" to change this firewall.

Personally, I use a hardware firewall as well as firestarter to secure myself.

Pricey

btw i have the same bug with the Azureus popups :(

---

### Post by earobinson on 2006-08-14
i guess the kernel could be seen as a firewall

---

### Post by d4rk on 2006-08-14
> **earobinson said:**
> do other bt programs work?



Azureus does work, it just tells me that a firewall is blocking some features.

---

### Post by steve.horsley on 2006-08-14
iptables is the inbuilt firewall s/w. But by default it doesn't filter anything. And you normally use a front-end GUI like firestarter or guarddog to configure it. You can tell what iptables is filtering with this command:
**sudo iptables -L**
An un-filtered box will look like this:
> steve@StevesPC:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


---

