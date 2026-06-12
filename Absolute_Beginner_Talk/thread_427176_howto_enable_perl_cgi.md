---
title: "howto enable perl cgi"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-04-29
i added this into /etc/apache2/apache2.conf:
```

Include /etc/apache2/sites-enabled/[^.#]*
Alias /cgi-bin/ /usr/lib/cgi-bin/
PerlModule ModPerl::Registry
<Location "/cgi-bin/">
 SetHandler perl-script
 PerlHandler ModPerl::Registry
 Options +ExecCGI
</Location>

```

doesn't seem to work...any suggestions?

---

### Post by kdnewton on 2007-04-29
Following guides through official Apache documentation has led me to pulling out my hair in frustration. I'd tried the approach you are attempting, too. If you want a quick and dirty way of getting cgi-bin set up for your apache web server do the following.

Create a "cgi-bin" directory in /var/www or wherever you've got your web server pointed to.

Next, create a symlink in /usr/lib that points to /var/www/cgi-bin (ie, /usr/lib/cgi-bin points to /var/www/cgi-bin) and that should get your cgi-bin working.

A longer how to can be found [here]("http://ubuntuforums.org/showthread.php?t=422412")

---

