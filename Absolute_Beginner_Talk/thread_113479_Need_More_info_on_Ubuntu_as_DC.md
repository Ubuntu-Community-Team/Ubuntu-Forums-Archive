---
title: "Need More info on Ubuntu as DC"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by bendigo on 2006-01-06
I am new to Ubuntu and need to use it to basically be a domain controller. Is this possible? Basically, just for user authentication to the network and print server.
I have a small office with 6 client machines and this new Ubuntu server.

I see some of the other posts about using SAMBA. I have never used it, is it hard to install and administer?

Are there any other options?

Thanks

---

### Post by mips on 2006-01-06
[http://ubuntuforums.org/showthread.php?t=79223](http://ubuntuforums.org/showthread.php?t=79223)

Also do a search for Domain Controller in these forums

---

### Post by lunatech on 2006-01-07
[QUOTE=bendigo]I am new to Ubuntu and need to use it to basically be a domain controller. Is this possible? Basically, just for user authentication to the network and print server.
I have a small office with 6 client machines and this new Ubuntu server.

I see some of the other posts about using SAMBA. I have never used it, is it hard to install and administer?
Thanks[/QUOTE]

I had done something like this in my previous office.  It is not that hard to setup.  Check out the docs at the samba's website.  Two books (available on the site itself) that I would recomend is the Practical Exercises in Successful Samba Deployment ([http://sg.samba.org/samba/docs/man/Samba-Guide/](http://sg.samba.org/samba/docs/man/Samba-Guide/)) and the Using Samba ([http://sg.samba.org/samba/docs/using_samba/toc.html)](http://sg.samba.org/samba/docs/using_samba/toc.html)).  The 'Using Samba' is bit outdated, but it is still useful.

I took a machine out of network, installed samba on it.  I configured it as PDC.  Next I took out one windows machine and tried adding it to the domain (for which the samba was the PDC).  Once I made both of them work, I migrated the other machines to the domain.

I suggest you schedule some downtime for this and try to install things on compatiable hardware to avoid useless headaches.  Even though the whole thing is complex, the documentation is quite good.

---

### Post by bendigo on 2006-01-09
THANKS Guys! I will check out those books also Lunatech.
:razz:

---

