---
title: "permissions for /usr/local/bin ?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by 5-HT on 2005-12-23
Hi, i'm wondering if someone may be able to clear up one tiny thing for me...


I installed f-prot (.deb package through dpkg from f-prots website) which created the /usr/local/bin directory within which  a symbolic link to its shell executable script was placed, but for some reason it only gave executable permissions of that directory and link to root (700 permissions all together).

This install was an upgrade, and the previous version gave exec permissions to everyone, so I'm wondering if it's ok to give exec permissions to everyone for /usr/local/bin (in general) so a normal user may run f-prot, or if that may be a security risk/issue ?


I see that /usr/bin & /bin has executable permissions for everyone (755 permissions all together) so I think this is ok (especially given the nature of bin directories...) but just wanted to make sure...anyone have any suggestions?


Thanks for any help

(I posted this on the f-prot how to, but looks like no one else was having this issue, and as it's more of a general permissions question for /usr/local/bin and not f-prot * per se * I'm posting this here hoping no one gets annoyed/has aversions to this...sorry about this if you do).

---

### Post by Kyral on 2005-12-23
According to the Debian Policy Guide packages aren't supposed to put ANYTHING in /usr/local. /usr/local is generally for compiled programs (ones that you do the ./configure, make, sudo make install dance for)...what is wrong with the F-Prot from the Repos? (I know this odoesn't answer your question but bear with me for a sec)

---

### Post by 5-HT on 2005-12-23
Thanks for the info, didn't know /usr/local/bin was the preferred path to place for compiled programs.

I installed f-prot from a .deb downloaded straight from the f-prot website instead of the f-prot installer in the repos (maybe doing the install through that method would have placed the link in a better palce...).

I just created a symbolic link in /usr/bin pointing to the f-prot script, would that be a good place for it?

---

### Post by Kyral on 2005-12-23
yah..make sure the permissions are right though

---

