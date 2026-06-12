---
title: "Turn My Computer Into An FTP Server?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2008-02-18
Is this possible?  If so, how?  I already have and use Ubuntu 7.10, I don't have another computer to use Server Edition on, but I'd like to have control over my FTP files...

---

### Post by infoseeker on 2008-02-18
I use 'vsftp' with no problems.

---

### Post by Niklas Schröder on 2008-02-18
Awesome.  I installed it from the repositories and am reading through the man pages and such.  Any tips on how to get started?

---

### Post by ruy_lopez on 2008-02-18
See this:

[https://help.ubuntu.com/7.10/server/C/ftp-server.html]("https://help.ubuntu.com/7.10/server/C/ftp-server.html")

If you want access from an external system, you'll have to set up a dynamic hostname, and enable port forwarding on your router.

---

### Post by Niklas Schröder on 2008-02-18
Any suggestions as to the dynamic hostname?  I've been doing searches of that nature all day and am kind of sick of it...

---

### Post by gerod on 2008-02-18
You dont need the server ubuntu version. U only need to install and configure a FTP server package like proftp or vsftp or something else. I think there is a gui to config it gproftp.

---

### Post by zekopeko on 2008-02-18
> **Niklas Schröder said:**
> Any suggestions as to the dynamic hostname?  I've been doing searches of that nature all day and am kind of sick of it...

[https://www.dyndns.com/](https://www.dyndns.com/)

or

[www.no-ip.com](www.no-ip.com)

i think you can set that on the router if you have a decent one, or directly on the computer. i think that the package for one of the above is in the repos

---

### Post by Niklas Schröder on 2008-02-18
I've been looking at those all day.  They're supposed to be free.  Are they?

---

### Post by Niklas Schröder on 2008-02-18
At infoseeker:

What does your /etc/vsftpd.conf look like?  Did you edit it at all?

---

