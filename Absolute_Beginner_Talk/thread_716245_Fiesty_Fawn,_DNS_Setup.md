---
title: "Fiesty Fawn, DNS Setup"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by CrazyEyesITGuy on 2008-03-05
hello again,

i've reinstalled the linux OS and set up only the DNS service package during the install.  

i've found a different site that has directions to set up box as a DNS.

question1

Once i get the box configured as a DNS is there a way to test it to make sure its doing what its supposed to do?

question 2

will i be able to use the linux DNS with a windows 2003 server set up as a domain controller using active directory?

question 3

Can anyone direct me to information on this forum or some other on how to accomplish both of these?

thanks for all the help.

p.s. this is all for a learning experience and the first time i've tried to do anything like this...???

---

### Post by Matt Cadorette on 2008-03-05
question1

A: open up a terminal and type nslookup.  You will recieve the > prompt.  Type in a web address and see if it gives a response.  Here is a example.

some@somehtingu:~$ nslookup
> [www.google.com](www.google.com)
Server:         192.168.7.45
Address:        192.168.7.45#53

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.167.104
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.167.99
Name:   [www.l.google.com](www.l.google.com)
Address: 64.233.167.147
> 

question 2

A: I'm assuming you are asking if you can use a Linux box as the DNS server for a Windows machine, and the answer is yes.  BIND can be set up as a DNS server as well as a client.

question 3

If you google BIND there is a ton of documentation on it.  Also if you really just want to get your linux server up and running you could look at webmin.  Its  a web based gui that makes setting up a lot of Linux/UNIX services easy, however you won't really learn much.  

:)

---

### Post by CrazyEyesITGuy on 2008-03-07
Hello Again,

I was directed to remove the Old DNS Settings from the .conf file that were assigned by the DHCP.  

Right now it was set to search my router first and the nameservers we're set to the IP address of the gateway.

??

I know the Nameservers should be the DNS servers for my ISP but what should i be searching first 

the code looks like this

search (router name)
nameserver (gateway IP address)
nameserver (gateway IP address) - there are both the same IP address

Question 1

Can anyone explain to me what this is doing

Question 2

would i be able to set the search in the first line to the Static IP of the linux box and then point a windows domain controler to that ip address and allow the nameservers to remain set as they are to the gateway IP address.

hope i explained that well enough.

---

