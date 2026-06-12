---
title: "Link"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by hannulan on 2007-07-24
How do I link one directory to another?

I would like to do it in the console.

---

### Post by Mornedhel on 2007-07-24
See the 'link' man page : [http://pwet.fr/man/linux/commandes/link__1](http://pwet.fr/man/linux/commandes/link__1)

---

### Post by Cypher on 2007-07-24
Hmm..I've always used "ln"
```

ln -s <TARGET> <LINK NAME>

```
<TARGET> is the file you want to link to
<LINK NAME> is what you want the link to be..

So if you had a path like "/home/USER/really/long/path/name" and wanted to make a link shorter, you would do
```

ln -s /home/USER/really/long/path/name /home/USER/name

```

---

### Post by Mornedhel on 2007-07-24
> **Cypher said:**
> I've always used "ln"

That's because you got used to two-letter long commands. We youngsters need longer, more explicit names... :P Plus, I think 'link' is distribution-specific.

I agree though, ln is more powerful.

---

### Post by Cypher on 2007-07-24
> **Mornedhel said:**
> That's because you got used to two-letter long commands. We youngsters need longer, more explicit names... :P Plus, I think 'link' is distribution-specific.

I agree though, ln is more powerful.
LOL. I didn't even know the existence of 'link' until you mentioned it. It is available on Fedora (I checked :) )..but it does provide a quick way of doing what LN does.

---

