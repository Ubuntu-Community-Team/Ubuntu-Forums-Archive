---
title: "How to create a domain in my system"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Abhi Kalyan on 2006-11-13
Hi,
Need to know how to have a domain name on my system, LDAP needs this and i havnt got a clue.

I suppose it is fairly simple.
My hostname is viki.
But i ahvnt got a doamin name?

Hopig some one can point me in the right direction.
Thank you
Sincerely
Abhi Kalyan

---

### Post by darrenm on 2006-11-13
edit /etc/hostname and put your FQDN in (hostname.domain) there.
then edit /etc/hosts and put it against your ip address in the following format eg.
192.168.0.1 hostname.domain hostname

edit - if you dont have a domain name for your network then just just localdomain if you are on a private subnet (192.168. 172. and 10.)

---

### Post by podunk on 2006-11-13
You mentioned Samba in your other post - if you're trying to connect to a windows network you will need to use the  same domain on your Linux computer as you do the windows ones.

Boot up in windows, look in Control panel> networking for that.

---

### Post by Abhi Kalyan on 2006-11-13
thank you darrenm and podunk,
this is how my current network works:
1. There is a AD server called 'x'
2. he domain name for it is 'zen.local'
3. This system has windows server2003 installed on it running DNS, DHCP, NAT through RRAS
We have 15 computers connected to this server, once we have the linux setup completely i will have 150 systems connected to this server and a couple more eventually.
And have a deadline till 10th december this year to do the whole lot.

My sole support is this forum and loads of books,
Seriously having big time deficiency with time.

I seriously thank you for the help.
Will work on this - Please do post in any links which could help.
Thank you both and all the people in this forum for all the help i had received.
Sincerely
Abhi Kalyan

---

### Post by darrenm on 2006-11-13
Just use zen.local then.

Never fear, theres nothing difficult about a Ubuntu server.

You will always get answers around here.

Good luck.

---

### Post by Abhi Kalyan on 2006-11-13
thank you darrenm

---

