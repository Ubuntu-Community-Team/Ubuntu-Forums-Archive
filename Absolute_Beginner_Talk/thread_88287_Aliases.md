---
title: "Aliases"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by ArthurHeng on 2005-11-09
Just wondering, about those aliases such as "alias rm='rm -i'", "alias cp='cp -i'", "alias mv='mv -i'", when I put them in my .bashrc file, they doesnt seem to work. So where's the correct script file to store these aliases?

---

### Post by 23meg on 2005-11-09
.bash_profile

---

### Post by ArthurHeng on 2005-11-09
Btw, anything I should do after adding the aliases in .bash_profile? Coz it doesnt work for me.

---

### Post by 23meg on 2005-11-09
You may have to logout and login again.

---

### Post by Joe_lurker on 2005-11-09
When you open a terminal the .bashrc is read.  If you make changes in the terminal you can 'source ~/.bashrc'.  This will reload the .bashrc file.

-Joe

---

### Post by 23meg on 2005-11-10
Or rather, "source ~/.bash_profile".

---

### Post by mechanic on 2005-11-10
[QUOTE=23meg]Or rather, "source ~/.bash_profile".[/QUOTE]
Normally aliases are in .bashrc. I have no problem with them there. Is there not an alias set up for color support to ls in the intall setup by default?

m.

---

### Post by Sutekh on 2005-11-10
I put my aliases in their own script ".bash_aliases" and then in ".bashrc" uncommented the lines which execute the .bash_aliases file... they were something like this 

```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

---

