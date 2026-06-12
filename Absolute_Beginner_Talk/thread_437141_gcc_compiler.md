---
title: "gcc compiler"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by programmer in linux on 2007-05-08
hello all,

> gcc -c hash.c 
hash.c:1:19: error: stdio.h: No such file or directory
hash.c:2:18: error: time.h: No such file or directory
hash.c:6:21: error: pstdint.h: No such file or directory


how to get this files so i can run my c file  ..?

---

### Post by kosmic on 2007-05-08
"sudo apt-get install binutils" 

:)

or fire up synaptic and install GCC :)

---

### Post by LaRoza on 2007-05-08
Did you install every thing? 

```

sudo apt-get install build-essential

```

---

### Post by programmer in linux on 2007-05-08
thx LaRosa

---

### Post by lostvicking on 2007-05-12
Thanks a lot to LaRoza. Had exactly the same problem, installed GCC through Synaptic but seemed to be missing the stdio.h and stdlib.h among others. This solved it.
Thanks again.

---

