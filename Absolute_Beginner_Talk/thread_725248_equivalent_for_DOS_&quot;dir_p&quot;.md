---
title: "equivalent for DOS &quot;dir /p&quot;?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by flowevd on 2008-03-15
my terminal output is out of control.
is there a 'see more on keystroke' feature like in DOS?

thanks for your help.

---

### Post by bollix47 on 2008-03-15
```
ls -l | more
```

You can pipe most commands thru more to get a page at a time.

---

### Post by luisromangz on 2008-03-15
Use the more command:

ls -l | more

---

### Post by disturbedite on 2008-03-15
i've often wondered this myself.
i just checked ls's man page but did not see anything like it.

---

### Post by flowevd on 2008-03-15
thanks!

---

### Post by louieb on 2008-03-15
:popcorn:And because its Linux you can use more or less.
```
 ls -l | less
```less lets you scroll up and down 
and when done press q to quite

---

### Post by drubin on 2008-03-15
> Re: equivalent for DOS "dir /p"?
And because its Linux you can use more or less.
Code:

 ls -l | less

less lets you scroll up and down
and when done press q to quite

Less is deff the way to go. going backwards. easier to use.

---

