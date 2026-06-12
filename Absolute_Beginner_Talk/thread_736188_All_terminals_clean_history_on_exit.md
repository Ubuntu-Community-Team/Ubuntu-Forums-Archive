---
title: "All terminals clean history on exit"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-03-26
Hi

I'm have Xubuntu, why system cleans history every time I close terminal.
What can I do to stop cleaning.
I press the up key, but can't see previous entris.
I googled, found nothing appropriate.

---

### Post by nitro_n2o on 2008-03-26
here is something on the top of my head (but i'm not sure if it works) 

if you are using bash add this somewhere on you .bashrc file 

```
function _exit()
{
    cat /dev/null > /home/<user_name>/.bash_history
}
trap _exit EXIT
```

it might work

---

### Post by (((X))) on 2008-03-27
It didn't help.

---

