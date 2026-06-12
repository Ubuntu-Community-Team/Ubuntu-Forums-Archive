---
title: "Ubuntu Distro Version?"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by wirespeed on 2006-02-28
This is a really stupid question, but I'll ask it anyway.

How do I tell which version of the ubuntu I'm running?  i.e 5.10 vs. 6.04?

As a followup, if I wanted to try and update to 6.04 from 5.10, how would I go about doing that?  There's no critical data on my box, so it's not a huge deal if I have problems.

Thanks in advance.

---

### Post by engla on 2006-02-28
you can read the output from 'uname -a' and from the kernel version deduce what release you are running.

Breezy uses 2.6.12-x and dapper 2.5.15-x

---

### Post by wirespeed on 2006-02-28
Thanks!

---

### Post by 5-HT on 2006-02-28
[quote=wirespeed]How do I tell which version of the ubuntu I'm running? i.e 5.10 vs. 6.04? [/quote]

Here are a couple of nice ways:

```
 lsb_release -a 
```
or

```
 cat /etc/issue 
```

Hope that helps.

***EDIT:** Missed that question about upgrading...

[quote=wirespeed]As a followup, if I wanted to try and update to 6.04 from 5.10, how would I go about doing that? There's no critical data on my box, so it's not a huge deal if I have problems. [/quote]

**I would strongly recommend you read this cautionary thread about upgrading to dapper when it's in development** (as it will be until its release sometime in april):

[http://www.ubuntuforums.org/showthread.php?t=93157](http://www.ubuntuforums.org/showthread.php?t=93157)

If you would still like to upgrade and are aware of the consequences, to do so is as easy as:

1. Replace every instance of 'breezy' with 'dapper' in  /etc/apt/sources.list
 (making backups of files such as these is always a good idea before modifying them)
2. ```
 sudo apt-get update 
```
3. ```
 sudo apt-get dist-upgrade 
```

HTH

---

### Post by taurus on 2006-02-28
Just so you know, Ubuntu 6.04 means April of 2006!!!

---

### Post by wirespeed on 2006-02-28
Thank you, that was extremely helpful.  This is actually the first version of Linux I'm actually enjoying using.

---

