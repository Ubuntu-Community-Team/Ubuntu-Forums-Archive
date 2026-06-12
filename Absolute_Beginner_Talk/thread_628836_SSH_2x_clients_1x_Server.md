---
title: "SSH 2x clients 1x Server"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by jmknash on 2007-12-01
Hi fellas
I am wondering if you could help me to link up a router used as a client to a wireless connection (not mine) with dropbear SSH behind a firewall (not configurable) to 'phone' home to my SSH server. Then I can access the first client with my Ubuntu SSH client connected to my server. Is that possible? Thx
Jon

---

### Post by mellowd on 2007-12-01
I'm a bit confused exactly what it is you are trying to do, could you give a bit more depth?

---

### Post by Dr Small on 2007-12-01
Yes, I really didn't understand what you are trying to do.

---

### Post by jmknash on 2007-12-01
Hot damn a fast reply. Okay, I will try to explain.

Client 1 > SSH Server < Client 2.

I have a hardware router (Client 1) which has been 'modified' to run linux and that is
connected to an internet connection which is not mine and it's is behind a 
firewall too.

I cannot connect to it because of the firewall but was hoping to make a script
on it to automatically connect to my SSH server on a linux box through the internet to my
internet connect as a SSH client.

I then connect to my SSH server which is the 'middle' man using Client 2, my SSH server is within my LAN.

I wish to access Client 1 (router) via Client 2 (pc)

Does that help you to understand??

Jon

---

### Post by mellowd on 2007-12-01
I see what you mean. You can creapte a script to automatically get client 1 to connect via ssh.

You could also ask that they forward a port for you or open access for you some other way?

---

### Post by jmknash on 2007-12-01
mellowd, how would I make it open access please?
Can you estimate on bandwidth for keeping the connection open, it may need keep-alive tho or set up as a cron task to
schedule at specific times..

---

### Post by mellowd on 2007-12-01
I'm not going to be able to help that much unfortunately. 

I'm not sure on the exact bandwidth required to keep a SSH tunnel open, but it shouldn't be too much.

Secondly, I've never actually SSH'd into a device that was SSH'd into another server. It might be possible but I've never actually done it that way.

---

### Post by Dr Small on 2007-12-01
It is possible to ssh into one server, and from that server ssh into another one, but I don't think it is possible to ssh into server1 and connect to the ssh session that server1 is connected to server2.

---

### Post by Seq on 2007-12-01
There is a good writeup of how to do this on the gentoo Wiki. It's called a [reverse tunnel]("http://gentoo-wiki.com/TIP_SSH_Reverse_Tunnel").

Using something like that combined with autossh on your client's machine should work.

---

### Post by Dr Small on 2007-12-01
> **Seq said:**
> There is a good writeup of how to do this on the gentoo Wiki. It's called a [reverse tunnel]("http://gentoo-wiki.com/TIP_SSH_Reverse_Tunnel").

Using something like that combined with autossh on your client's machine should work.
Oh, well that is similar to this then:
[http://php.8ez.com/drsmall/blog/wp-content/bypassfirewall_sshtunnel.png](http://php.8ez.com/drsmall/blog/wp-content/bypassfirewall_sshtunnel.png)

---

### Post by mellowd on 2007-12-01
> **Dr Small said:**
> Oh, well that is similar to this then:
[http://php.8ez.com/drsmall/blog/wp-content/bypassfirewall_sshtunnel.png](http://php.8ez.com/drsmall/blog/wp-content/bypassfirewall_sshtunnel.png)

similar, but not quite the same

---

### Post by jmknash on 2007-12-01
Thanks I will read up on TIP SSH Reverse Tunnel and the picture, I think autossh is available for the box.

---

### Post by jmknash on 2007-12-02
I managed to do it, this is the line client 1 uses.

~# ssh -R 1209:192.168.10.18:22 jon@192.168.10.10
(port 10000 was not free, webmin is using that!)

After a battle of figuring out why client 2 kept getting connection refused -
no port was created I believe when it was localhost, so I replaced it to 192.168.10.18,
which is client 1's Lan/Wifi address.

192.168.10.10 is the 'middle' man. Client 2 can connect to Client 1 now via middle man tested 
in my local lan. gr8.

Now.. If client 1 is put on another internet (not mine) and 192.168.10.10 in the 
command line is replaced with my Wan internet address will this work?? 
(Obviously I will open a port forward from my wrt54g to 192.168.10.10). Jon

---

