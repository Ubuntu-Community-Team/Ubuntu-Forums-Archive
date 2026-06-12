---
title: "Problems Upgrading to Feisty"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by meanburrito920 on 2007-08-11
I have been running Edgy for a while now and finally decided to Upgrade to Feisty. However, when I go to update through update manager, I get an error message that says Error during Update: ```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```
It also says that the problem probably is with my network connection, but I have checked and everything seems to be running properly, it just wont upgrade. [EDIT] I burned a CD of Feisty also. Is there a way to upgrade from CD without doing a clean install?

---

### Post by kast on 2007-08-11
Do you have a mix source list? Try commenting out all unofficial repos then try the upgrade again.

---

### Post by Jimmyfj on 2007-08-11
I'd say if you already have a Feisty Cd you are better off with a clean install that an upgrade. Upgrading via the Internet takes TIME, I've tried and it took more than 6 hours to complete. Unless you have some data you just WANT to keep you are better off with a clean flawless install.

---

### Post by bwtranch on 2007-08-11
You know the upgrade path is really not recommended. Although it can be done that way. The preferred method is to burn an iso and do a clean install. And you know what? I agree. You are going to be better off in the long run. Because when you upgrade to Gutsy, this will be way better. Trust me on this one.

---

### Post by halitech on 2007-08-11
you say you are running edgy now? then why is that repo looking for edgy-security? if you are trying to upgrade, it should be pointing at fiesty, not edgy

---

### Post by bwtranch on 2007-08-11
Re: #3 You know I did agree with what you said. But the part about it taking 6 hrs. That depends on your connection speed. I am lucky enough to have a T3 line and it takes about 10 mins. to download 700 MB :shock: Well, I know that I am lucky to have that and I thank the internet gods everyday :)  But, the point is, that it just depends on what you have available.

---

