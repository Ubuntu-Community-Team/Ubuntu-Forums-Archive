---
title: "multiverse, universe, and PLF repository update errors"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-11-25
In xfce's update manager I keep getting these errors on these 2 repositories, I wonder if their names have been changed. I just reinstalled for an unrelated reason, and before that with synaptic it looks like I was getting the exact same errors, except the multiverse one. 

> [http://mo.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://mo.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://mo.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://mo.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)

Also, some dumbed down advice on how to deal with this would be appreciated:

> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718


Thank you

---

### Post by DougieFresh4U on 2006-11-25
wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -    **That should work**

---

### Post by leetrefz on 2006-11-25
so I put the key in after apt-key add? 

No luck. says no such file or directory, with nothing, the key (F120156012B83718 ), and the http address. 

I wasn't kidding when I said I need it dumbed down.

---

### Post by DougieFresh4U on 2006-11-25
wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add  **"Get that in that terminal!**"

---

### Post by leetrefz on 2006-11-25
Ah. sudo in the middle. does this:> chief@chief-toshiba:~$ wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add
Password:--10:51:16--  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
           => `-'
Resolving packages.freecontrib.org... 88.191.37.159
Connecting to packages.freecontrib.org|88.191.37.159|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,120 (2.1K) [application/octet-stream]

100%[====================================>] 2,120         --.--K/s             

10:51:20 (112.32 MB/s) - `-' saved [2120/2120]




why not back to chief@chief-toshiba:~$ ?
there's a sudo in there but it didn't ask for the password. 
Still gives me the 
> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

---

### Post by AndyCooll on 2006-11-25
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add
```

Copy and paste the above (exactly as it appears) into a terminal. If that still doesn't work then either the site is temporarily unavailable or they've changed the key.

:cool:

---

### Post by leetrefz on 2006-11-26
ok, still not working for me, if they changed the key how would i find it?

and anyone know what to do with the other ones? that's a bit more pressing.

---

### Post by leetrefz on 2006-11-26
well changing the server seems to do the trick. why no tkeep all the servers up to snuff?

---

### Post by lawina on 2006-12-02
> **AndyCooll said:**
> ```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add
```

Copy and paste the above (exactly as it appears) into a terminal. If that still doesn't work then either the site is temporarily unavailable or they've changed the key.

:cool:

This worked for me. Mucho thanks.

---

### Post by K.B. on 2006-12-04
am getting the same errors... tried the solution and this is what I get:

[I][INDENT]--22:23:09--  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
           => `-'
Resolving packages.freecontrib.org... gpg: can't open `': No such file or directory
88.191.37.159
Connecting to packages.freecontrib.org|88.191.37.159|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,120 (2.1K) [application/octet-stream]

 0% [                                     ] 0             --.--K/s             


Cannot write to `12B83718.gpg' (Broken pipe).
[/INDENT][/I]


I tried it more then once and made sure I did a good copy/paste but I still get the same problem.

---

### Post by WhErE on 2006-12-09
Hey there. I was having the same problem myself, I think you are missing the hyphen at the end of that statement. It worked for me when I added that.

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -


--12:52:44--  [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg)
           => `-'
Resolving packages.freecontrib.org... 88.191.37.159
Connecting to packages.freecontrib.org|88.191.37.159|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,120 (2.1K) [application/octet-stream]

100%[==================================>] 2,120         --.--K/s             

12:52:44 (3.47 MB/s) - `-' saved [2120/2120]

OK

---

