---
title: "How do I set up DHCP?"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by Chucky G on 2006-05-10
I thought I had set it up properly, and Ubuntu says it sees my ethernet connection.

But it is not letting me connect to the internet. :( 

Does anyone have a step by step tutorial of how to set up DHCP?  Maybe I am missing something?  ](*,)

---

### Post by ProjectGod on 2006-05-10
the most likely solution i found with NOT being able to connect to the internet with a DSL connection... is the setting for DNS server. check your ISP's DNS server address... insert it into ubuntu... under System -> Administration -> Networking... then select the DNS tab and pop in the IP address of the ISP's DNS server..

hope this works out.

---

### Post by Chucky G on 2006-05-10
I should have mentioned I use a cable modem, and use a linksys router to share the connection.

I think I'll try the ISP's DNS address suggestion.  Thanks!

---

### Post by ProjectGod on 2006-05-10
can you ping the router? is the router acting as the DHCP server? have you set the Ethernet card on ubuntu to "DHCP" instead of static ip? 

if you can ping the router... but keep timing out when you open firefox to browse internet... its most likely DNS problem.

---

### Post by mjm115 on 2006-05-10
OK, if Ubuntu sees your ethernet connection, then it may be the router.  When you go to a terminal (Applications>Accessories>Terminal) and type in **ifconfig**, what is your IP Address set to?  It should be something like '192.168.1.100' or something like that.  If it does, then it is a problem with the router's connection to the Internet.  If it doesn't, then DHCP is set up incorrectly on the router.  Are you able to connect to the Internet with other computers?

---

### Post by Chucky G on 2006-05-10
[QUOTE=mjm115]OK, if Ubuntu sees your ethernet connection, then it may be the router.  When you go to a terminal (Applications>Accessories>Terminal) and type in **ifconfig**, what is your IP Address set to?  It should be something like '192.168.1.100' or something like that.  If it does, then it is a problem with the router's connection to the Internet.  If it doesn't, then DHCP is set up incorrectly on the router.  Are you able to connect to the Internet with other computers?[/QUOTE]


The router appears fine.  I have another PC hooked up to it with no problems to speak of.

---

### Post by mjm115 on 2006-05-10
ok, what does 'ifconfig' tell you about the IP Address?

---

### Post by Kobalt on 2006-05-10
Have you tried setting up your connection by typing "pppoeconf" in a command line ?

---

### Post by Resurrection on 2006-05-10
Also, one thing that people often forget about......You have to enable DHCP in your router.  This means going into your router setup, usually through a web browser, and enabling DHCP.  Also make sure that you don't have any MAC address filtering or any other type of access limitations in the router settings.

---

