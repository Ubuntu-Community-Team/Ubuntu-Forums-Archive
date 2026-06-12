---
title: "Licq"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Fleshy on 2007-03-19
help me please!
I have  quite strange trouble with LICQ installation. I've downloaded DEB-package of     LICQ but when I'm trying to install it, I receive message that licq-plugin dependence is not satisfiable. Then I install licq-plugin-qt but it requires LICQ as dependence!!! what i have to do? i dont know...

---

### Post by AtrejuT on 2007-03-19
you could try to force it I guess>
```

dpkg -i --force packagename.deb

```
I think is the syntax, but I'm not at home and not on Ubuntu right now...

---

### Post by Fleshy on 2007-03-19
Thanks! It's working!

---

