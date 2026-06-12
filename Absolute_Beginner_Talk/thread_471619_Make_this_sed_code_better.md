---
title: "Make this sed code better"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by oldcpu on 2007-06-12
```
sed 's/[a-z][a-z][a-z][a-z][a-z][a-z][a-z][a-z][a-z][a-z]/??????????/'
```
As you can see, the code is quite ugly with 10 "[a-z]".  What is a more better way to put it?

Also, what is the variable for any character?  [a-zA-Z0-9] only covers the alphanumerics, there are many other characters that are not affected by it such as !@#$%, etc.

---

### Post by reclusivemonkey on 2007-06-12
What are you trying to accomplish?

---

### Post by Skrynesaver on 2007-06-12
```

sed 's/[a-z]{10}/??????????/'

```
'.' matches any character
'?' matches zero or one instance of any character
and '*' matches zero or many instances of any charcter

However tr is more suitable for what you seem to be doing

---

### Post by oldcpu on 2007-06-12
> What are you trying to accomplish?
An elegant code.

```
echo "abcdefghijklmnopqrstuvwxyz" | sed 's/[a-z][a-z][a-z][a-z][a-z][a-z][a-z][a-z][a-z][a-z]/0123456789/'
```

Anyone know how I can simplify all the [a-z]'s?

EDIT: Thanks, Skrynesaver!

---

