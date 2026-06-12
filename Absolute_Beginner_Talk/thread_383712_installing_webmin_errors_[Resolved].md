---
title: "installing webmin errors [Resolved]"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by warriore on 2007-03-13
hi, I'm trying to install webmin, just downloaded the deb file on to my ubuntu desktop (i have also installed the ubuntu server with lamp) on the webmin site they say to run the following command: run the command dpkg --install webmin_1.330_all.deb and the install will be done automatically to /usr/share/webmin

error: dependacy is not satisfied libauthen-pam-perl

does this mean that I need to install perl? if so, can you please point me to instructions on how to, is there away to do it with the apt-get?

any help would be greatly apreciate it....thank you in advance! 

ty

---

### Post by warriore on 2007-03-13
q

---

### Post by warriore on 2007-03-14
could someone look at the following post: [http://www.ubuntuforums.org/showthread.php?t=383712&highlight=installing+webmin](http://www.ubuntuforums.org/showthread.php?t=383712&highlight=installing+webmin)

I'm not finding anything on the web to help me install these perl dependacies that webmin needs, thanks for your help guys! ty

---

### Post by aysiu on 2007-03-14
**Step 1**:
Get a fresh set of repositories by following [these directions](http://www.psychocats.net/ubuntu/sources). Remember to copy and paste and not retype.

**Step 2**:
Install webmin by pasting this command into the terminal: ```
sudo aptitude update && sudo aptitude install webmin
```

---

### Post by warriore on 2007-03-14
it all worked, thank you soooo much, really, thanks!

---

