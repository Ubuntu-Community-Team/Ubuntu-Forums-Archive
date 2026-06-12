---
title: "how to install psi by source"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-07-25
[http://www.google.com/support/talk/bin/answer.py?answer=24074](http://www.google.com/support/talk/bin/answer.py?answer=24074)

i want to install psi to make google talk in gmail.
the problem is....i dont know how to install psi by source.

the url i give is where they do the explaination abt the psi and jabber.

how can i install the psi by using the souce?

the url for the psi...[http://psi-im.org/download](http://psi-im.org/download).

---

### Post by Jagot on 2006-07-25
This is how to install from source:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Are you aware however that psi is available in the ubuntu repositories - universe I think?

---

### Post by taurus on 2006-07-25
I assume you know that you need QT & QCA developer packages (besides "build-essential") before you can build PSI from source!!!  On the other hand, why not grab the Debian unstable package and install it with "dpkg -i"!

---

### Post by penguinKabuki on 2006-07-25
even the file type is bz2?
btw....what is bz2?

---

### Post by taurus on 2006-07-25
Bz2 is just a different type of compression like gzip!!!  Most of the time, you would see either filename.tar.gz or filename.tar.bz2.  So, to uncompress and untar them, you would do

```

tar xvzf filename.tar.gz
tar xvjf filename.tar.bz2

```

---

