---
title: "RaspberryPi as DNS server"
date: 2013-12-25
forum: Any Other OS
---

### Post by LinuxUser666 on 2013-12-25
Hello fellow Ubuntu Linux users, I am running 32-bi Ubuntu 12.10 with Xubuntu session. I have graduation work to do and its about Linux PC-s administration and monitoring LAN traffic. I've got this thing about administration down but my I have no practical how to do proper network management. My initial idea was to buy RaspberryPi and set it up as a DNS server which would restrict access to certain websites such some social networks and/or porn sites. My plead to community, since so far I found no solid solutions I would like you to please answer me to these questions:

1.How to set up RaspberryPi to use it as DNS server and what software to use? 
2.How to route all LAN traffic through RaspberryPi DNS server, if possible?
3.How to configure RaspberryPi DNS server to block certain websites by ip?

My regards, stay brutal. ):P

---

### Post by tgalati4 on 2013-12-25
I would think you would have better luck buying a better-quality router and installing [http://dd-wrt.com](http://dd-wrt.com) on it.  It has all of the network monitoring tools that you want built-in or easily installable.  A raspberrypi has only one ethernet port, so you would have to add additional ethernet boards which might cause some issues with power and speed.

---

### Post by Iowan on 2013-12-25
My network DNS/DHCP server is a P3/500 with 128M RAM (I suspect the Pi could outrun it). It has only one ethernet pot - and it runs 10MB/s. I'm about ready to let the Tomato router do these duties... the DNSMasq settings are different - Tomato doesn't seem to remember host names as well as the Ubuntu version. I also have a BeagleBone Black (running Ubuntu) that could replace the server and fit in an Altoids tin...

---

### Post by LinuxUser666 on 2014-01-06
[SIZE=2]I think I 'll try [COLOR=#000000][FONT=Verdana]Linksys WAP54G v1 router with dd-wrt and I will try it also with tomato firmware and see how it plays out, I need my own experience to judge what is better, thanks for your suggestions. I will not bug you with flashing those firmwares on router here, but I will keep the thread open so I can ask you if I stuck in that process. Is that ok, I hope it is...otherwise I will close it if I must.

Thanks again, stay brutal, my regards. [/FONT][/COLOR][/SIZE]):P

---

### Post by Bucky Ball on 2014-01-06
*Thread moved to **Other OS/Distro Support**.*

You'd have much better luck asking these questions on the Pi forums:

[http://www.raspberrypiforums.com/forums/](http://www.raspberrypiforums.com/forums/)

Also, be aware of this, from the Forum Guidelines:
> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

Best course of action:

- Buy an RPi;
- Start setting it up and learning about it;
- Start asking questions when you get stuck.

Just read your last post. Open a new thread for any further questions regarding Tomato or anything else as they will have nothing to do with this thread title and will therefore be off topic. Posting here would also decrease you chances of getting help.

You can't close the thread, I've done it for you.

*Thread Closed.*

---

