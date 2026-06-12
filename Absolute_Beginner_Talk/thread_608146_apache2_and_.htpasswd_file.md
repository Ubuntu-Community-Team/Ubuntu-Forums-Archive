---
title: "apache2 and .htpasswd file"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by mmokay on 2007-11-09
Hi all,

Yup, newbie here.

I seem to be doing ok so far, have apache2, php5 and mysql installed on Gutsy. Using it as a test server for web developing. I have htaccess'd my www root, and put a htpasswd file in /var/lock/ which "lock" is a dir i created to store the htpasswd file. However for whatever reason, it randomly (not sure when it happens) gets removed.

So I end up with Internal Server Errors.
The .htaccess file is looking for /var/lock/.htpasswd but it is gone.
If I put it back it works fine again, then the next day, it is gone again.

Any idea what could be removing my .htpasswd file?

Thanks a million.

PS: By the way, i am a total convert. Why the hell had a I been using crappy old Microsoft for so long. I will never been turning back. I cannot believe this is all free!

---

### Post by Daveski on 2007-11-18
Is it the file or "lock" directory which is vanishing?

---

### Post by tierrah on 2007-12-06
hi!

I also have a problem in a accessing my files. I have  enabled htaccess and htpasswd in one of my directories. When I tried to access it in the web it won't authenticate the username and password I have supplied.

Can you give me any ideas why I can't login?

Thanks!

---

