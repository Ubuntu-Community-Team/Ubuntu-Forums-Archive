---
title: "DNS Setup"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by ClareJonsson on 2006-03-02
Hi guys,

Can anyone tell me how to set up a DNS service on Ubuntu. I may already have it but I have no idea how to go about checking etc.

Clare.

Edit:
Okay I think I have installed it, am I right in thinking it's called bind? if so, I now need to figure out how to configure it, any help appreciated.

---

### Post by ssalman on 2006-03-02
You can find your DNS configuration at:
/etc/reslove.conf

I hope this helps.

---

### Post by StefanoCole on 2006-03-02
Check if you have a file named /etc/resolv.conf
If you don't have it then create it and insert in it two lines as follows:

nameserver xx1.yy1.zz1.kk1
nameserver xx2.yy2.zz2.kk2

Where xx1.yy1.zz1.kk1 and xx2.yy2.zz2.kk2 are the server addresses (your Internet Service Provider should give them to you).

Stefano

---

### Post by Zelut on 2006-03-02
I've been curious about this as well.  I host a few sites and, so far, have stuck to using the registrars DNS.  If I could switch to my own that might be better.

Let me see if I understand this.  I would list
my.domain my.ip.address.1
my.domain my.ip.address.2

in resolv.conf and that is the basic of the DNS?

---

### Post by ClareJonsson on 2006-03-02
[QUOTE=StefanoCole]Check if you have a file named /etc/resolv.conf
If you don't have it then create it and insert in it two lines as follows:

nameserver xx1.yy1.zz1.kk1
nameserver xx2.yy2.zz2.kk2

Where xx1.yy1.zz1.kk1 and xx2.yy2.zz2.kk2 are the server addresses (your Internet Service Provider should give them to you).

Stefano[/QUOTE]

Okay but I need to have my own DNS tables so I can manage my domains on the web server. I figured out how to setup Apache for virtual domains etc. Now I need to get the DNS tables set up correctly. I have looked online for tutorials, and they tell you happily how to install and set up a basic config, but no explanation of what I edit, and what I put into the files.

I'm guessing there's a file that I can edit to add domains and point them to an IP address (Server), and add alias's (Sub Domains) to that? But I have no idea how to do this.

TTFN,
Clare.

---

