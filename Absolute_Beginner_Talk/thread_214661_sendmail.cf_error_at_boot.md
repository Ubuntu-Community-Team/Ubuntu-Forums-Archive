---
title: "sendmail.cf error at boot"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by kd7swh on 2006-07-12
While booting dapper I get a strange error.

Something to the effect of:

Starting basic networkinging.

sendmail.cf could not be removed /ect/mail/sendmail.cf read only.

this lags my boot time a lot.

I tried removing sendmail with Synaptic (I am not even using it) and when I check the sendmail.cf file for removal the status bar inticates that it is a broken package and can't be removed. 

Deleteing the file as root doesn't change anything.

How can I get rid of sendmail.cf and speed up my boot time in general???

---

### Post by trent dillman on 2006-07-13
Check what's booting in the /etc/rc?.d folders, which are links to /etc/init.d. You could use sysv-rc-conf to check as well (it's in the repos).

I'd look at /etc/init.d/networking first... see if you can reproduce it with

```
sudo /etc/init.d/networking restart
```

EDIT: Don't go deleting any files or disabling services unless you know what it is! :-)

EDIT 2: try ```
sudo apt-get -f install
``` for fixing the broken packages warnings, but be careful not to uninstall a bunch of stuff.

---

### Post by kd7swh on 2006-07-13
There were a lot of shell script looking things in several of the ect/r?? directories. Some of them looked relevant. (referenced sendmail)

the first edit you listed didn't reproduce the error.

apt-get didn't fix the package either. z:-k

---

### Post by trent dillman on 2006-07-14
Install sysv-rc-conf, then run that in a terminal using sudo. That will let you turn off services.

---

### Post by richbarna on 2006-07-14
> **kd7swh said:**
> While booting dapper I get a strange error.

Something to the effect of:

Starting basic networkinging.

sendmail.cf could not be removed /ect/mail/sendmail.cf read only.

this lags my boot time a lot.

I tried removing sendmail with Synaptic (I am not even using it) and when I check the sendmail.cf file for removal the status bar inticates that it is a broken package and can't be removed. 

Deleteing the file as root doesn't change anything.

How can I get rid of sendmail.cf and speed up my boot time in general???

I had the same problem with sendmail after a Dapper update. it's a common problem. I found a workaround on this forum, where you edit a sendmail file. Do a forum search for "sendmail" and see if you can find it. I will look as well. If I find it I'll post back.

---

### Post by Carl Mueller on 2006-09-25
Here is the link to the previous discussion.

[http://www.ubuntuforums.org/showthread.php?t=166691&highlight=sendmail](http://www.ubuntuforums.org/showthread.php?t=166691&highlight=sendmail)

---

### Post by Carl Mueller on 2006-09-25
By the way, the recommended fix was to remove the files

/etc/network/if-down.d/sendmail
/etc/network/if-up.d/sendmail

I removed these files and the problem was solved.

---

