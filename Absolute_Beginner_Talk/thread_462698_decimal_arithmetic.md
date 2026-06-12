---
title: "decimal arithmetic"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2007-06-03
im trying to write a script in which a decimal, stored in a variable, is multiplied by 100 and set as another variable. from my online research, bash treats decimals as strings, so bash arithmetic wont work. ive tried bc
but anything of the form

var=$((echo $othervar*100 | bc -l ))

causes syntax errors.

how might i do this?

thanks!

---

### Post by yabbadabbadont on 2007-06-03
The 'eval' bash built-in can be used for this.  Read the "ARITHMETIC EVALUATION" section of the bash manpage for details.

EDIT: 'eval' is not the correct function, use 'expr' instead.  Sorry.

---

### Post by yabbadabbadont on 2007-06-03
Here is an example:

```
wallpapernumber=`expr $randomnumber % $number_of_wallpapers + 1`
```

---

### Post by xolot1 on 2007-06-03
thank you very much, thats perfect!
::)

---

