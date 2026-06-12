---
title: "How do I eliminate blank lines after 'cat'?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-06-27
When 'cat' is used, what is needed to be piped to eliminate blank lines and lines that begin with "#"?

The best I can do by myself is
```
cat file | sed 's/#\.*//g'
```

I can only solve the eliminating comments part.  It still leaves a blank line.

The pipe does not have to be sed.  It can be anything so long as it gets the same result.

Please help.

---

### Post by wjp.reg on 2007-06-27
This link might help 

[http://www.dsl.org/cookbook/cookbook_17.html]("http://www.dsl.org/cookbook/cookbook_17.html")

---

