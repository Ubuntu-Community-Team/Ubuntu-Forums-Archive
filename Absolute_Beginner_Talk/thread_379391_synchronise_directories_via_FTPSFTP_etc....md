---
title: "synchronise directories via FTP/SFTP etc..."
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Incompetnce on 2007-03-08
I used winSCP before becoming an ubuntu convert and I really like the "keep directories synchronised" option; this would keep the remote directory up to date as i altered things in the local. Does any program available through the package manager offer this kind of thing? I can even get anything to synchronise once, let alone continually...

I may have missed the option, but neither gftp nor kasablanca seemed to have the feature im looking for...

---

### Post by haelters on 2007-03-08
you might check out Unison : [http://www.cis.upenn.edu/~bcpierce/unison](http://www.cis.upenn.edu/~bcpierce/unison)

Hope it helps !

---

### Post by Incompetnce on 2007-03-08
perfect. thanks. i havent quite got it to work yet though. i cant work out what is the right address for the remote folder...

---

### Post by haelters on 2007-03-09
the right hand side would be something like this ssh://hostname//home/me/test2 if you can use sftp. 
Ideally you should use ssh with keys so that you don't need to enter the password each time.

Hope it helps !

---

### Post by Incompetnce on 2007-03-09
what about my username? should it be Username@ssh://hostname/etc ?

---

