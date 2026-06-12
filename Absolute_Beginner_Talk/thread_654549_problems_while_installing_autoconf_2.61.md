---
title: "problems while installing autoconf 2.61"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by me_himanshu on 2007-12-31
Hi,
       I want to install autoconf 2.61 on my ubuntu machine...After downloading and extracting the package i try './configure' comand to configure it...it runs succesfully...thereafter when i try to compile it through 'make' command....i get an error.

"no rule to make target autoconf.texi needed by autoconf.info "

I am stuck..
Plz help....

---

### Post by Vixis on 2007-12-31
it is in repos:
> sudo apt-get install autoconf

---

### Post by Cypher on 2007-12-31
> **Vixis said:**
> it is in repos:
Agreed, v2.61 is in the Ubuntu repository. You'll find installing applications this way a lot easier than compiling it yourself, unless you need a specific version/fix and are adept at compiling packages yourself..

---

### Post by me_himanshu on 2007-12-31
Thanks for your concern but the issue is that I can not connect through internet on my machine. So, I have to explicitly download them from another machine and then compile and install on my non internet UBUNTU (Fiesty)machine .So I need to resolve this issue without SYNAPTIC MANAGER. What could be the possible solutions for this problem during MAKE of autoconf 2.61....... ERROR:no rule to make target autoconf.texi needed by autoconf.info 
 Further, please let me know that autoconf downloaded from internet will work for both Ubuntu distributions DAPPER and FEISTY.

I have stuck please help asap.

Thanks

---

### Post by Vixis on 2008-01-01
maybe you have problems with texinfo package?

you can search for packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

for example autoconf packae for feisty:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Fautoconf%2Fautoconf_2.61-3_all.deb&md5sum=1e3bce1e7a9de284965dd6f84d805c8c&arch=all&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fa%2Fautoconf%2Fautoconf_2.61-3_all.deb&md5sum=1e3bce1e7a9de284965dd6f84d805c8c&arch=all&type=main)

---

### Post by SonicRacer1412 on 2008-03-25
I have the same problem, only the error has to do with the release candidate.

---

