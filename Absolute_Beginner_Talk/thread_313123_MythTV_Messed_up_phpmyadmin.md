---
title: "MythTV Messed up phpmyadmin"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-05
Hi all
I tried installing MythTV - which didn't work but now if I go to "LocalHost" and try to access phpmyadmin/ - Firefox askes me what I want to do eith this file?

Previously this link would ask for my MySQl username and pword and would then open the MySQl control page. How can I ge this back.


MythTV is a real pain in the a$$.

---

### Post by superm1 on 2006-12-05
Sounds to me like you are missing the the apache php package.  Check and make sure that you have either libapache2-mod-php5 or libapache2-mod-php4 installed.

---

### Post by dkenny on 2006-12-11
[QUOTE=superm1]Check and make sure that you have either libapache2-mod-php5 or libapache2-mod-php4 installed.[/QUOTE]

OK, I checked that and I had php5 installed. I added php4 and it still isn't working.
Any other ideas?

---

### Post by superm1 on 2006-12-12
Well someone else that encountered this issue completely removed all php related and apache2 related packages and their configuration files and reinstalled to solve the problem.

If you'd like to diagnose (eg you have configured other websites in apache and don't want to rewrite configs), then the first thing to check
is /etc/apache2/mods-enabled.

You should get something similar to this:
```
mythtv@mythdell:/etc/apache2/mods-enabled$ ls
cgi.load  php5.conf  php5.load  rewrite.load

```

---

### Post by gosh on 2006-12-13
What worked for me (SuperM1's suggestion in another thread) is clearing the cache in Firefox

---

### Post by superm1 on 2006-12-13
Sounds like something I did say in another thread.  So yea, what I said :)

---

### Post by dkenny on 2006-12-14
> **superm1 said:**
> Well someone else that encountered this issue completely removed all php related and apache2 related packages and their configuration files and reinstalled to solve the problem.

Is there a way for me to generate a list of installed packages? (I'm sure there is - I'm just ignorant)

If  I post a list here could you identify what needs to be uninstalled and re-installed?

---

### Post by superm1 on 2006-12-14
> **dkenny said:**
> Is there a way for me to generate a list of installed packages? (I'm sure there is - I'm just ignorant)

If  I post a list here could you identify what needs to be uninstalled and re-installed?

dpkg -l

will generate a list of installed packages.

Offhand, I can think that anything libapache2*, anything apache2*, php4, php5.  I'm sure there are a few more that are missing though in that list.

---

### Post by dkenny on 2006-12-14
Here's the list I've generated based on your wildcards. (I attached the full set of packages also.
I only installed apache as part of my abortive attempt to install MythTV.

I assume, therefore, that I should be OK uninstalling and reinstalling all of the following?

apache-common
apache2
apache2-common
apache2-mpm-prefork
apache2-utils
libapache-mod-php4
libapache2-mod-auth-mysql
libapache2-mod-php5
php4-common
php5-cgi
php5-common
php5-mysql
php5-mysqli
phpmyadmin

---

### Post by superm1 on 2006-12-14
> **dkenny said:**
> Here's the list I've generated based on your wildcards. (I attached the full set of packages also.
I only installed apache as part of my abortive attempt to install MythTV.

I assume, therefore, that I should be OK uninstalling and reinstalling all of the following?

apache-common
apache2
apache2-common
apache2-mpm-prefork
apache2-utils
libapache-mod-php4
libapache2-mod-auth-mysql
libapache2-mod-php5
php4-common
php5-cgi
php5-common
php5-mysql
php5-mysqli
phpmyadmin
The easiest solution to mythweb and phpmyadmin working will be to remove all those,purge any configuration files for any of them, install mythweb (which resolves all apache dependancies), and then install phpmyadmin.

If you want to make sure mythweb install goes smoothly, here is the workaround guide for the current version:
[https://help.ubuntu.com/community/MythTV_Edgy_Backend#head-8e655335dc86ca02c9a0aeb300f57e8c00af3a48](https://help.ubuntu.com/community/MythTV_Edgy_Backend#head-8e655335dc86ca02c9a0aeb300f57e8c00af3a48)

---

