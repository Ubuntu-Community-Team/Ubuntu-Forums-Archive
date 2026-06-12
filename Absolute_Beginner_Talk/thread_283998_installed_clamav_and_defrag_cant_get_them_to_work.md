---
title: "installed clamav and defrag cant get them to work"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by bigdavesr on 2006-10-25
:mad: Does anyone know how to execute these programs. I have tried every thing I KNOW TO DO  . tHEY ARE INSTALLED BUT CANT RUN THEM

---

### Post by tubasoldier on 2006-10-25
> **bigdavesr said:**
> :mad: Does anyone know how to execute these programs. I have tried every thing I KNOW TO DO  . tHEY ARE INSTALLED BUT CANT RUN THEM

clamav runs as a daemon in the background. It is not a program that acutally needs to be "run". Matter of fact there is only like 20 known viruses for linux and they are quite difficult to get. The only reason to run clamav is to help stop viruses for people who run windows and who happen to be on your network. 

defrag? where did you get that? search the forums for information about defragging linux file systems. there is a lot of information about why we dont need to.

---

### Post by CupofDice on 2006-10-25
```
man clamscan (for info)
```

Lets say you want to scan home. Just type-
```

clamscan -r /home/user/ [COLOR="Red"](r for recursive)[/COLOR]
clamscan -r --quiet /home/user [COLOR="Red"](so it tells you only if you have viruses or errors)[/COLOR]

```

---

