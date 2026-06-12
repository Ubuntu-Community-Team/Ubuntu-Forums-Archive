---
title: "Fill in the bash code"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-01-19
```
cat file | grep 'foo$'
x=y

```

What I am trying to do is cat something that matches to "foo".  Then have "foo" be "y".  So I can use $x.  Would someone please fill in the missing code?

---

### Post by kabus on 2006-01-19
```
x=`grep 'foo' file`
```

"grep 'foo' file" is equivalent to your first line and the result would get assigned to $x.
Not sure I understood what you want to do, though.

---

