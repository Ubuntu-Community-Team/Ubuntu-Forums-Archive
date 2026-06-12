---
title: "Postfix help please"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by jesrani on 2008-02-06
Hello everyone. I have been struggling to setup an email server on my Ubuntu 7.10 machine. I have read posts about Postfix config but it is just going above my head. I am giving below my requirements and I hope someone can give me detailed instructions.

1) I have setup Ubuntu desktop 7.10 on a network with 98/XP machines. WORKGROUP is "Astro". Samba is installed and running as well as Firestarter. I have a broadband internet connection on this and static IP of the machine is 192.168.0.25, subnet 255.255.255.0. Machine name is also Ubuntu.
2) There are 98/XP machines on the network with static IP's from 192.168.0.11 to 192.168.0.20 but no internet connection. Some computer names are admin( Ip 11), production (ip 12), purchase (ip 13), sales (ip 14)
3) I own a domain, say [www.abc.com](www.abc.com). It has a email id [email]info@abc.com[/email], which I can access from Evolution on my Ubuntu machine if I put the server settings  : POP3 server mail.abc.com : SMTP server mail.abc.com : username : [email]info@abc.com[/email] : password : info ; my outgoing server needs authentication. Ports are 25 and 110.
4) I want to setup the same local domain abc.com and create users like info, admin, sales, purchase, production so that the 98/XP machines can send messeges to each other using Outlook Express / Evolution, through the Ubuntu machine
5) I also want to be able to give the purchase and sales machines the ability to send mails to the internet through the Ubuntu machine but the mail should appear as being sent from [email]info@abc.com[/email] so that the replies are all received on Ubuntu machine only. If possible, any mail sent by these machines to the internet should have a copy automatically sent to [email]info@abc.com[/email] as local mail.
6) I have installed / uninstalled Postfix ; Exim but just not able to understand.
7) I have done this thing successfully before on an XP machine using MailEnable but there was a GUI and here in Ubuntu there is none. I am totally clueless.

Can anyone give me detailed steps for this please, what else do I need to install and how to configure. I have been struggling with this for the past 2 weeks. I am not able to understand the configuration at all. Please help me out.

---

### Post by jesrani on 2008-02-06
Any chance of getting help???

---

### Post by wirawan0 on 2008-02-11
I may or may not help. But is this document useful for you?

[http://www.postfix.org/SOHO_README.html](http://www.postfix.org/SOHO_README.html)

---

