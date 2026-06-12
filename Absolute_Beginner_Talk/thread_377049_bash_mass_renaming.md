---
title: "bash: mass renaming"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-03-05
Using just bash, how do I mass rename?

Say the examples are as follows:

linux2610
linux2612
linux2614

After using bash to mass rename, it shoudl look like this:

kernel2610
kernel2612
kernel2614

Again, just using bash.  I am aware that there is a mass renaming tool such as mrename and krename available.  But I would like to see how it is done with just bash.

---

### Post by invalid on 2007-03-05
It would look something like this:```
#!/bin/bash
for fil in `ls linux[0-9]*`
do
  echo $fil
  new=`echo $fil | sed  -e 's/linux/kernel/g'`
  mv $fil $new
done
```

Please note I have not personally tested this, and you should test it before using it on important things :)

---

