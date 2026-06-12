---
title: "setting alias in a script"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by munkar on 2006-12-25
i'm trying to set my aliases at the beginning of my bash session. rather than putting all my aliases in my .bashrc file, i'd prefer to have them all in a script and call that script from .bashrc. but it seems as though the aliases don't stick outside the script. is there any way to fix this? thanks!

---

### Post by m83 on 2006-12-25
You can try putting something like this in your .bashrc file:
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Then put all your alias='' commands in ~/.bash_aliases. This is how I do it and it works without problems.

---

### Post by munkar on 2006-12-26
thanks so much. from looking at your example, i figured out that what i was missing was a period before the line in which i was calling the external script.

what the period does, i have not a clue. ;)

---

### Post by po0f on 2006-12-26
munkar,

Sources the file.  You could also swap out the period with `source` if it makes it more readable for you.

---

