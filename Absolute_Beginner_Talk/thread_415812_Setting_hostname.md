---
title: "Setting hostname?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by puffyfluff on 2007-04-20
I'm trying to set up LAMP on an internal network in a large organisation where there already are specified nameservers, gateways and so on. So, the server IP is static (193.224.xx.xx) and connects to their nameservers and gets assigned hostname from them. This means of course that my server becomes fd5727516.theirdomain.com. Not very useful in my opinion...Are there any guides on how I can still be in the same subnet 255.255.240.xx but have a different name on the machine, like myserver.mydomain.com? The purpose of the server is so that internal users can connect to http and it would make my life easier if they didn't have to remember fd5727516.theirdomain.com.
Go easy on me if this is a stupid question, I'm going on my 1:st week as Ubuntu commandline user (don't have GUI on server), never used Linux before but still got the whole she-bang up and running...well...almost ;)

---

### Post by tbg58 on 2007-04-21
just typing
sudo /bin/hostname newhostname.mydomain.com
will set a host name.
If you have the GUI installed you can set it under System, Administration, Network Settings, General tab.
Hope this helps!

More info here:
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)
Good luck!
-Rob

---

### Post by chalex on 2007-04-21
Under Debian/Ubuntu, the hostname is stored in the file /etc/hostname  There is also an entry in /etc/hosts

it is a good idea to reboot after changing the hostname.  it is one of the few times that a Linux system needs to be rebooted.

---

### Post by puffyfluff on 2007-04-21
I read the article you posted and I would hope that it would be as straight forward as this. I cannot connect to the server through SSH from home (for some reason). Works only when I'm within the office, but that's another issue I need to wrap my head around soon ;)
Thnx Rob, hope this helps, I'll give it a try on Monday when I'm back in the office.

---

