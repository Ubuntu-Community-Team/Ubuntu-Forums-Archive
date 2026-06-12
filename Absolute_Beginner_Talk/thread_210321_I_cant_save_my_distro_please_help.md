---
title: "I cant save my distro please help"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by MACRI on 2006-07-06
im editing my distro and i get this message 

```
** (gedit:10193): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.

```

how i got there for the extra noobish

```
sudo gedit /etc/apt-get/sources.list
```

and what im putting into it if anyone else wants any of it.

```

## Add comments (##) in front of any line to remove it from being checked.  
## Use the following sources.list at your own risk.  

deb HTTP://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src HTTP://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb HTTP://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src HTTP://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb HTTP://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src HTTP://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb HTTP://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src HTTP://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb HTTP://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src HTTP://packages.freecontrib.org/ubuntu/plf dapper free non-free 
```

---

### Post by Lord Illidan on 2006-07-06
I think you got the location wrong. It should be:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by MACRI on 2006-07-06
[QUOTE=Lord Illidan]I think you got the location wrong. It should be:
```
sudo gedit /etc/apt/sources.list
```[/QUOTE]
thank you very much. it works perfectly. :D

---

### Post by Lord Illidan on 2006-07-06
[quote=MACRI]thank you very much. it works perfectly. :D[/quote]

No prob, just a word of advice.
Next time rename your title better though. better say "Problem with gedit" than "i can't save my distro please help".

All the best!

---

