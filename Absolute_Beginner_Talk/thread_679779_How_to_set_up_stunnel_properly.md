---
title: "How to set up stunnel properly?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Dirtbead on 2008-01-27
Hi

I am trying to set up stunnel but it keeps asking for stunnel.pem when I try to run it from the terminal.
Please can somebody help me step by step in how to get stunnel up and running?

Thanks for your help :)

---

### Post by ~LoKe on 2008-01-27
Can we please have the exact terminal output?

---

### Post by Dirtbead on 2008-01-27
2008.01.27 16:27:15 LOG3[10114:3082925744]: /etc/stunnel/stunnel.pem: No such file or directory (2)

---

### Post by seventhc on 2008-01-27
I think just run stunnel with your options from the terminal don't use the path like you have.
How did you install it??
```
sudo apt-get install stunnel
```worked for me.

---

### Post by ~LoKe on 2008-01-27
By default stunnel.pem is not added to /etc/stunnel.  I'm not entirely familiar with this process, but I believe we can work it out.  Navigate to [this](http://www.stunnel.org/pem/) website and fill out the necessary details.  Once it generates the file, paste the contents into **/etc/stunnel/stunnel.pem**

---

### Post by Dirtbead on 2008-01-27
Ok I have a new error now:

2008.01.27 16:44:12 LOG4[10561:3082983088]: Wrong permissions on /etc/stunnel/stunnel.pem
inetd mode must define a remote host or an executable

The version I am using is stunnel4 from the repositories.

---

### Post by ~LoKe on 2008-01-27
You must run stunnel with sudo or as root.  Also, make sure to run this in the terminal to change the permissions:
```
sudo chmod 600 /etc/stunnel/stunnel.pem
```

---

### Post by Dirtbead on 2008-01-27
Ok after applying that I have this error:

2008.01.27 16:51:26 LOG3[10647:3082634928]: Error reading certificate file: /etc/stunnel/stunnel.pem
2008.01.27 16:51:26 LOG3[10647:3082634928]: error stack: 140DC002 : error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib
2008.01.27 16:51:26 LOG3[10647:3082634928]: error stack: 20074002 : error:20074002:BIO routines:FILE_CTRL:system lib
2008.01.27 16:51:26 LOG3[10647:3082634928]: SSL_CTX_use_certificate_chain_file: 200100D: error:0200100D:system library:fopen:Permission denied

---

### Post by jjb123 on 2008-02-08
I get this message too. Does anyone know how to fix this?

---

### Post by zbot on 2008-03-10
> **~LoKe said:**
> By default stunnel.pem is not added to /etc/stunnel.  I'm not entirely familiar with this process, but I believe we can work it out.  Navigate to [this](http://www.stunnel.org/pem/) website and fill out the necessary details.  Once it generates the file, paste the contents into **/etc/stunnel/stunnel.pem**

Also, try:
openssl req -new -x509 -days 3650 -nodes -out stunnel.pem -keyout stunnel.pem

as shown in this post:

[http://www.z-bots.com/blog/?p=26](http://www.z-bots.com/blog/?p=26)

I am trying to find a solution for this post, any addt'l info is much appreciated!

Zbot_1

---

### Post by zbot on 2008-03-10
> **Dirtbead said:**
> Ok after applying that I have this error:

2008.01.27 16:51:26 LOG3[10647:3082634928]: Error reading certificate file: /etc/stunnel/stunnel.pem
2008.01.27 16:51:26 LOG3[10647:3082634928]: error stack: 140DC002 : error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib
2008.01.27 16:51:26 LOG3[10647:3082634928]: error stack: 20074002 : error:20074002:BIO routines:FILE_CTRL:system lib
2008.01.27 16:51:26 LOG3[10647:3082634928]: SSL_CTX_use_certificate_chain_file: 200100D: error:0200100D:system library:fopen:Permission denied

What command are you using?

try:
sudo /etc/init.d/stunnel4 start

Cheers,
-Zbot_1

---

