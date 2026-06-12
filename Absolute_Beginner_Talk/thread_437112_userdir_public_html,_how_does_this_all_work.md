---
title: "userdir public_html, how does this all work?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by sgg on 2007-05-08
Hello,

I'm trying to host a website and I need to learn how to host
from a user's home folder.

I need a tutorial that will walk me through using
userdir.


Thanks

---

### Post by jfinkels on 2007-05-08
> **sgg said:**
> Hello,

I'm trying to host a website and I need to learn how to host
from a user's home folder.

I need a tutorial that will walk me through using
userdir.


Thanks

Once you have apache installed, just put a folder in your home folder called "public_html", put some files in there and you will be able to see them from "http://yourdomain/~username" where "yourdomain" is your domain name (or IP address...127.0.0.1 will work if you are working from the computer on which apache is installed) and "username" is the name of the user (same as the name of the home folder).

---

