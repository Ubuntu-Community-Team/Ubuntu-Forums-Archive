---
title: "2&gt;/dev/null to suppress error msg not working"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Kent84 on 2008-03-05
```
/> find / -name "*mathematica*" 2 > /dev/null
find: paths must precede expression
Usage: find [path...] [expression]
```

Is there something I am missing??? I hate the find command! :(

---

### Post by Dr Small on 2008-03-05
It's this, isn't in?
```
 2&>1 > /dev/null 
```

---

### Post by unutbu on 2008-03-05
```

find / -name "*mathematica*" 2&>1 > /dev/null

```

dumps the error messages into a file called '1'.

```

find / -name "*mathematica*" 2>/dev/null

```

works

```

find / -name "*mathematica*" 2&>/dev/null

```

also works. If someone could tell me what the '&' is supposed to mean, I'd be much obliged.

---

### Post by unutbu on 2008-03-05
By the way, Kent84,
try

```

locate mathematica

```

It is much much faster than find.

---

### Post by glennric on 2008-03-05
Refer to the following link for more information on using stdin, stderr, and stdout.
[http://www.linuxdevcenter.com/pub/a/linux/lpt/13_01.html]("http://www.linuxdevcenter.com/pub/a/linux/lpt/13_01.html")

---

### Post by Kent84 on 2008-03-05
Problem solved. The machine I was ssh'ing into was running the tcsh shell and not the bash shell.

---

### Post by bhold on 2008-03-05
> **unutbu said:**
> ```

find / -name "*mathematica*" 2&>1 > /dev/null

```

dumps the error messages into a file called '1'.

```

find / -name "*mathematica*" 2>/dev/null

```

works

```

find / -name "*mathematica*" 2&>/dev/null

```

also works. If someone could tell me what the '&' is supposed to mean, I'd be much obliged.


Try man 1 sh and man 1 bash and look at the sections that describe redirection. Personally, I found it clear as mud but I think that is where you would look for a rigorous description of how this should work. With a lot of this shell syntax, best to find something that works for you, test it,  and move on - - very easy to dive down into the rabbit hole on some of this stuff.

---

