---
title: "SPM confused?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by fjm03 on 2007-01-23
SPM keeps attempting to  install automatix2/edgy on my dapper system. I already have automatix2/dapper installed.

Why is SPM trying to install an unsuitable app?

I'm tired of looking at the false update icon.

How can I instruct SPM to stop promoting the 6.10 version.

Thanks.

---

### Post by Shatrat on 2007-01-23
Perhaps automatix added some edgy repositories?
Im not 100% sure this is the best way, but you could try editing /etc/apt/sources.list and put a # in front of all the Automatix entries which have edgy in them.

---

### Post by jvc26 on 2007-01-23
SPM Shouldnt try to put on edgy packages unless you have set up your /etc/apt/sources.list to have edgy repos in it. Go to:
```

gksudo gedit /etc/apt/sources.list

```
And check that the text there matches this:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories)
As it sounds like you have edgy repos in your list.
Il

---

### Post by fjm03 on 2007-01-23
To shatrat and illuvator:
Thanks. That's apparently what transpired.
Rmed 3 edgy files from /var/lib/apt/lists  and problem solved.
Again thanks.

---

### Post by jvc26 on 2007-01-23
Not at all mate, glad to be of help :)
Il

---

