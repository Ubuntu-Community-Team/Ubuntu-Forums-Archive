---
title: "quick question about a missing &quot;default&quot; dir?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Simimi on 2007-11-10
Where is the root directory for Web documents (normally /var/www, right?) in Ubuntu Gutsy? I never looked for it or needed it before, but now that I want to make use of it I noticed it isn't there for me.
```

simimi@ubuntubook:/var$ ls
backups  cache  crash  games  lib  local  lock  log  mail  opt  run  spool  tmp

```

Can I just add a www dir and it will have the same effect as normal? (I assume there is a reason it is called the root directory for Web documents... must have some special Web document holding power or some such right?)

Thanks again all!:popcorn:

EDIT: Also do I need to add cgi-bin to /usr/lib/cgi-bin... or does it exist somewhere else as a default?

---

### Post by taurus on 2007-11-10
Have you installed apache2, yet?  When you do, it will create /var/www for you.  Otherwise, create it by hand with

```
sudo mkdir /var/www
ls -la /var
```

---

### Post by Simimi on 2007-11-10
Ahh, thanks so much, but when I installed apche2 it did not create it so I made one just so. Thanks again!

---

