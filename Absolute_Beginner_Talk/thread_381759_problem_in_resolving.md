---
title: "problem in resolving"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2007-03-11
I am testing a two machines LAN with a view to share the internet connection. Both of the machines are using Dapper.

From the client machine (where no direct internet connection) if I type
```
ping 216.239.59.103
```
it is working fine and pinging the host (which is [www.google.com](www.google.com) in the above example).

But if I ping [www.google.com](www.google.com)
```
ping www.google.com
```
it cannot ping the host.

I can understand it is a problem in resolving the name. My question is how to solve this problem and exactly what I have to type in resolv.conf ?

---

### Post by chewearn on 2007-03-11
```
nameserver xxx.xxx.xxx.xxx
```

where xxx.xxx.xxx.xxx is the IP address of your DNS server.  Example:

```
nameserver 192.168.1.1
```

---

### Post by Linux Lover on 2007-03-11
Thank you for your reply.

I have tried editing my client machines /etc/resolv.conf with

nameserver 192.168.1.1

But it did not work.

Also, tried 

search 192.168.1.1

it too did not work. In both of the case I can ping to outside world using ip-addresses but cannot ping the hostnames of those ip-addresses.

---

### Post by jkeyes0 on 2007-03-11
Are you going through a router? If so, what is the IP address of that router?

For a quick fix, try changing the nameserver to 4.2.2.2. I'm not sure offhand who that one belongs to, but it's one my old ISP told me to test with.

---

### Post by lloyd_b on 2007-03-11
"192.168.1.1" was just an example.  Look in the "/etc/resolv.conf" file on the *server* machine, and see what it's entry for "nameserver" is.  Then copy that "nameserver" line to the "/etc/resolv.conf" of the client machine.

Lloyd B.

---

### Post by Linux Lover on 2007-03-11
> **lloyd_b said:**
> "192.168.1.1" was just an example.  Look in the "/etc/resolv.conf" file on the *server* machine, and see what it's entry for "nameserver" is.  Then copy that "nameserver" line to the "/etc/resolv.conf" of the client machine.

Lloyd B.

In case of my server machine, the internet connection is not a static connection. The IP address is assigned by my ISP dynamically. So, I am addressing my client machine's resolv.conf to the 2nd NIC of my server machine. 1st NIC of my server is connected with the internet.

---

### Post by Linux Lover on 2007-03-11
> **jkeyes0 said:**
> Are you going through a router? If so, what is the IP address of that router?

For a quick fix, try changing the nameserver to 4.2.2.2. I'm not sure offhand who that one belongs to, but it's one my old ISP told me to test with.

I am not going through a router. It is just a direct connection with two machines using crossover cable.

4.2.2.2 trick did not work for me. :-(

If I put the ip address in the browser's address box, it is opening the page, but cannot resolv the name.

Checked /etc/hosts and /etc/resolv.conf at my client machine again

/etc/hosts contains the ip-address of my server and the alias

/etc/resolv.conf also contain the proper entry in `nameserver   ipaddress.of.my.server` format

Please tell me what to do.

---

### Post by Linux Lover on 2007-03-11
> **lloyd_b said:**
> copy that "nameserver" line to the "/etc/resolv.conf" of the client machine.
Lloyd B.

What a fool I am ......... simply overlooked the above part. Actually I think I was somehow biased in my own thought and it was not working. A fresh sleep overnight make me fresh and after getting up, I again looked at your thread and understand, what you have told.


and ... wow .. it rocks.


Thank you my friend. Thank you for helping me.

---

