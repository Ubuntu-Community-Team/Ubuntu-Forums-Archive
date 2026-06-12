---
title: "Trying to setup a LAMP server et al"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by lilalfyalien on 2006-11-04
Hi,

I'm a real newbie; I'm clueless! I've set up a LAMP server as by the instructions on this page: 
[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

I have some questions, perhaps more about networking than ubuntu...

Firstly at the end of the tutorial above it says:

[B]You need to setup manually DNS servers in resolv.conf file when you are not using DHCP.

#vi /etc/resolv.conf

You need to add look something like this

search domain.com

nameserver xxx.xxx.xxx.xxx[/B]

What does this mean- what am I supposed to put here? Am I supposed to buy a domian name and put those details here?

Secondly, how do I test that this is working? At the moment when I point my browser to my IP address it forwards me to the configuration for my home gateway/router all-in-one box. Do I need to configure a virtual server? If so on what port and does this affect setup files on my LAMP server?

How do I install files via FTP, if so how?

Another question is there any way that I can have a server with a GUI, i.e. just install the desktop version of ubuntu and have a server running off it too? 

As you probably tell I don't know alot. If anyone could explain to me or point me in the direction of a more comprehensive tutorial I would be very grateful.

Thanks in advance

Lilalfyalien

---

### Post by localuser on 2006-11-04
Wow, you are certainly a brave soul in trying to get a LAMP server working without some networking background.

See if this helps...

[http://www.cjfay.com/lamp.html](http://www.cjfay.com/lamp.html)

> How do I install files via FTP, if so how?

Actually, FTP is used to transfer files, and not exactly to install files...

[http://www.ftpplanet.com/ftpresources/basics.htm](http://www.ftpplanet.com/ftpresources/basics.htm)

> Another question is there any way that I can have a server with a GUI, i.e. just install the desktop version of ubuntu and have a server running off it too?

Ubuntu server is really nothing more than Ubuntu desktop without the graphical interface.  So yes, you can have a server with a GUI...

$ sudo aptitude install ubuntu-desktop

Or you can install the desktop version and configure Apache, MySql, and PHP on your own.

Good luck.

---

