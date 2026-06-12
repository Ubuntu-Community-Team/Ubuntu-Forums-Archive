---
title: "krb5-user broken packages"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by briansrapier on 2006-09-07
Greetings. I am a newbie to Ubuntu/Debian, but have been using Redhat and Gentoo distros for some time. 

I am attempting to do my first Ubuntu/AD integration having successfully completed it with other distros. Using the HowTo:

[http://ubuntuforums.org/showthread.php?t=91510&highlight=krb5-user](http://ubuntuforums.org/showthread.php?t=91510&highlight=krb5-user)

I attempted to install krb5-user, but get the message:

The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.4.3-5) but 1.4.3-5ubuntu0.1 is to be installed
  krb5-user: Depends: libkadm55 (= 1.4.3-5) but 1.4.3-5ubuntu0.1 is to be installed

The only info I could find related to the issue was a bug with Breezy in which the work-around was to add universe to the security download sites. 

Is there a way to force the dependancy? I'm not as familiar with the in's and out's of apt-get.

Thanks.

---

### Post by snowpalmer on 2006-09-07
I just had this problem.  The reason is that I uncommented the normal universe repository in /etc/apt/sources.list but I didn't uncomment the security updates universe repository.  Once I fixed that it worked fine.

---

### Post by briansrapier on 2006-09-08
Yep. That was the ticket. Thanks.

---

### Post by beatmix01 on 2006-10-05
sweet!  I also ran into this problem and uncommenting the sec universe repo did the trick!

Thank you snowpalmer

---

### Post by cwhitmore on 2006-10-20
I tried the suggestions above, I even uncommented all of the security and universe lines, but I'm still getting the same error. I'm running the desktop version 6.06.1.
Any Ideas?

---

### Post by tang0 on 2006-10-26
I worked all the morning with this issue. ](*,)  
After lunch, I readed this thread.

My solution was add universe an multiverse to security sources in /etc/apt/sources.list

my security sources were this ones:

```

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

```

and now, with problem solved are:

```

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

hope this helps ;) 

Mauro

---

### Post by cwhitmore on 2006-10-26
Thanks, that was the issue.

---

### Post by dowski on 2008-03-19
Thanks.  Adding the universe security repo did the trick for me too!

---

