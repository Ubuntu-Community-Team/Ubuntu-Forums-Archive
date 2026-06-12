---
title: "How would I change to a different shell?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-24
Hi, I installed a few different shells but I can't figure out how to use them....I tried making a new terminal profile but no luck.


Thanks

---

### Post by jordilin on 2006-07-24
If you are talking about changing bash to korn shell or tcshell, then try 
```
chsh username shell_path_name 
```

---

### Post by jordilin on 2006-07-24
to know in what type of shell are you, then type
```
echo $SHELL
```

---

