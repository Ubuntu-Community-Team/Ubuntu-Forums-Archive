---
title: "More newbie questions: program startup, FTPD"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by boga on 2007-02-22
1. I've figured out that each time I start ANY program (be it calculator or gedit or anything, NOT only ones that really access the network) the system sends a DNS IPv6 query for my host name to my DNS server. This causes a real slowdown if the network is down. How can I get rid of it?
2. I need to share some files on my JFS volume by FTP to several users (different set for different user). As far as I understand the whole JFS partition has only one owner and one set of permissions. So I need a quite simple FTP server that has its own set of users/access rights rather than rely on Linux, OTOH I don't want to install MySQL for user database. Does such a server exist?
3. It seems that many programs don't recognize numpad arrows as arrows and none recognizes Shift+numpad arrows. But I've got used to those arrows since PC XT times. Is there any solution except learing to use non-numpad arrows?

---

### Post by xyz on 2007-02-22
[About IPv6]("http://ubuntuforums.org/showthread.php?t=87798")
Try and not ask tooo many questions in the same thread. Among other things, it makes it difficult for others with the same problem to get answers/help. The thread's title should reflect your question/problem. Thanks for your understanding.

---

### Post by capdog on 2007-02-22
1. You can easily disable the IPV6, there are loads of posts here on the forums. Do a search, I saw them last when looking for resolution to slow network access. 

2. ProFTP? My advice would be to search in synaptic for "FTP", then see what servers are installable. Go through each one, looking at it's homepage. I'm sure there are many servers that don't require MYSQL as a database! The settings are stored in flat text files. I don't see why they'd need MYSQL.

3. No idea! :)

---

### Post by boga on 2007-02-22
1. No luck with disabling ipv6. Well, ipv6 seems to be disabled so now it sends conventional ipv4 DNS queries. E.g. that's what happends when I start the calculator:
No.     Time        Source                Destination           Protocol Info
      1 0.000000    82.138.25.185         82.138.20.130         DNS      Standard query AAAA boga.ttk.ru
      2 0.000565    82.138.20.130         82.138.25.185         DNS      Standard query response
and later when I terminate it:
      3 0.004970    82.138.25.185         82.138.20.130         DNS      Standard query A boga.ttk.ru
      4 0.005530    82.138.20.130         82.138.25.185         DNS      Standard query response A 82.138.25.185

2. Thank you, I'll look at ProFTP closely if it suites my needs.

---

### Post by boga on 2007-02-23
One update: my host is listed in /etc/hosts:
82.138.25.185 boga.ttk.ru
yet it doesn't prevent from accessing DNS server to resolv my hostname neither in this case nor when I excplcitly try "host boga.ttk.ru"
What's going wrong?

---

### Post by boga on 2007-03-19
The problem wa solved by changing the line for my host in /etc/hosts to:
82.138.25.185 boga.ttk.ru boga

---

