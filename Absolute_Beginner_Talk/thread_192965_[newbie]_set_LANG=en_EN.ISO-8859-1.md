---
title: "[newbie] set LANG=en_EN.ISO-8859-1"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by derbouka on 2006-06-09
Hi!

I'm starting using linux/ubuntu and I would like to know how can I change my local language to en_EN.ISO-8859-1?
When I do 'locale' I have this configs:
> LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=


---

### Post by derbouka on 2006-06-10
what?! I can't get help on this issue on ubuntu forum???:evil: 
Thanks anyway and bye!

---

### Post by derbouka on 2006-06-13
For those who may have the same problem..

[LIST][*]First I had to install en_US.ISO-8859-1 encoding:
**[root terminal]**
```
$ cd /usr/share/locales
$ sudo ./install-language-pack en_US
```

[*]Then edited the file "/etc/locale.gen" and added to it "en_US ISO-8859-1"
[command to edit the file: **$ sudo gedit /etc/locale.gen**]
[my /etc/locale.gen file]
```
en_US ISO-8859-1
pt_PT ISO-8859-1
pt_BR ISO-8859-1
en_GB ISO-8859-1

```

[*]Then run this command to generate the locales:
**$ sudo locale-gen**


[*]And finally, edited the file "/etc/environment" like this:
[command to edit the file: **$ sudo gedit /etc/environment**]
[my /etc/environment file]
```
LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=en_US
```[/LIST]
Ok, I logged out and logged back in, and my application is now working as it should(as in windows ;))..

I've used this links to solve my problem:
[LIST]
[*][http://www.subterfugios.net/blog/](http://www.subterfugios.net/blog/)
[*][http://ubuntuforums.org/archive/index.php/t-6856.html](http://ubuntuforums.org/archive/index.php/t-6856.html) (post by cscc_leth )
[/LIST]

---

