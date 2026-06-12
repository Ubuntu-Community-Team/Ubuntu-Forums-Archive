---
title: "DNS configuration in ubuntu server"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by fnkhan on 2008-03-20
I m new in linux. I have some problem for configuring DNS in ubuntu server. My system IP is 192.168.0.81 and two hosts are there in my system. One is local and the other is ubuntu. I m configuring only forward zone plz send me the whole configuration & I installed built-in bind9. :guitar:

---

### Post by leroyc on 2008-03-20
From your post it is not really clear what you are trying to do.

Can you please provide with more information?

I will be glad to help if I can.

---

### Post by fnkhan on 2008-03-20
Thanks 4 reply
actully I m new in linux 
I want to configure DNS in this IP : 192.168.1.81this is my system IP. plz guid me the configuration of this.

---

### Post by LeChacal on 2008-03-20
If you mean to set up DNS so that some else can enter [www.yournamehere.com](www.yournamehere.com) to get to your website instead of 192.168.0.81. You can't set it to that ip address because that is a privte only address you have to set it to your public address, and then maybe setup Dynamic DNS unless you have a static IP address. You may want to look at /etc/resolv.conf this is where you put in your DNS address. If you are setting up a server you may also need to look at other network config files such as /etc/host.conf or the file in /etc/network, these are just some files.

---

### Post by ruy_lopez on 2008-03-20
Here's a simple [HOWTO]("http://www.langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO-5.html#ss5.3") I've used myself in the the past.

---

### Post by spiderbatdad on 2008-03-20
If you are try to set ServerName in /etc/apache2/httpd.conf, or in named.conf,  for example, so that you can reach www, then you can use ServerName 4.2.2.1 and ServerName 4.2.2.6 each on a separate line. So it should look like:

```
ServerName 127.0.0.1
ServerName 4.2.2.1
ServerName 4.2.2.6
``` Alternatively, you can replace 127.0.0.1 with your local IP.

---

### Post by fnkhan on 2008-03-20
ya ithink u r right
configured DNS on a single pc on single IPi.e. my IP is 192.168.1.81 and domain is abc.com
If i enter nslookup abc.com the result shows 192.168.1.81

---

