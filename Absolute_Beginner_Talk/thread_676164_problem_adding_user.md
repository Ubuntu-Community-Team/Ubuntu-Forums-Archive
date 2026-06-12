---
title: "problem adding user"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by leo_br on 2008-01-23
I am experiencing a very strange issue. Installed Ubuntu Gutsy in some machines today and everything worked fine, just in one I was not able to add a second user. After trying some different possibilities I noticed that I could add the user, but only if I use a short password (6 digits) and I was trying one with (13 digits). 
This is an fresh install, I only had to change some settings on /etc/X11/xorg.conf to get it working.

Any ideas?

---

### Post by gvartser on 2008-01-23
Check out this post.

[http://ubuntuforums.org/showthread.php?t=347827](http://ubuntuforums.org/showthread.php?t=347827)

/G

---

### Post by leo_br on 2008-01-23
thanks! After I check this out tomorrow I will post if it solved or not! :)

---

### Post by leo_br on 2008-01-24
Actually after your reply I found some other related posts.
I solved it doing:
```
sudo passwd username
```

and so you can set even a blank password

---

