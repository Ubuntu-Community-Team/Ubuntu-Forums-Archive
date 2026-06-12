---
title: "DNS conguration error"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by fnkhan on 2008-03-23
I have a problem for configuring DNS 
my system IP is 190.160.0.4
and using xx.xx.xx.xx gatway e.g 190.160.0.1
first i installed bind9
#sudo apt-get install bind
then after installation completed
setting up domain resolution
sudo vi /etc/bind/named.conf
zone "abc.com" {
type master;
file "abc.com.db";
notify no;
};

zone "0.160.190.in-addr.arpa" {
type master;
notify no;
file "reverse/190.160.0";
};

after this creating a dir and file
sudo mkdir /var/cache/bind/reverse
vi /var/cache/bind reverse/190.160.0
@ IN SOA ns.br.com root.br.com
NS ns
ns A 190.160.0.3


then add reverse zone
zone"0.168.190.in-addr.arpa"{
type master;
notify no;
file "reverse/190.160.0";
};

then create a dir and file
mkdir /var/cache/bind/reverse
vi /var/cache/bind/reverse/192.168.0
@ IN SOA ns.br.com root.br.com
NS ns.br.com
3 PTR ns.br.com.


then go to /usr/bin
and check nslookup

>190.160.0.3

OR

>br.com
there is an error on both
:;connection time out; no server reached

Plz tell me what can I do
is there important for add /etc/bind/named.conf.options

---

### Post by RealPSL on 2008-03-23
I would take a look at this it was certainly beneficial to me:

[http://doc.ubuntu.com/ubuntu/serverguide/C/dns.html](http://doc.ubuntu.com/ubuntu/serverguide/C/dns.html)

It is still in draft but useful just the same.

The one thing that I am not sure I understand from your post is whether or not you switched your /etc/resolv.conf to point to your locally configured DNS server because running the test. Otherwise did you set your DNS server to the local host while running the nslookup test. Using dig to trouble shoot can be more helpful than nslookup as well.

---

