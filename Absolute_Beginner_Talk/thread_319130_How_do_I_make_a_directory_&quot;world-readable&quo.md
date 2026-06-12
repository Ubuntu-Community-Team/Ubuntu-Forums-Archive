---
title: "How do I make a directory &quot;world-readable&quot;"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lodbergs on 2006-12-15
Hi

I've got a directory - public_html - that I need to make "world-readable", how do I do that in a terminal?

Hope someone can help.

/Lodberg

---

### Post by ddtrust on 2006-12-15
> **lodbergs said:**
> Hi

I've got a directory - public_html - that I need to make "world-readable", how do I do that in a terminal?

Hope someone can help.

/Lodberg

```

chmod 755 -R public_html/

``` 

gives everybody the rights to read and execute..

---

### Post by lodbergs on 2006-12-15
thank you so much ddtrust. Saved my morning ;)

Have a nice day

---

### Post by ddtrust on 2006-12-15
> **lodbergs said:**
> thank you so much ddtrust. Saved my morning ;)

Have a nice day

I'm glad I could help. :)

---

