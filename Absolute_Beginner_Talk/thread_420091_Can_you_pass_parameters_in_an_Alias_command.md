---
title: "Can you pass parameters in an Alias command?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Loki-uk on 2007-04-23
Hi is it possible to pass parameters in a alias command. For example -

Alias edit=sudo nano %filename

then use suedit filename

Thanks

---

### Post by finer recliner on 2007-04-23
alias just replaces the left hand side of the argument with the right hand side before bash executes it.

therefore you dont need to pass an argument in, because the command nano can still take arguemtns even though its coming from an alias

heres what you want:
```

alias suedit= sudo nano

//now back to prompt
$suedit filename.txt

```

---

### Post by Loki-uk on 2007-04-23
Thanks :)

---

