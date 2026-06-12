---
title: "Openvpn - need new keys"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by kelliot on 2007-12-18
I had a tech person install openvpn on our dapper drake server and create 4 user keys.  They have all been installed onto remote computers and work great. 

Now I need to generate 2 more keys and the tech person is GONE!

I tried to do this by running ./build-key clientXX

but I get an error that says I needed to define the KEY_DIR

I'm not sure how to do that.  In vars it is defined as keys, which there is.

any ideas?

thanks

---

### Post by koenn on 2007-12-18
post the comand you give and the error exactly as it appears on your screen.

---

### Post by kelliot on 2007-12-18
/etc/openvpn/easy-rsa$ ./build-key user5
you must define KEY-DIR

This is all that happens

---

