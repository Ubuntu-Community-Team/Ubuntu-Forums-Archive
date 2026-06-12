---
title: "Problem with Lincity-NG"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by esocyn on 2007-03-07
Hey;

I recently installed Lincity-NG from the Snyaptic Package Manager. Well, when I go to start it from the games menu, nothing comes up. Likewise, when I try to start it after creating a launcher, nothing comes up either. I check the program manager and it doesn't say anything about Lincity running after I tried opening it.

Is there any other way I should try or is it hopeless?

---

### Post by kariopto on 2007-03-07
What does it say when you try to run it from the terminal?

---

### Post by esocyn on 2007-03-07
"Unexpected exception: Failed creating configuration directory '/home/eric/.lincity': Permission denied"

---

### Post by schwascore on 2007-03-07
A quick-and-dirty way of fixing this might be:
```
cd ~
mkdir .lincity
chmod 777 .lincity

```

That creates the directory and gives universal read-write-execute privilege to all users / programs.  Not the ideal solution, but a quick one.

---

