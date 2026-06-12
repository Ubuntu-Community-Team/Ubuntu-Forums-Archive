---
title: "Which Package?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Axme on 2007-04-05
When running ./autogen.sh I get the message

No package 'gtk+-2.0' found

In ubuntu I can not find gtk+-2.0 or its like in the repositories. Which package do I need to downlaod please?

---

### Post by moore.bryan on 2007-04-05
[I]try
```
sudo aptitude install --with-recommends libgtk2.0-0
```
[/I]

---

### Post by Axme on 2007-04-06
Thanks, that worked!!!

---

### Post by moore.bryan on 2007-04-06
*no problem...*

---

