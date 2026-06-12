---
title: "Browser HOSTS file"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Fedz on 2006-09-06
Just a quick question :)

Is the Hosts file in /etc the browsers host file for blocking unwanted ads ...etc.?

Tia

---

### Post by wiseguy on 2006-09-06
Yes it is. 

I use this host file.

[http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)

---

### Post by Fedz on 2006-09-06
Great :) Thanks for the quick reply wiseguy.

I always used hosts file on window$ (from that site) but, never gave it a 2nd thought until now when I was browsing and saw a million and one ads :rolleyes:

I should email the site and ask them to add the path in linux (Ubuntu).
Do you know is the hosts file always in /etc for linux?

Tia

---

### Post by steve.horsley on 2006-09-06
This is not what the hosts file is for. The original purpose of the hosts file is to provide a lookup from name to IP address without having to to use a DNS name server. In fact DNS was only invented when hosts files started getting un-maintainably big. 

That said, the hosts file still exists, and is consulted before a DNS server is, which means three things:

1) You can put hosts in there which are for some reason unknown to the name server.

2) You can put commonly used lookups in there to prevent so many requests to the DNS server

3) You can cause the computer to go to a different address than the one known by the name server. 

Item 3 has 3 convenient uses:

a) You can use it to prevent your browser from connecting to irritating ad servers. This is Good.

b) You can put the name of your bank etc. in there so that if phishers hack your ISP's DNS server, they can't redirect you to their fake sites. This is Good.

c) If phishers can get at the hosts file, they can redirect requests for valid URLs to any fake site they choose. This is Bad.

Yes the file is always there.

Keep a copy in your home folder. My hosts file seems to get overwritten with a clean one very regularly. I suspect it's synaptic during upgrades, but haven't proved it yet. It's very irritating.

---

### Post by Fedz on 2006-09-07
**Warning**:
Before changing your hosts file in /etc/hosts please read **[this thread](http://www.ubuntuforums.org/showthread.php?t=252876)**.

Kind regards

---

