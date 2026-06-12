---
title: "Change server default language"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Mr.Carramba on 2008-02-04
Hi!
When I installed server I configured it to use Swedish language, but I would like to change it to English.
After searching the forum I find only solutions for the keybord of gui, but since I'm not using either of it solutions doesn't help :)

Any ideas how to do it?

---

### Post by ashmew2 on 2008-02-05
[http://gramps-project.org/wiki/index.php?title=Howto:_Change_the_language_of_reports](http://gramps-project.org/wiki/index.php?title=Howto:_Change_the_language_of_reports)

Let me know if you find the information useful.

I got this info from a thread on Ubuntu Forums itself , 

[http://ubuntuforums.org/showthread.php?p=4215303](http://ubuntuforums.org/showthread.php?p=4215303)

:)

---

### Post by hyper_ch on 2008-02-05
Install the language-pack-en, language-pack-en-base, manpages and uninstall their respective swedish (-se) packages. Also as root:

```

sudo dpkg-reconfigure locales

```


Check that /etc/environment has the right values, ie.

LANGUAGE="en_GB:en_US:en_GB:en"

LANG=en_GB.UTF-8
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/us r/bin:/sbin:/bin:/usr/bin/X11:/usr/games"

---

### Post by Mr.Carramba on 2008-02-05
I have installed files and exported variables
LC_ALL
LANG
LANGUAGE

but running 

```
sudo dpkg-reconfigure locales
```generates 

> 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = "en_GB:en_US:en_GB:en",
        LC_CTYPE = "en_GB:en_US:en_GB:en",
        LANG = "en_GB:en_US:en_GB:en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory


EDIT: solved, had to add LANGUAGE to /etc/envirement and move it before pach as well as efport only en_US
thank you both!

---

