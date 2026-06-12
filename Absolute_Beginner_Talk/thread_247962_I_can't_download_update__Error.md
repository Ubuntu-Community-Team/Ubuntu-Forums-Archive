---
title: "I can't download update : Error"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by invigo on 2006-08-31
I've tried to download system update, that is libtag1c2a.When downloading of the package begins, a warnig window occurs, stating:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-4~dapper1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-4~dapper1_i386.deb)
  404 Not Found

---

### Post by Bachstelze on 2006-08-31
did you *sudo apt-get update* ?

---

### Post by gsdefender on 2006-08-31
The package has probably not hit your mirror, as of yet.

You have two choices:

1) Wait till is (doing ```
sudo apt-get update; sudo apt-get upgrade
``` from time to time);

2) Add a second mirror to your /etc/apt/sources.list. I am not using Ubuntu on i386, but I've checked that en.archive.ubuntu.com has the package, so simply add.

```

deb http://en.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

```

then do the usual

```

sudo apt-get update; sudo apt-get upgrade

```

and you should be able to get it.

---

### Post by whizbaby on 2006-08-31
(only do this when the stuff above doesn't help)
The link you're trying to download in fact doesn't exist, this is the correct one:
[http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-3_i386.deb)

you can download it by pasting it in your browser's adress line and then install with dpkg 
(go (in terminal) to the place you downloaded it and type
sudo dpkg -i libtag1c2a_1.4-3_i386.deb)
if automatic installation fails.

---

