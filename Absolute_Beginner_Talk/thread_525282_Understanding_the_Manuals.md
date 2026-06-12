---
title: "Understanding the Manuals"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by will71110 on 2007-08-14
Hi.  I was wondering how do you read what the manuals tell you in the terminal(or the help)?  Example would be:

route [ v]  [-A family] add [-net] target [netmask Nm] and so on

Basically where do you put user (like IPs in the example above) info and what is required stuff?    Basically there are:

Condition in **bold**
Condition with a -
Condition with [] around

But I get confused when trying to read them.  Anyone know how I can better read these?

---

### Post by heimo on 2007-08-14
```
man man
```

>        bold text          type exactly as shown.
       italic text        replace with appropriate argument.
       [-abc]             any or all arguments within [ ] are optional.
       -a|-b              options delimited by | cannot be used together.
       argument ...       argument is repeatable.
       [expression] ...   entire expression within [ ] is repeatable.


---

### Post by will71110 on 2007-08-14
wow I would have never thought of man the man.  LOL...Thanks. :)

---

