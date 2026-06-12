---
title: "&quot;dependency is not satisfiable: libcurl3&quot;"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by OldDog1 on 2007-12-07
Hi,

I am trying to install some software from CNR.COM. In order to do that I need the cnr client.
When I try to install that I get this:  "dependency is not satisfiable: libcurl3" Libcurl3 appears to be installed on my machine. So now what?

I am running Ubuntu 7.10 (for about 2 days)

Thanks,

Olddog1

---

### Post by PmDematagoda on 2007-12-07
I do not think CNR is still stable enough for normal day-to-day work on Ubuntu, what programs are you trying to install anyway?

---

### Post by S3Indiana on 2007-12-07
> **OldDog1 said:**
> Hi,

I am trying to install some software from CNR.COM. In order to do that I need the cnr client.
When I try to install that I get this:  "dependency is not satisfiable: libcurl3" Libcurl3 appears to be installed on my machine. So now what?

I am running Ubuntu 7.10 (for about 2 days)From [here]("http://community.cnr.com/docs/DOC-1035"):
# Uncomment the following two lines to add software from the 'backports' repository
deb     [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

---

