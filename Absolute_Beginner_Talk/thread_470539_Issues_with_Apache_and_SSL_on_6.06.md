---
title: "Issues with Apache and SSL on 6.06"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by coupdetard on 2007-06-11
I am running Dapper on an eMac, thus PPC. I am trying to set up the apache webserver manually, ie I downloaded the source and have been trying to get some customizations to work for me.

It should be noted that I am new at this, kinda, but I'm not completely lost.

One of the custom modules I wanted to load for my apache server was SSL. When I run the configure script with the many enable flags everything goes well until it checks for the SSL dependencies, which it says it has none of. I looked it up and the module relies on OpenSSL. I checked synaptic and it says it is installed. Though just to be safe I downloaded the source for openssl and installed it myself then restarted. However still no dice. 

So if anyone has any ideas I would be very grateful and thanks in advance.

---

### Post by Wardazo on 2007-06-11
Hi

First of all, if this is your first attempt at setting up a server I would recommend that you use apt-get for apache. It works pretty much straight out of the box with mysql postfix php and of course the apache mods.

It's kind of difficult to diagnose your problem with such a small amount of information. Genarally it's a very good idea to copy any error messages into your post.

Did you choose a manual instalation to chroot the server?

Which version of apache are you running?

I'll guess you're running apache2, could you tell me what error message if any you get when you enter:

sudo apache2-ssl-certificate -days 365

Post back with some error messages and I'll see if I can help;)

Ward

---

### Post by coupdetard on 2007-06-11
I haven't even gotten apache 2.2.4 installed yet. I am just working on my configure, ie running:

```
 $./configure --enable-authn-dbd=shared \ 
>--enable-cgi=shared \
>--enable-actions=shared \
>--enable-dbd=shared \
>--enable-speling=shared \
>--enable-ssl=shared \
>--enable-userdir=shared 
```

I am letting it install to it's default directory which is why there is no prefix flag. I am going to try the apt-get for apache if this becomes too much of a hassle but in all of my experiences I have found that I learn much more by throwing myself into the deepend and working m way back out. So, that is kinda what I am doing here.

Anyway, this is what the configure says when it gets to the point that it is checking the SSL dependencies:
```

checking whether to enable mod_ssl... checking dependencies
checking for SSL/TLS toolkit base... none
checking for OpenSSL version... checking openssl/opensslv.h usability... no
checking openssl/opensslv.h presence... no
checking for openssl/opensslv.h... no
checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
no OpenSSL headers found
checking for SSL-C version... checking sslc.h usability... no
checking sslc.h presence... no
checking for sslc.h... no
no SSL-C headers found
configure: error: ...No recognized SSL/TLS toolkit detected

```

As I said in last post I assure you that I synaptic says I have openssl installed but on top of that I installed it myself to see if that would help. So yeah, any ideas? Thanks for posting back to me so quickly and thanks again for any help you can give me.

---

