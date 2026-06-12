---
title: "&quot;make&quot; command isn't recognized"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by drorl on 2006-09-15
hi
i have some c files and a make file in one dirctory.
when typing make or any kind of make XXX it says the command isn't recognized. (i have just installed ubunto).
any ideas?
thrnk 
dror

---

### Post by jmwhokie on 2006-09-15
sure...do a sudo apt-get install make


(or do it from the Applications->Add/remove advanced tab under the Dev section.

---

### Post by ronmarley1 on 2006-09-15
Additionally/instead of..., I'd recommend ```
sudo apt-get install build-essential
```

---

### Post by Najand on 2006-09-15
I agree with ronmarley1, becuase build-essential contains packages (including  make) needed  for building applications and is essential when compiling packages.

---

