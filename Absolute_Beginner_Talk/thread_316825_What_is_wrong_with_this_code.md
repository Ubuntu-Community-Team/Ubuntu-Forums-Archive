---
title: "What is wrong with this code?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2006-12-11
What is wrong with this code?

```
if [ -f *foo* ]; then rm -f *foo*; fi
```

What the code is suppose to do is if there is a *foo* file, then remove it without interaction.  If there is  not, then nothing happens, not even an error return.

---

### Post by sybaritefury on 2006-12-11
What if you tried something a little more like:

for i in `ls *foo*`
do rm -f $i
done

This will traverse every single file named *foo* and delete it when it finds it.  I'm not sure whether the file test operators can handle wildcards...?

---

### Post by newbie22 on 2006-12-11
That works, but with the hassle of a error return if no such file exists.  Is there a way I can do it without an error return if no such file exists?

---

### Post by weresheep on 2006-12-11
You could try something like this...

```

find . -type f -name *foo* | while read FILE ; do
  echo "$FILE"
  #rm -f "$FILE"
done


```

WARNING- find will search the current directory (the . in the above command) and ALL subdirectories. Make sure this is what you want before running with the rm -f uncommented.

If 'find' does not find any matches there are no errors as the while loop exits straigt away.

-weresheep

---

