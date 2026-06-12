---
title: "Conky date"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-03-23
Does anyone know how to add the date to conky? I have the time up already but what about the date?

---

### Post by RealPSL on 2008-03-23
Your best bet there is to use the exec/execi option eg.

{exec date}

You can format the date to your preference using standard options.

---

### Post by herbster on 2008-03-23
```
${time %r}
```

---

