---
title: "Error"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by shawn fernandes on 2006-12-03
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


I have got this message after installing the software updates. What does it mean and what do I do about it?

Thank you

---

### Post by shawn fernandes on 2006-12-03
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718

And I this message in my terminal.

---

### Post by kakalaky on 2006-12-03
You need to get the key for the EasyUbuntu repo you added.  Just type this in a terminal:

```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O - | sudo apt-key add -
```

---

### Post by wesley_of_course on 2006-12-12
gpg: can't open `12B83718.gpg': No such file or directory
wesley@RatDog:~$ sudo wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O - | sudo apt-key add -
--01:15:30--  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
           => `-'
Resolving packages.freecontrib.org... 88.191.33.6
Connecting to packages.freecontrib.org|88.191.33.6|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:15:30 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.


    What up ?  Tried a few different approaches and get the same response .

                       ](*,) 

   Thanks in advance !

---

