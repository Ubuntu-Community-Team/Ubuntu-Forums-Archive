---
title: "C shell question on strings"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2006-10-14
Bear with me here:

Let's say I have a script that takes an input from the user where they are prompted for multiple inputs on the same line:
```
echo -n "Please enter first and last name:"
set fullname = $<
```
 Is it possible to then parse the *fullname* string and seperate the two in the C shell?

------------------------------------------
Managed to figure this one out after a bit:
```
echo -n "Please enter first and last name:"
set fullname = $<
set firstandlast = ($fullname)
echo -n "First name is" $firstandlast[1]
echo -n "Last name is" $firstandlast[2]
```

Thank you to those who took a look at the problem anyways.:mrgreen:

---

