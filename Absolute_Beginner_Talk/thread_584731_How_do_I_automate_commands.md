---
title: "How do I automate commands?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by kenweill on 2007-10-21
How do I automate commands?

Everytime I start my Ubuntu computer(gateway), I always have to type these commands in order:

sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT

sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

sudo iptables -A POSTROUTING -t nat -j MASQUERADE

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"


I have to type all these 4 commands in order for my other computers to connect to the internet. My Ubuntu machine is the one sharing the internet connection.

But how do I automate those commands? So that I don't have to type all those commands everytime I start my computer. Is there a way to do that?

I want to share my internet connection even when my computer is just turned on, and not logged-in in the GUI. Just turn on the computer and internet connection is shared. No need to log-in in the GNOME.

Can this be done? How?

---

### Post by aktiwers on 2007-10-21
You can add them to startup. 
[http://ubuntuforums.org/showthread.php?t=353643](http://ubuntuforums.org/showthread.php?t=353643)

read a little down that thread. :)

---

### Post by kenweill on 2007-10-21
Thanx.. I'll try to read that.. I hope its just an easy steps.

---

### Post by kenweill on 2007-10-21
It works.
I inserted all those commands in /etc/rc.local

Thanx alot.

Cheers.

---

