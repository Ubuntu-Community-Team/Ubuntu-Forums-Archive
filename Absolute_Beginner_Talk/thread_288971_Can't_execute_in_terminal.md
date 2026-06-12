---
title: "Can't execute in terminal"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by ortcutt on 2006-10-30
If have a program, chmod u+x it, and type ./foo , bash tells me  

bash: ./foo: No such file or directory

even though foo is very much in the working directory.  I also own the directory and have full user privileges for it.  Any ideas what's going on here?

---

### Post by steve.horsley on 2006-10-30
Try **ls ./foo** just to prove the point that it's there.

I have occasionally seen this with scripts that are trying to open other files. So it could be thta your program is trying to open a non-existent file.

---

### Post by tatimmer on 2006-10-30
foo may be in the directory, but is it in the current working directory (pwd) ?

---

### Post by ortcutt on 2006-10-30
Yes.  foo is in the pwd.

---

### Post by taurus on 2006-10-30
> **ortcutt said:**
> Yes.  foo is in the pwd.
Then, what is the output of 

```
ls -la
```

---

### Post by ortcutt on 2006-10-30
> **taurus said:**
> Then, what is the output of 

```
ls -la
```

...
-rwxr-xr-x  1 baz baz 4015796 2005-08-09 11:01 foo
...

---

