---
title: "Compiz"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-06-27
Okay, I have dapper 6.06. I downloaded and instaleld compiz with the shell. 
I used sudo apt-get install compiz. And it says that it downloaded and installed.
But i cant find the app anywhere on my computer. Is it that it doesn't work on dapper?
I also rebooted and all.

please help.

---

### Post by Steve B on 2007-06-27
have you tried ```
$ compiz
```
in the terminal?

---

### Post by phizikal on 2007-06-27
yes i have.

```

root@admin:/home/admin# compiz.real: No composite extension

```

---

### Post by phizikal on 2007-06-27
*cough* excuse me... =/

---

### Post by aeiah on 2007-06-27
well it seems you're missing the composite extention :p

what graphics card have you got? are you using compiz with XGL or AIGLX? have you installed and verified that you are using the opengl capable video drivers?

---

### Post by aeiah on 2007-06-27
oh, and have you tried launching compiz from your user account and not root?

---

