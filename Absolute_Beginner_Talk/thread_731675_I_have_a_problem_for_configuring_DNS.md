---
title: "I have a problem for configuring DNS"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by fnkhan on 2008-03-22
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

### Post by RealPSL on 2008-03-22
This might sound like silly questions but you did not mention it in your post so I have to ask. 

1. Did you configure your /etc/resolv.conf to point to the DNS server you just configured?
2. When you did the nslookup (prefer dig in this case) did you set the server value to the DNS server you just setup if the answer to one is no?

---

### Post by fnkhan on 2008-03-23
i already configure /etc/resolv and server value

---

### Post by RealPSL on 2008-03-23
can we see the output of /usr/sbin/named-checkconf and /usr/sbin/named-checkzone run against your configuration and zone files?Also did you check /var/log/messages for errors after starting the DNS server (named process).

---

