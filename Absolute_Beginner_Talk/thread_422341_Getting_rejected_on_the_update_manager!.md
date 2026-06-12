---
title: "Getting rejected on the update manager!"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by karishbhr on 2007-04-25
Trying to upgrade to 7.04 and here is the error i get, what now?



> Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

---

### Post by kevinlyfellow on 2007-04-25
You get an error because the server doesn't seem to exist anymore... they are very old anyways, dating back to breezy.

Do you know what was on the server?

---

### Post by karishbhr on 2007-04-25
ok, but when i close out of that window it exits the upgrader

---

### Post by kevinlyfellow on 2007-04-25
Can I see your sources.list file?

```
cat /etc/apt/sources.list

```

---

### Post by Sef on 2007-04-25
> You get an error because the server doesn't seem to exist anymore... they are very old anyways, dating back to breezy.

If that is the case, then I would open the terminal and comment out those lines.  To comment out means that those lines will be ignored.

First, Applications > Accessories > Terminal

Second, type in this code: ```
gksudo gedit /etc/apt/sources.list
```

Third, to comment out those repositories add a # before them.

How they would look after commenting them out:

> 
#[http://antesis.freecontrib.org/mirro...zy/](http://antesis.freecontrib.org/mirro...zy/)
#[http://antesis.freecontrib.org/mirro...tion-en_US.bz2](http://antesis.freecontrib.org/mirro...tion-en_US.bz2) 
#[http://antesis.freecontrib.org/mirro...tion-en_US.bz2](http://antesis.freecontrib.org/mirro...tion-en_US.bz2) 

---

### Post by karishbhr on 2007-04-25
thanks, that worked

---

