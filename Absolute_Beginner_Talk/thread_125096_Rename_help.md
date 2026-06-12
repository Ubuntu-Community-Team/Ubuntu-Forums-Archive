---
title: "Rename help"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-02-03
Examples:

012do.foo
123re.foo
234mi.foo
345fa.foo
456so.foo

What I am trying to do is rid the numbers and just keep the alphabet.  So it would look like this afterwards:

do.foo
re.foo
mi.foo
fa.foo
so.foo

I tried this:
```

rename [0-9] "" *.foo

```

But it didn't work.  How do I tell rename to remove all numbers in a file name?

---

### Post by mvaniersel on 2006-02-03
How about:

```

rename 's/[0-9]+//' *.foo

```

---

