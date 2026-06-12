---
title: "Software Listing Command"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by markbusu on 2008-02-26
What is the command needed to check if a particular package is installed in command prompt?

Such as check as G++ is installed?

Thanks!

---

### Post by markbusu on 2008-02-26
Grrr... Meant Terminal Sorry :)

---

### Post by shad0w_walker on 2008-02-26
As with almost everything there are a few ways to do it. I prefer using the aptitude method:

```
aptitude show <package-name>
```

That will show the package details, third line shows the package state. If you just want the state and nothing else you can use

```
aptitude show <package-name> | grep "State:"
```

---

### Post by markbusu on 2008-02-26
Cheerz m8!

---

### Post by 289Shelby on 2008-02-26
There are probably a few ways of doing this but the two I use are:

which g++

which on my system returns /usr/bin/g++

or for more infomation about the package and whether or not it's installed try:

aptitude show g++ (or whatever package you're interested in)

Hope this helps.

---

