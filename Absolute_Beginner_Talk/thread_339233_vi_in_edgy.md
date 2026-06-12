---
title: "vi in edgy"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by jtibau on 2007-01-15
I've noticed vi works differently in edgy than in dapper. This confuses and bothers me a little.
Does it have to do with using dash instead of bash?

---

### Post by taurus on 2007-01-15
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by mvaniersel on 2007-01-15
I've noticed the same, I get all kinds of extra characters while editing. Shouldn't this be considered a bug? Why should you need to install vim-full to get a workable vi?

---

### Post by trash on 2007-01-15
vim-full wants to install another 39.8mb, seems excessive to get vi working

---

### Post by neilp85 on 2007-01-15
This is because both vim and vi are installed on Edgy. It used to be that vi and vim commands invoked the same editor. This is no longer the case.

---

