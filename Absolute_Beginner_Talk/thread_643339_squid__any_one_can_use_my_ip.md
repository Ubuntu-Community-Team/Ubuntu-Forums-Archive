---
title: "squid : any one can use my ip ?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by qwe010 on 2007-12-17
hi

i setup squid and it works good

but now if any one but the ip of my server in the browser

localhost 8080

he can browser the web with my ip

how can stop that ?

and if there any way to browser the web Private

without need to shell account ?

[http://www.howtoforge.com/linux_secure_browsing_squid](http://www.howtoforge.com/linux_secure_browsing_squid)

---

### Post by Severun on 2007-12-17
Google is your friend!

I did a Google search for "squid configure howto and found:

[http://www.linuxheadquarters.com/howto/networking/squid.shtml]("http://www.linuxheadquarters.com/howto/networking/squid.shtml")

Check the second paragraph under introduction.  It talks about an acl entry that will restrict access to your proxy based on individual IP or subnet.

Also as an additional bit of advice, if you have any piece of software that listens on the net, make sure you have configured your ACL's (Access Control List) for that piece of software, i.e. you don't want to start up Samba and let anyone from the Internet browse the files on your hard drive, you want to make sure the software is configured so it only allows access to the people you intend.

---

### Post by qwe010 on 2007-12-19
i did that

> /etc/rc.d/init.d/squid restart
Stopping squid: 2007/12/19 20:39:33| aclParseIpData: WARNING: Netmask masks away part of the specified IP in '192.168.1.10/255.255.255.0'
2007/12/19 20:39:33| WARNING: '192.168.1.0/255.255.255.0' is a subnetwork of '192.168.1.0/255.255.255.0'
2007/12/19 20:39:33| WARNING: because of this '192.168.1.0/255.255.255.0' is ignored to keep splay tree searching predictable
2007/12/19 20:39:33| WARNING: You should probably remove '192.168.1.0/255.255.255.0' from the ACL named 'mynetwork'
................                                           [  OK  ]
Starting squid: .                                          [  OK  ]



and i search in google many time

---

