---
title: "[SOLVED] CenterIM"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by manro on 2007-09-18
Hi,

Have someone upgraded centericq to centerim successfully?, I been trying to find out how but with no luck!

Thanks for the help!

Regards,
Manro

---

### Post by jnorth on 2007-09-18
> **manro said:**
> Hi,

Have someone upgraded centericq to centerim successfully?, I been trying to find out how but with no luck!

Thanks for the help!

Regards,
Manro

"Upgrade" - umm no.  What I did is just apt-get remove centericq and then manually download and compile centerim.  Are you familiar with how to do that?

Edit: I forgot you also need these libs if you run into the curl-config not found error while running ./configure.```
sudo apt-get install libcurl3-dev libwww-curl-perl python2.4-pycurl
``` and if you need the ncurses dev files, then ```
sudo apt-get install ncurses-dev
```

---

### Post by manro on 2007-09-18
> **jnorth said:**
> "Upgrade" - umm no.  What I did is just apt-get remove centericq and then manually download and compile centerim.  Are you familiar with how to do that?

Edit: I forgot you also need these libs if you run into the curl-config not found error while running ./configure.```
sudo apt-get install libcurl3-dev libwww-curl-perl python2.4-pycurl
``` and if you need the ncurses dev files, then ```
sudo apt-get install ncurses-dev
```

Thanks jnorth, now I have Centerim working! :)

Regards,
Manro

---

### Post by Dr Small on 2007-09-18
Please remember to mark theads as "[SOLVED]" when they are so.

---

### Post by manro on 2007-09-18
> **Dr Small said:**
> Please remember to mark theads as "[SOLVED]" when they are so.

Oops, sorry ... forgot it! :oops:

Thanks ;)

---

### Post by jnorth on 2007-09-19
No prob - glad to help.

---

