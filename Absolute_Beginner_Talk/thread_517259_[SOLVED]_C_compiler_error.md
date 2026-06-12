---
title: "[SOLVED] C compiler error"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by kinngg on 2007-08-04
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

i dn get this.. wats da problem?

---

### Post by Brunellus on 2007-08-04
what were you trying to do in the first place?

---

### Post by kinngg on 2007-08-04
buildin amule

---

### Post by jw5801 on 2007-08-04
Post everything that you did, ie. copy and paste the terminal commands you used and their output. Then we'll see what we can do to help.

---

### Post by Majorix on 2007-08-04
Why build when you can download from the repos...

Make sure you have universe and multiverse repos enabled and then type this in a terminal:

```
sudo apt-get install amule
```

If you are not satisfied, post the log that the comp speaks of.

---

### Post by lambros on 2007-08-04
I think this happens when you have the C compiler installed, but not the development headers and libs.  Try this command:
```
sudo aptitude install build-essential

```
Lambros

---

### Post by kinngg on 2007-08-04
the build-essentials worked thx.. :)

---

