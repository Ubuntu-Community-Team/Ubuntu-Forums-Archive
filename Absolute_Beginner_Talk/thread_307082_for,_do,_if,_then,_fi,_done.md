---
title: "for, do, if, then, fi, done"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2006-11-26
Would someone please write a short code or command line that involves "for, do, if, then, fi, done" that will run in the console and does not have to be in a script?

I want to see how it is done without breaking the lines.

---

### Post by wastrel on 2006-11-26
for i in $(ls); do echo $i ; done

---

### Post by Razor81 on 2006-11-26
The basic thing is to put a ; anywhere there would be a line break in the script.  You can also optionally use \<enter> to break the command onto multiple lines from a command prompt.

ie:

pseudo-script:
```

if [something]; then
    dosomething
    dosomethingelse
fi

```

can be written on the command line as:
```

if [something]; then; dosomething; dosomethingelse; fi

```
or as:
```

if [something]; then; \
    dosomething; \ 
    dosomethingelse; \
fi

```

for-do-done works the same way on the command line, by replacing line breaks with ; and optionally with \<enter> to split it onto multiple lines.

---

