---
title: "How to set up FTP Server"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-09-15
I am going to set up an FTP server that I basically want to be a file storage website/server where I can  store lots of my personal files from anywhere in the world. I am going to use [www.dyndyn.org](www.dyndyn.org) to get a free domain name, but I need to know the steps in order to achieve it. I have already upgraded my router with the latest firmware, and know that it can do port forwarding. I would greatly appreciate if you could walk me through the steps about how to set up an FTP server to be an online website/ server. 

Thanks 

:guitar:

---

### Post by nonewmsgs on 2007-09-15
i dont know how to, but i really want to as well, and apparantly you can't subscribe to a thread you didn't reply to.
*subscribes*

---

### Post by dwhitney67 on 2007-09-15
I just did this the other day.  Thanks to your post, it has reminded me to remove my FTP server because I no longer require it.  Anyhow, to get you going do this:

[FONT="Courier New"]$ sudo apt-get install proftpd gproftpd[/FONT]

Then run gproftpd from **System -> Administration -> GProFTPD**.

You will need to setup an account (preferably one that already exists).  You will also need to specify the IP address (or alias) of your localhost.  I've heard that 'localhost' may not achieve desirable results, thus if you know the IP address assigned to your workstation, just key that in.

Finally, you need to enable the proftpd server.  There is a button do just that in the GUI controller.  If that fails to activate the server, then you may need to comment out the 'ftp' line in /etc/inetd.conf.  Thus,

[FONT="Courier New"]$ gksudo gedit /etc/inetd.conf[/FONT]

Insert a hash-character ('#') to comment out the line containing ftp.

Follow these instructions to the letter and everything will work.

P.S.  You really should consider using SSH in lieu of FTP, or FTP with an SSH front-end.  Here's a good [article]("http://aplawrence.com/Unixart/proftpd.html") to read before you make a choice.

---

