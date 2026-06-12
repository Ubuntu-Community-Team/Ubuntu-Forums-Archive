---
title: "Access to truecypt volume only as root, not what I want"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by dragi on 2006-06-04
Hello,

after installing kubuntu I installed a secong HD into my PC. I ancrypted this one with truecrypt and truecrypt made a Fat filesytem on it. However, I can only access this filesystem by doin "sudo truecrypt /dev/hdc1 /home/dragi/crypt" and now I have only access to crypt as root. How can I change that so that I have full access to this as user dragi?

Thank you so much

dragi

---

### Post by Zar on 2006-07-27
Do this once: sudo chmod u+s /usr/bin/truecrypt
And then a non-root user can open the volume: truecrypt -u /volume /mountpoint

---

### Post by aysiu on 2006-07-27
Read [this](http://www.ubuntuforums.org/showthread.php?t=216356).

---

