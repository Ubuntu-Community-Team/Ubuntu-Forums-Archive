---
title: "Just wondering how to change the shape of  prompt"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-16
Hi all , 
I'm just wonderning who can i change the prompt of the terminal ?? 
(i.e the current **xxxx@yyyy~:**  change it to **[xxxx@yyyyy~:]**


Cheers,
   Mba7eth

---

### Post by zerhacke on 2007-01-16
Edit your .bash_profile file in /home/yourusername to look like the following:

```
# set prompt: ``username@hostname:/directory $ ''
PS1="[\u@\h:\w] " 
case `id -u` in
      0) PS1="${PS1}# ";;
      *) PS1="${PS1}$ ";;
esac
```

---

### Post by Mba7eth on 2007-01-16
cooool thanx dude 


Cheers, 
     Mba7eth

---

