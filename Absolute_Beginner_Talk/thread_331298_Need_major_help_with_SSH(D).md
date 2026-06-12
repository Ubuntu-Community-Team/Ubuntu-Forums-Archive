---
title: "Need major help with SSH(D)"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by spyder0101 on 2007-01-04
I need help with 2 things regarding ssh(d).

1.  How do I assign my computers names instead of ip addresses to use with ssh?

2.  Why am I getting a timeout/host not found when I try to access my servers with ssh.

My network is set up like this :


Wireless Laptop (router)''''''''''''''''''''''''''''''''''''''''''''''''''''''''New Wireless Laptop
"""""""_____________|______5-way gigabit switch____________
'''''''''''|'''''''''''''''''''''''''''''''''''|''''''''''''''''''''''''''''''''''|''''''''''''''''''''''''''''''''''''''|
my.server1""""""""""""my.server2"""""""my.server3"""""""""""my.server4

The Wireless Laptop is an old windows laptop that is set to share internet connection and does nothing else.  The servers are all 5.10 Ubuntu server installs with nothing added but the "ssh" package to install ssh and sshd.  I am trying to access the servers from the New Wireless Laptop using Putty on a windows machine.

Thanks in advance for any help you can give.

Jon

---

### Post by Bachstelze on 2007-01-04
1. Either use a DNS server or - better if you have few machines - use the /etc/hosts file to store the IP - hosts.

2. There can be lots of resons, connection broken, server not running properly, bad address...

---

### Post by spyder0101 on 2007-01-04
What are some good DNS servers?

---

### Post by Bachstelze on 2007-01-04
Trust me, you don't want to use a DNS server with just five machines ;)

If you still want to fiddle with it, there's a good guide in the HOWTOs section in this forum.

---

### Post by spyder0101 on 2007-01-04
They are soon going to all be web servers, so unless I am mistaken, I will need a DNS server anyway.  Anything I can do about the timeouts?

---

### Post by scrooge_74 on 2007-01-04
is the router forwarding port 22?

---

### Post by spyder0101 on 2007-01-04
I have no idea.  How can I check?

---

### Post by scrooge_74 on 2007-01-04
Check the configuration of the router firewall maybe you have the ssh port close, or you need to configure the firewall to forward any request to that port to the desire machine. 

 I am no expert so I am not sure how to set it up to work with all the other servers. 

I have done that for a single server

---

