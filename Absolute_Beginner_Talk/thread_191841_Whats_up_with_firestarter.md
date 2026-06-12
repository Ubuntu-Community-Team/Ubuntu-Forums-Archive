---
title: "Whats up with firestarter"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-06-08
Why does firestarter block my LAN??

Ive set up the following rule but it continues to block all local ports:

Allow connections from host-
192.168.1.1-255

Allow service SAMBA(SMB) |Port137-139 445 |192.168.1.1-255
HTTP                              |Port 80             |192.168.1.1-255

---

### Post by timetunnel on 2006-06-08
Entering "192.168.1.1-255" as a range of IPs doesn't work in Firestarter. You have to enter an IP and a subnet mask in a certain way to ensure that an IP-Range is allowed.

Read the chapter "The inbound traffic policy groups" here:
[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

And here about the notation Firestarter uses:
[http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

So, if you want to allow all IPs from 192.168.1.1 to 192.168.1.255, you'll have to enter "192.168.1.1/24" in Firestarter.

Jens

---

### Post by timetunnel on 2006-06-08
Forgot to say that there's a long table at the wikipedia link I provided above. There, you can find the number of PCs ("hosts") you want in your network and then look up the right number ("CIDR") that you have to put behind the slash

Jens

---

### Post by dgrafix on 2006-06-08
Lol,

Ive no idea what any of that means
Anyone know of a normal firewall that works on ip ranges? It really is the most complicated firewall ive ever encountered.

All i want to do is basically say if the incomming traffic is from 192...1-255 allow it, otherwise block it.

---

### Post by cstudent on 2006-06-08
I have mine set up as:

192.168.1.1/255.255.255.0

and it works fine.

---

### Post by dgrafix on 2006-06-08
wont that only allow connections for the host machine to itself or am i missing something.
](*,)

---

### Post by cstudent on 2006-06-08
The way I understood it, it was similar to 192.168.1.1/24, but I couldn't get that form of entry to work. I have 5 computers on my home network and this let's each one talk to each other.

---

### Post by timetunnel on 2006-06-08
dgrafix, you're right, something like "192.168.1.1-192.168.1.255" is much easier to understand. But the way Firestarter does it is pretty simple as well (one doesn't have to understand all that, you just have to pick the right number). Like I wrote above, just go to the table at

[http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Prefix_aggregation](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#Prefix_aggregation)

Pick the number of computers in your network from the "hosts" column and then use the number given in column "CIDR" for Firestarter.

Moreover, I already gave you the value you need in my first post: Use 192.168.1.1/24 and you'll have the range from 192.168.1.1 to 192.168.1.255

---

