---
title: "URGENT: Linux running as server help"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by sebz2005 on 2006-07-25
How do I make my Ubuntu run as a network server?
I want my Windows PC to logon to the Ubuntu server via domain.
Domain name is set to "SebZ-Server" (Without quotes).

Thanks for any help.

---

### Post by Thund3rstruck on 2006-07-25
Ah.. you need a domain controller in order to allow machines to login to a domain. If you wish for Ubuntu to be your domain controller you need to install samba.

[Samba 3 Howto]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/")

---

### Post by sebz2005 on 2006-07-25
A bit long don't you think?
This should be my reading list from now on. :p

Thanks.

---

### Post by sebz2005 on 2006-07-25
I'm stuck now.
I'm trying to run it as a WINS server, but it's talking about nmbd, witch I can't get.

---

