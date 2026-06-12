---
title: "mail relay on ubuntu server"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by angelofarina on 2007-12-01
Hi guys, this is my first post here, I started using Ubunto just past monday. Very easy and fast learning curve :), I have to say...
In three days I managed to install two Ubuntu Desktop 7.10 machines (laptop and desktop) and one Ubuntu Server 7.10, configuring the latter for multiple IP support (it responds to the addresses 160.78.24.2, 4, 13,14,15,16,17). Each IP address has got its own web server. The problems are with the E-mail server....
Here are my problems, for which I kindly ask for advice (after spendiing two days browsing this forum and googling around on the net):
1) I want to have a separate list of users for each of the different IP numbers (and corresponding network domains)
2) I want to to be able to allow selected users to relay mail through the server, wherever they are....
I suppose that the first is just matter of editing some .conf file (which one?), for the second I did find some guidance on the forums, but always referring to the usage of SSL protocols or the like, which require to employ "strange" TCP ports on the firewall. 
As this machine is in the University Campus, I have no control on the firewall, nor I am allowed to ask to open "not standard" ports.... So I need to manage the user authentication without usage of "strange" secure protocols and the related (unavailable) ports...
Any hints about how to configure my mail server?
Thanks!
Bye!

Angelo Farina
[HTTP://www.angelofarina.it](HTTP://www.angelofarina.it)

---

### Post by irish_flu on 2007-12-01
What software are you using to serve mail (sendmail, postfix, etc)?

---

### Post by angelofarina on 2007-12-02
Uh, I am using the one already integrated in Ubuntu server, I did not install any additional package...
From what I can see, it appears to be Postfix as the general mail server, and Dovecot is used for Pop3/Imap access.
It's Ubuntu server 7.10 Gutsy Gibbon, it should be the latest stable release. I would avoid, if possible, to install anything which is not already pre-installed, as I was told that this Ubuntu Server package does already contain EVERYTHING needed for running a web/mail server.....
I am sure that the system CAN relay mail, it is just some setting hidden in some .CONF file prohibiting this for "security" reasons.....
I managed easily to configure the system for remote DOWNLOAD of Email messages, but I cannot SEND messages through my server.... Whatever I do, I always get an error related to "unathorized mail relay"...
If anyone knows the hint for unlocking mail relay (of course, for authorized users only), I will be grateful....
However, please do not give suggestions if you do not have experience with the same system. It is of no value for me to say "please install this other Email package, which I am using happily"...
I want to configure my standard Ubuntu server package, not to start hybridizing it with other flavours of Linux.... 
All other settings were easy and straightforward, both for Web and Email services, I am really coming crazy about this difficulty configuring the mail-relay service. 
It looks to me that it should be one of the most basic and important functions of a mail server, it appears impossible that Ubuntu server is released WITHOUT a simple-to-configure mail-relay service...

Thanks
Bye!

Angelo Farina

---

### Post by irish_flu on 2007-12-02
Cool, postfix is very widely used.  If I were you, I'd look at the Postfix documentation (as far as I know, the Ubuntu devs have not customized it).

---

