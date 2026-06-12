---
title: "Making Aliases"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-22
What character(s) can I use in an alias command to stand for the argument in the aliased command?  I am trying to make an alias undelete command like this:
```
alias und=mv ~/.Trash/xxx $dir
```
Then on the command line I would type
```
und xxx
```
and restore the file from Trash to the current directory.  Unfortunately I don't know how to do it and haven't been able to find out.

Thanks,
Buck

---

### Post by raul_ on 2006-12-22
Files deleted from the terminal don't go to the trash i think..just so you know :)

---

### Post by Buck2348 on 2006-12-22
> **raul_ said:**
> Files deleted from the terminal don't go to the trash i think..just so you know :)
I am already using an alias for rm that moves the file into .Trash.

Where could I find information like this?--I'd like to see a listing of the shell's environmental variables, if that's the right term.

Thanks,
Buck

---

### Post by raul_ on 2006-12-22
```

env

```

Is that what you're looking for?

---

### Post by Buck2348 on 2006-12-23
> **raul_ said:**
> 
Is that what you're looking for?
Interesting, but now I think what I'm looking for is called a "local variable," the argument entered along with a command.

Thanks for your reply.

Buck

---

