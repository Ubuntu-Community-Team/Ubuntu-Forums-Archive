---
title: "ls question"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-01-03
If I "ls" in a directory that has a lot of files, it would only show the bottom results.  Whatever top results is truncated and cannot be seen because it does not fit in the console.

Is there a way I can get "ls" to print part of it, and requires me to hit Enter to show the next set of result?

---

### Post by 23meg on 2007-01-03
```
ls | less
```

---

### Post by Bachstelze on 2007-01-03
```
 ls | less -
```

will let you browse the ls results in less, as with any other text. Browse with the up/down arrows and Q to return to the prompt.

---

### Post by MkfIbK7a on 2007-01-03
well actually 
go to a terminal 
the "edit" menu "profiles" chose one and press "edit"
click the "scrolling" tab change number of lines in scroll back
(see screen shot)

---

