---
title: "gproftpd (GUI)"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Linux_n00b on 2007-05-21
So I inatalled proftpd the gui.  Now, every user I create goes under Anonymous.  How can I create a user that is not under anonymous in the GUI?  Also, how can I share different partitions for download/upload?  ex.  sda3.  It only allows me to care /var/ftp/ directory.  Help would be greatly appreciated :o)

---

### Post by finer recliner on 2007-05-21
real linux users dont use GUIs to manage their servers    (jk jk!)

but i really do use proftpd (with no gui). i followed this guide:
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) 
which i found very helpful and walks you through every step including how to configure the server for different users and different permissions and everything.

if you find it helps. go for it.

---

### Post by Linux_n00b on 2007-05-21
How right you are thought!  How hard is it to manage to manage command line FTP server?  Being the n00b I am, would you recommend it? or should I get used to the GUI first and then go command line?  Teach me to become the non-n00b

---

### Post by finer recliner on 2007-05-22
well if you're like me. and you dont use the server very often or some large project you can probably just do command line. configure it just once and never worry about it again.

---

### Post by Linux_n00b on 2007-05-22
Anothe quesiton about the gftpd... I put it on my work laptop which I also take home.  When I put in the IP address that I am assigned at work, it works.  If I were to put in the IP address that I am assigned at home, it does not work.  I am using the wired connected to work and using a Netgear WG511T wireless card at home. I have also noticed that if I were to goto my windows xp box and try to ping my ubuntu laptop, it come back "destination host unreachable".  How would I go about configuring gftpd so I works at both work and at home?

---

