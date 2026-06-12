---
title: "When does /tmp get used?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by desklamp on 2007-11-17
Under what conditions will the /tmp folder get used?  Best if accompanied with examples.

Note that I am looking for technical answers than "It is used when temporary files need to be temporary stored somewhere."

---

### Post by Brautigam on 2007-11-17
[http://www.redhat.com/archives/fedora-list/2004-February/msg05382.html](http://www.redhat.com/archives/fedora-list/2004-February/msg05382.html)
this should help you :guitar:

---

### Post by desklamp on 2007-11-17
How does that help me?

I asked when the /tmp folder is used.  You gave me a link to a init script to clear it automatically.

---

### Post by shad0w_walker on 2007-11-17
Though I didn't post it, I apologise for that response, he has been making less than help responses around the forums today.

Anyway, the tmp folder is used when a program is storing files that are 'unimportant' mostly temporary files such as lock files and other files which are created but not ment to be kept for anything more than the current session. It is also a useful place to store files whilst they are being worked on as all users can access the tmp folder. 

I use it quite a bit in various bash scripts to store a file whilst it is being worked on and then write the output to its final destination, helps me keep target folders clear of junk and makes cleaning up after a process easier.

---

