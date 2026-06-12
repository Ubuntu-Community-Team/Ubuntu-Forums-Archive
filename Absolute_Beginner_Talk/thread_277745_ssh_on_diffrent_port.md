---
title: "ssh on diffrent port"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-10-15
hi,

how do i tell ssh that i want to connect to a diffrent port?
i have forwared a port on my gateway like this : 9999 to 22 on my machine.
what is the syntax for ssh to make it connect on port 9999?

---

### Post by nyinge on 2006-10-15
```

ssh username@host -p port_number

```

Is it what you want?

---

### Post by zekopeko on 2006-10-15
Thnx!

That was exactly what i need

---

