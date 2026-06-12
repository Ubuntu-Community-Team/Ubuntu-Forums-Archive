---
title: "Website filter"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-02-13
Is there a way websites can be blocked without using any password? A simple website entry into a box that just blocks the site is what I am looking for. It's a shared computer so using password will mean I have to share the password with other adults. I just want adult sites to be blocked from kids viewing them.

---

### Post by Brunellus on 2007-02-13
you want dansguardian.

---

### Post by Bagboy23 on 2007-02-14
I tried all day to sort out and work out dansguardian with no luck, (i'm not a technical person) is there anyting else?

In addition to adult filters, one of my friends asked if he could block certain myspace and hi5 pages, allowing only some through. So what I ideally need is to enter a website address and have it blocked, without using a password. The reason for no password is that a lot of the adults will also filter pages as they see fit, so managing the password would be hard.

---

### Post by apjone on 2007-02-14
I have riggid together squid/dansguardian/bannerfilter with a mysql/php management console and some bash to glue it together. It works well and is in use with alot of users

Also with latest dansguradian you have filter groups which is useful. group 1 = adults / group 2 = kids

---

### Post by erkki70 on 2007-02-14
Hi,
This thread might be of interest if you want to block sites.

[http://ubuntuforums.org/showthread.php?t=241460](http://ubuntuforums.org/showthread.php?t=241460)

Hope it helps...

Cheers,

---

### Post by Bagboy23 on 2007-02-14
Thanks it did help.

I just wrote a shell script to simply things (attached). 

If anyone else wants to use it please be aware that it makes use of your hosts file.

---

