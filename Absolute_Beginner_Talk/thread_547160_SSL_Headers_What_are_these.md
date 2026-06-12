---
title: "SSL Headers? What are these?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by DAE_JA_VOO on 2007-09-09
I'm trying to install **partimage** (i had to compile it myself). But i've got a bit of an issue. It gave me a few problems and told me that it needed libraries, and i installed them through synaptic, and then it went PAST them, but now i get this:

> checking for strings.h... (cached) yes
checking for getopt.h... (cached) yes
checking for sys/types.h... (cached) yes

checking for openssl... /usr/bin/openssl
configure: checking  for SSL Library and Header files ... ...
checking "for rsa.h crypto.h x509.h pem.h ssl.h err.h"... "no"
configure: error:  SSL Headers not found. 


How do i install these "headers"?

Thanks for the help :)

---

### Post by annda on 2007-09-09
did you install libsssl-dev? and what is wrong with the partimage package in the rpositories?

---

### Post by DAE_JA_VOO on 2007-09-09
> **annda said:**
> did you install libsssl-dev? and what is wrong with the partimage package in the rpositories?

I did yes.

I can't find it in the repositories. Is there a specific repository i should add to use as a source?

---

### Post by DAE_JA_VOO on 2007-09-09
Anyone?

---

### Post by DAE_JA_VOO on 2007-09-10
> **DAE_JA_VOO said:**
> I can't find it in the repositories. Is there a specific repository i should add to use as a source?

?

---

### Post by BrendanM on 2007-09-10
You'll need to enable the "Universe" repositories: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

[http://packages.ubuntu.com/feisty/admin/partimage](http://packages.ubuntu.com/feisty/admin/partimage)

---

### Post by monkeyking on 2008-06-05
libssl-dev
not libsssl-dev

---

### Post by Joeb454 on 2008-06-05
Not sure that's entirely relevant anymore - last thread activity was September 2007 ;)

---

